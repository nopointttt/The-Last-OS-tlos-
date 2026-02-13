# Procedural Memory: Developer Guide

## 1. Запуск проекта
Проект состоит из Ядра (Kernel) и Оболочки (Shell), работающих в суверенном тулчейне.

### Сборка Frontend (Shell UI)
```powershell
cd shell/frontend
npm install
npm run build
```

### Сборка и Запуск Ядра (через Zig)
Мы используем Zig для кросс-компиляции C-зависимостей (`libcrux`, `rquickjs`).
```powershell
# Сборка
cargo zigbuild -p desk-shell

# Запуск сервера
.\target\debug\desk-shell.exe
```
*Port: 3000 (HTTP для статики + WebSocket для моста)*

### Работа с Латицей (NATS)
Shell требует запущенный NATS-сервер для полной функциональности.
- **Default**: `nats://localhost:4222`.
- **Failure**: Если NATS не найден, Shell выведет `WARN` и продолжит работу в локальном режиме.
- **Start**: `wash dev` или `nats-server`.

## 2. Работа с состоянием (SolidJS)
Мы используем `solid-js/store`.
- **Чтение**: Обращайтесь к свойствам напрямую (через прокси): `components[0].x`.
- **Запись**: Используйте `produce` для мутаций.

## 5. Lessons Learned (Complexity & Bugs)
### 1. Reactivity Trap (`createSignal` vs `createStore`)
- Переход на `createStore` + `produce` для сохранения ссылочной целостности объектов.

### 4. Lattice wRPC API (Critical)
- **Dependency Isolation**: При использовании `wrpc-transport-nats` необходимо отключать дефолтные фичи (`default-features = false`), чтобы избежать конфликтов версий NATS.
- **API v0.28.4 Signature**: Метод `invoke_values` требует 5 аргументов. Параметр `paths` должен иметь тип `&[&[Option<usize>]]`.
- **Result Handling**: Возвращаемое значение — кортеж из 2 элементов: `((Results,), Option<Future>)`. Игнорирование второго фьючера (`_fut`) обязательно.

### 6. Windows Networking (10061 Error)
- При использовании `wash dev` на Windows часто возникает конфликт IPv6/IPv4. Всегда принудительно используйте `127.0.0.1` вместо `localhost`.
- Если NATS не отвечает на 4222, проверьте процессы через `Get-Process nats-server`.

## 13. Spatial Index (Quadtree)
Spatial Actor хранит данные в Quadtree. Поиск объектов по координатам — O(log N).

## 14. Logging & Debugging
- **Console**: Трейсинг в Shell настроен на "pretty" вывод (только важная инфо).
- **Files**: Полный стек логов пишется в `.temp/shell.log`. Это первый файл для проверки при ошибках в wRPC/NATS.

## 15. Universal UI Protocol (UUP)
- Все интерактивные элементы должны использовать `Intent` для возврата управления в Lattice. Shell — чистый рендерер.

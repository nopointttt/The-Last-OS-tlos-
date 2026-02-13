# Actor Interface: The WIT Contract System

Этот документ описывает стандарт интерфейсов акторов (Actor Interface) в **The Last OS (tLOS)**. Мы используем **WebAssembly Interface Types (WIT)** как основной язык определения контрактов (IDL).

---

## 1. Архитектура документации: C4 + IDD

Для описания интерфейсов мы используем гибридную модель:

-   **C4 Model (Level 3 - Component)**: Визуализирует границы актора (Container) и его внутренние компоненты, взаимодействующие через WIT.
-   **Interface-Driven Development (IDD)**: WIT-файлы являются "единственным источником истины" (Single Source of Truth). Документация встроена прямо в код интерфейса через `///`.
-   **Mermaid Sequence Diagrams**: Используются для описания сложных протоколов обмена сообщениями через **wRPC**.

---

## 2. Структура WIT-пакета tLOS

Мы придерживаемся стандарта **WASI Preview 3** и организации пакетов Bytecode Alliance.

### 2.1. Организация файлов
```text
wit/
├── deps/          # Внешние зависимости (wasi, wasmcloud)
├── types.wit      # Общие типы данных и перечисления
├── interfaces.wit # Определение функциональных интерфейсов
└── world.wit      # Финальная сборка мира актора
```

### 2.2. Стандарты именования
-   Идентификаторы: `kebab-case` (ASCII).
-   Пакеты: `namespace:package-name@version`. Пример: `tlos:spatial-engine@0.1.0`.
-   Версионирование: Строгое соблюдение **SemVer**.

---

## 3. Ключевые паттерны проектирования

### 3.1. Async-First (WASI Preview 3)
Для tLOS критически важна неблокирующая работа. Мы используем нативные типы `stream` и `future`:
```wit
interface spatial-query {
    record point { x: f64, y: f64 }
    query-radius: func(center: point, radius: f64) -> stream<point>;
}
```

### 3.2. Marshalling & Polyglot
WIT автоматически обрабатывает маршалинг данных между языками (Rust, Go, JS).
-   **Strings & Lists**: Передаются через Canonical ABI (копирование).
-   **Resources**: Используются для объектов, передаваемых по ссылке (`handle`), что предотвращает лишнее копирование тяжелых структур (например, Quadtree Nodes).

### 3.3. Рекурсивные типы
Для древовидных структур (Spatial Quadtree) используем рекурсивные определения:
```wit
type node = variant {
    leaf(record-data),
    branch(list<node>) // Рекурсия
}
```

---

## 3.4. Примеры живых интерфейсов (Legacy Examples)
Для понимания механики взаимодействия за пределами Quadtree:

### `tlos:identity/manager`
```wit
interface manager {
    /// Получить публичный ключ Суверена
    get-pubkey: func() -> string;
    
    /// Подписать событие/контракт
    sign-event: func(event: string) -> string;
}
```

### `tlos:spatial/canvas` (High-level)
```wit
interface canvas {
    /// Мгновенное обновление координат группы окон
    update-batch-position: func(ids: list<string>, delta_x: f32, delta_y: f32);
    
    /// Создание окна по продуктовой спецификации
    create-window: func(spec: window-spec) -> string;
}
```

---

## 4. Интеграция с Фронтендом (SolidJS)

Для работы из браузера (Shell) мы генерируем TypeScript-биндинги:
1.  **Generation**: `wit-bindgen ts ./wit --out-dir ./src/gen`.
2.  **Usage**: Акторы импортируются как типизированные ES-модули.
3.  **SolidJS Hook Pattern**: 
    ```typescript
    const spatialEngine = await loadWasmActor('spatial_engine.wasm');
    const [data, setData] = createSignal(spatialEngine.queryRadius({x:0, y:0}, 100));
    ```

---

## 5. Транспортный уровень: wRPC

В распределенной среде (The Grid) вызовы WIT-интерфейсов оборачиваются в **wRPC** (WIT-over-RPC).
-   **Прозрачность**: Для кода актора нет разницы, вызван интерфейс локально или через сеть.
-   **Transport Agnostic**: wRPC работает поверх NATS, QUIC или TCP.

---
*Интерфейс — это обещание стабильности в меняющейся среде.*

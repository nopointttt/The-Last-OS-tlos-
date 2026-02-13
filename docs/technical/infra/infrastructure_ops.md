# Infrastructure & Operations: The Grid Deployment Spec

Этот документ описывает принципы развертывания и эксплуатации **The Last OS (tLOS)**. Мы ориентируемся на децентрализованную инфраструктуру, минимизацию DevOps-накладных расходов (Zero-Deployment) и высокую безопасность.

---

## 1. Модель документации: C4 Deployment View

Для визуализации инфраструктуры мы используем **C4 Model (Level 3 - Deployment)**:

-   **Deployment Nodes**: Серверы (Bare Metal), Виртуальные машины, Edge-девайсы, Akash Providers.
-   **Containers**: wasmCloud Host, NATS Server, OCI Registry.
-   **Communication**: Все типы связи помечаются протоколами (NATS, QUIC, wRPC WebSockets).

---

## 1.1. CI/CD Протокол: Security of Origin
Каждый компонент (Актёр или Провайдер) проходит строгий цикл подготовки перед попаданием в Grid:
1.  **Build**: Сборка в `wasm32-wasip2` через `wash build`.
2.  **Sign**: Подпись артефакта системным ключом `wash keys sign`. Только подписанные доверенными ключами Актёры могут получить доступ к ресурсам Lattice.
3.  **Push**: Загрузка в децентрализованный OCI Registry. Обновление в реестре мгновенно делает компонент доступным для всей Латицы через Content-Addressable Storage.

---

## 2. Self-Hosting Guide (Docker/Podman)

Для запуска собственной ноды tLOS на домашнем сервере рекомендуется использовать **Rootless Podman** для максимальной изоляции.

### 2.1. Конфигурация Podman (Rootless)
-   **Runtime**: `crun` с поддержкой WasmEdge или Wasmtime.
-   **Networking**: `pasta` (вместо slirp4netns) для сетевого стека без root-прав.
-   **Wasm-only Nodes (2026)**: В современных кластерах K8s мы используем **SpinKube** и **runwasi**. Это позволяет запускать tLOS компоненты напрямую через `crun` без OCI-надстройки Docker, обеспечивая "холодный старт" < 10мс.
-   **Security**: Использование User Namespaces для маппинга UID/GID.

### 2.2. Запуск через Docker Compose
```yaml
services:
  nats:
    image: nats:2.10
    command: "-js" # Включаем JetStream для персистентности Lattice
  host:
    image: wasmcloud/wasmcloud-host:v2.0.0
    environment:
      WASMCLOUD_LATTICE: tlos-production
      WASMCLOUD_NATS_HOST: nats
```

---

## 3. Cloud Deployment: Akash Network

**The Last OS** деплоится в децентрализованное облако **Akash** через SDL (Stack Definition Language).

### 3.1. SDL (deploy.yaml)
Акаш оперирует Docker-образами, поэтому мы упаковываем tLOS Kernel в легковесный контейнер.
```yaml
services:
  tlos-node:
    image: ghcr.io/the-last-os/kernel:latest
    profiles:
      compute:
        tlos-node:
### 3.2. Akash AI Offloading
Для задач, требующих высокой вычислительной мощности (например, работа с тяжелыми LLM типа MiniMax-M2 или Kimi-K2.5), tLOS использует стратегию **Offloading**:
1.  **Local Sync**: Ядро обнаруживает Akash-ноды через Lattice-интерфейс `system:ai`.
2.  **GPU Direct**: Тяжелые инференс-задачи перенаправляются на ноды с H100/A100 в Akash через wRPC-туннель.
3.  **Encrypted Results**: Результаты возвращаются в Wasm-актор пользователя в зашифрованном виде.
```
### 3.2. Масштабирование в Grid
Благодаря NATS, ноды в Akash автоматически обнаруживают друг друга и формируют единую сетку (Lattice) без настройки VPN или Ingress.

---

## 3.3. Вспомогательная Инфраструктура (Cloudflare)
Хотя tLOS является local-first системой, для глобальной связности используются следующие сервисы:
- **Cloudflare R2**: Хранение зашифрованных бэкапов состояния (Blob Storage).
- **WebTransport / TURN Relay**: Пробитие NAT и обеспечение связи в условиях сложных корпоративных фаерволов.
- **AI Gateway**: Централизованная маршрутизация запросов к LLM (OpenAI/Anthropic) с кэшированием и контролем лимитов.

---

## 4. Zero-Deployment Internals

Магия "запуска кода без сервера" в tLOS основана на четырех китах:

1.  **OCI-Ar (Content Addressable Storage)**: Код хранится как контентно-зависимый артефакт. Хост скачивает его только в момент вызова.
2.  **NATS Control Plane**: Все команды (`wash start actor`) передаются в Lattice как JSON-сообщения по топикам `wasmbus.ctl.v1.*`.
3.  **wadm (Orchestrator)**: Декларативный менеджер, который следит, чтобы текущее состояние Lattice (количество запущенных акторов) совпадало с желаемым.
4.  **No Ingress Architecture**: Благодаря NATS, нодам не нужны открытые входящие порты. Только исходящее соединение с Lattice, что исключает атаку через прямое сканирование портов.

---

## 5. Security: Zero-Trust by Default

-   **Signed Components**: Только подписанные Сувереном компоненты могут быть запущены.
-   **Capability-based**: Актор не может выйти в сеть, если в его JWT явно не указано разрешение `wasi:http`.
-   **Isolation**: Rootless Podman + Wasm Sandbox обеспечивают два уровня защиты от побега из контейнера.

---
*Инфраструктура должна быть невидимой слугой, а не капризным хозяином.*

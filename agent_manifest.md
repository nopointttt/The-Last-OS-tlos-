# Agent Manifest: Sovereign Identity & Capability Spec

Этот документ описывает спецификацию манифеста агента для **The Last OS (tLOS)**. Манифест является "паспортом" и "контрактом" AI-агента, определяющим его права, возможности и место в пространстве.

---

## 1. Модель документации: Hybrid C4 (Agentic)

Для описания спецификации манифеста мы используем гибридный подход:

-   **C4 Model (Level 3 - Component)**: Описывает статическую структуру манифеста (Identity, Capabilities, Policies).
-   **WIT (WebAssembly Interface Types)**: Определяет технический контракт (бинарный интерфейс) агента.
-   **SCXML (State Chart XML)**: Описывает логику состояний агента, заложенную в манифесте для обеспечения детерминизма.

> [!NOTE]
> C4 модель подходит для визуализации архитектуры "Hives" (рои агентов), но для самого манифеста критически важны формальные спецификации и схемы (JSON Schema).

---

## 2. Структура Манифеста (T-OAM Standard)

tLOS использует расширенный стандарт **OAM (Open Application Model)**, адаптированный для децентрализованных систем.

### 2.1. Идентификация (Sovereign Identity)
-   **DID (Decentralized Identifier)**: Уникальный криптографический ID агента (`did:tlos:v1:shaper-actor-0x...`).
-   **Agent Card**: Публичная карточка с метаданными (имя, аватар, описание) для динамического поиска.
-   **Provenance**: Хеш-цепочка, подтверждающая происхождение кода (Signed by Sovereign).

### 2.2. Возможности и Разрешения (Capability Matrix)
В tLOS используется **Capability-based security** вместо классических ACL.
-   **WIT Imports**: Список интерфейсов, к которым агент запрашивает доступ (например, `wasi:http/outgoing-handler`).
-   **Spatial Access**: Координаты или "слои" пространства, в которых агент имеет право действовать (GeoArrow MBRs).
-   **Token Limit**: Жесткие лимиты на использование LLM-токенов и вычислительных циклов Wasm.

### 2.3. Логика и Состояние (AgentML Core)
-   **State Machine Path**: Ссылка на SCXML-файл, определяющий жизненный цикл агента.
-   **MCP Tools**: Описание инструментов, которые агент экспонирует через **Model Context Protocol**.

---

## 3. Пример Манифеста (Agent Manifest JSON)
Пример структуры для "Pomodoro Agent":
```json
{
  "id": "tlos:standard:pomodoro@1.0.0",
  "name": "Pomodoro Agent",
  "permissions": ["spatial:create_widget", "system:notify"],
  "triggers": [
    { "type": "command", "pattern": "pomodoro" },
    { "type": "time", "interval": "25m" }
  ],
  "entry": "wasm/pomodoro.wasm",
  "ui": "widgets/pomodoro.html"
}
```

---

## 3. Пространственная интеграция (Spatial Metadata)

Манифест интегрирует агента в Infinite Canvas через **GeoArrow**:

-   **MBR (Minimum Bounding Rectangle)**: Логическая область "тела" агента в пространстве.
-   **Gaze Focus Traits**: Настройки реакции агента на взгляд Суверена (входящие события Eye-tracking).

---

## 4. Формальная верификация (FormaliSE 2026)

Каждый манифест проходит процедуру **Static Verification** перед развертыванием в Lattice:

1.  **Invariant Analysis**: Проверка декларативных инвариантов (например, "агент не может отправлять PII за пределы Grid").
2.  **Capability Sandboxing**: Автоматическая генерация SFI-границ (Software Fault Isolation) на основе WIT-импортов.
3.  **Conflict Check**: Проверка пересечения MBR с защищенными зонами (Safe Zones).

---
*Манифест — это закон, по которому живет агент в tLOS.*

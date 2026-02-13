# Патч Смыслов v2 (Web2 Legacy Patch)

Этот патч дополняет основной хаб документации деталями из архива `the-last-os-web2`.

## 📥 Продуктовые смыслы (Product Hub)

### 1. Метафора "Spatial Hypervisor" и "Unity для ИИ"
- **Что**: Описание ОС как гипервизора, который управляет не виртуалками, а пространственными потоками работы. Сравнение с игровым движком для софта.
- **Источник**: `web2/manifesto.md`.
- **Куда**: [manifesto.md](file:///c:/nopoint/the-last-os/.docs/product/manifesto.md) (раздел "The Grid Architecture").

### 2. Конкретика управления (Shortcuts & Interaction)
- **Что**: Описание шорткатов (`Cmd+K`, `Space+Drag`) и механики Double-Click для выбора всей группы.
- **Источник**: `web2/user_guide_ru.md`.
- **Куда**: [spatial_experience.md](file:///c:/nopoint/the-last-os/.docs/product/spatial_experience.md) (создать или дополнить раздел "Interaction Model").

---

## 🏗 Технические записи (Technical Hub)

### 1. Подробная схема AppState (SolidJS + Yrs)
- **Что**: Техническое описание структуры `AppState` и `Component` (включая `preSnapState`, `attachedTo`).
- **Источник**: `web2/api_reference_ru.md`.
- **Куда**: [state_management.md](file:///c:/nopoint/the-last-os/.docs/technical/shell/state_management.md).

### 2. Оптимизация групповых движений (`groupTransform`)
- **Что**: Механика `Visual Overrides` и использование `Snapshot Baseline` для исключения дрейфа окон при групповом драге.
- **Источник**: `web2/frontend_architecture_ru.md`.
- **Куда**: [spatial_math.md](file:///c:/nopoint/the-last-os/.docs/technical/shell/spatial_math.md) (раздел "Interaction Physics").

### 3. Agent Manifest (JSON Spec)
- **Что**: Пример спецификации агента (Permissions, Triggers, UI path).
- **Источник**: `web2/agent_guide_ru.md`.
- **Куда**: [agent_manifest.md](file:///c:/nopoint/the-last-os/.docs/agent_manifest.md).

### 4. Cloudflare Infrastructure (R2, WebTransport)
- **Что**: Использование Cloudflare R2 для бэкапов и WebTransport для релея.
- **Источник**: `web2/backend_architecture_ru.md`.
- **Куда**: [infrastructure_ops.md](file:///c:/nopoint/the-last-os/.docs/technical/infrastructure_ops.md).

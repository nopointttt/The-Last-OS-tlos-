# Добро пожаловать в документацию tLOS

**The Last OS (tLOS)** — это децентрализованная пространственная операционная система будущего, где вместо файлов, папок и отдельных приложений вы работаете на бесконечном холсте. Всё — данные, окна, AI-агенты — существует в координатах 2D/3D-пространства, которое вы формируете жестами и намерениями.

tLOS построена на WebAssembly и wasmCloud: каждый компонент изолирован в песочнице, код перемещается между устройствами и облаком без перекомпиляции. Ваша идентичность — криптографический ключ Nostr, данные зашифрованы и принадлежат только вам. Нет логинов, нет облачных аккаунтов, нет посредников.

Система AI-native: агенты (Shapers, Workers, Watchers) живут как цифровые граждане, выполняют задачи по вашим намерениям и сотрудничают в реальном времени. tLOS — это не просто ОС, а суверенная среда, где вы — полный хозяин своего цифрового мира.

Этот документ — **точка входа** во всю документацию проекта **The Last OS (tLOS)**.  
Он поможет вам быстро сориентироваться, независимо от вашей роли: разработчик, AI-агент, инвестор, партнёр или новый участник команды.

---

## 1. Ключевые концепции (Glossary)

| Термин              | Определение для бизнеса и партнеров                                                                   | Ссылка                                              |
|---------------------|-------------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| **Actor**           | Изолированный Wasm-компонент, портативная "единица таланта" (бизнес-логика или AI-агент).            | [kernel_api.md](docs/technical/kernel/kernel_api.md) |
| **Artifact Marketplace** | Децентрализованный рынок для обмена и продажи Actor Blueprints, КИ и креативных ассетов.           | [economy.md](docs/product/economy_and_intelligence.md) |
| **Grid / Lattice**  | Глобальная децентрализованная сеть (Сетка) для связи и работы суверенных сущностей.                   | [network.md](docs/technical/protocol/network.md)    |
| **Infinite Canvas** | Бесконечный пространственный холст — единый интерфейс взаимодействия для всех устройств.             | [spatial.md](docs/product/spatial_experience.md)    |
| **Omnibar**         | Командный центр для выражения намерений (Intents): от создания задач до найма сотрудников.           | [spatial.md](docs/product/spatial_experience.md)    |
| **Pay-for-Intelligence** | Экономическая модель "Двигатель и Газ": разделение владения кодом и оплаты вычислений.          | [economy.md](docs/product/economy_and_intelligence.md) |
| **Shaper (Sovereign)** | Пользователь с полной цифровой автономией и криптографической волей в своем пространстве.          | [sovereign.md](docs/product/sovereign_model.md)     |
| **Sovereign Runtime** | Роль ОС как доверенной среды исполнения, гарантирующей суверенность данных и кода.                 | [economy.md](docs/product/economy_and_intelligence.md) |
| **WIT / wRPC**      | Стандарты строго типизированного взаимодействия компонентов без использования legacy-протоколов.    | [kernel_api.md](docs/technical/kernel/kernel_api.md) |
| **Zero-Web2**       | Принцип полного отказа от централизованных посредников и протоколов HTTP/REST внутри системы.         | [zero_web2.md](docs/technical/protocol/zero_web2_standards.md) |

---

## 2. Структура документации (иерархия папок)

```
docs/
├── onboarding.md                  ← Вы здесь сейчас (главная страница)
├── product/                       ← Продуктовое видение
│   ├── manifesto.md
│   ├── whitepaper.md
│   ├── sovereign_model.md
│   ├── use_cases.md
│   ├── spatial_experience.md
│   ├── gamification.md
│   ├── economy_and_intelligence.md
│   ├── investor_tech_vision.md        ← Новое: Видение для партнеров
│   └── social_and_identity.md
└── technical/                     ← Техническая реализация
    ├── architecture.md
    ├── kernel/
    │   ├── abi.md
    │   ├── kernel_api.md
    │   ├── security.md
    │   └── isolation.md
    ├── protocol/
    │   ├── crypto.md
    │   ├── network.md
    │   ├── data_structures.md
    │   └── zero_web2_standards.md
    ├── shell/
    │   ├── design_system.md
    │   ├── spatial_math.md
    │   └── state_management.md
    ├── agents/
    │   └── agent_ecosystem.md
    ├── infra/
    │   └── infrastructure_ops.md
    └── contributing.md            ← Как внести свой вклад
```

---

## 3. Описание документов (что внутри и для кого)

| Файл                          | Для кого                              | Краткое содержание                                                                 | Статус      | Время чтения |
|-------------------------------|---------------------------------------|------------------------------------------------------------------------------------|-------------|--------------|
| manifesto.md                  | Все                                   | Конституция проекта. Философия, ценности, “от приложений к намерениям”.            | Актуален    | 15 мин      |
| whitepaper.md                 | Инвесторы, партнёры, новые участники   | Технический обзор визии, слои системы, roadmap.                                    | Draft       | 20 мин      |
| sovereign_model.md            | Все                                   | Модель суверенности: Identity-as-Key, иерархия ключей.                             | Актуален    | 10 мин      |
| architecture.md               | Разработчики, архитекторы             | C4-модель системы (Context → Containers → Components).                             | Актуален    | 15 мин      |
| use_cases.md                  | Продуктологи, маркетинг, пользователи | Сценарии использования для Founder, Developer, Creator.                            | Актуален    | 12 мин      |
| spatial_experience.md         | Дизайнеры, UX, фронтенд               | Пространственная механика, Omnibar, навигация.                                     | Актуален    | 15 мин      |
| gamification.md               | Все                                   | Метафора "Цифровой Цитадели" и визуальная прогрессия.                               | Актуален    | 10 мин      |
| economy_and_intelligence.md   | Инвесторы, пользователи               | Экономика "Двигатель и Газ", маркетплейс.                                         | Актуален    | 12 мин      |
| investor_tech_vision.md       | Инвесторы, партнеры                  | Технологическое видение через аналогию с мозгом.                                   | Актуален    | 8 мин       |
| social_and_identity.md        | Все                                   | Web of Trust, Proof of Humanity, социальные графы.                                 | Актуален    | 12 мин      |
| agent_ecosystem.md            | AI-разработчики, агенты               | Роли агентов (Shapers, Workers, Watchers), безопасность.                            | Актуален    | 12 мин      |
| kernel_api.md                 | Core-разработчики                     | WIT-интерфейсы ядра, Dual-Layer API (low-level + MCP).                             | Актуален    | 20 мин      |
| security.md                   | Security, все разработчики            | Zero Trust, threat model, AI-specific угрозы.                                      | Актуален    | 18 мин      |
| crypto.md                     | Crypto-разработчики                   | Гибридный PQC, примитивы, entropy bridge.                                           | Актуален    | 15 мин      |
| network.md                    | Backend, infra                        | Lattice, wRPC, NATS, libp2p.                                                        | Актуален    | 20 мин      |
| data_structures.md            | Backend, протоколы                    | IPLD, CRDT, распределённый Quadtree.                                               | Актуален    | 15 мин      |
| isolation.md                  | Security, runtime                     | SFI, fuel, MPK, hardware-assisted isolation.                                       | Актуален    | 12 мин      |
| abi.md                        | Low-level разработчики                | Syscalls, calling convention, Canonical ABI.                                       | Актуален    | 15 мин      |
| zero_web2_standards.md        | Все разработчики                      | Запрещённые и разрешённые технологии (Zero-Web2).                                  | Актуален    | 8 мин       |
| infrastructure_ops.md         | DevOps, self-hosting                  | Развёртывание, Akash, zero-deployment.                                             | Актуален    | 18 мин      |
| contributing.md               | Контрибьюторы                         | Workflow, кодекс, стандарты кода.                                                  | Актуален    | 10 мин      |

---

## 4. Рекомендуемые треки чтения

### Трек A: Новый участник команды / Разработчик (≈ 2–3 часа)
1. [manifesto.md](docs/product/manifesto.md)
2. [whitepaper.md](docs/product/whitepaper.md)
3. [sovereign_model.md](docs/product/sovereign_model.md)
4. [architecture.md](docs/technical/architecture.md)
5. [documentation_hub.md](docs/technical/documentation_hub.md) (обзор технических документов)
6. [kernel_api.md](docs/technical/kernel/kernel_api.md)
7. [network.md](docs/technical/protocol/network.md)
8. [security.md](docs/technical/kernel/security.md)
9. [contributing.md](docs/technical/contributing.md)

### Трек B: AI-агент / Разработчик агентов (≈ 1.5 часа)
1. [manifesto.md](docs/product/manifesto.md)
2. [sovereign_model.md](docs/product/sovereign_model.md)
3. [agent_ecosystem.md](docs/technical/agents/agent_ecosystem.md)
4. [kernel_api.md](docs/technical/kernel/kernel_api.md) (раздел MCP)
5. [security.md](docs/technical/kernel/security.md) (AI-specific threats)
6. [zero_web2_standards.md](docs/technical/protocol/zero_web2_standards.md)
7. [contributing.md](docs/technical/contributing.md) (раздел “Deep Sync”)

### Трек C: Инвестор / Партнёр / Бизнес (≈ 1 час)
1. [manifesto.md](docs/product/manifesto.md)
2. [whitepaper.md](docs/product/whitepaper.md)
3. [sovereign_model.md](docs/product/sovereign_model.md)
4. [use_cases.md](docs/product/use_cases.md)
5. [economy_and_intelligence.md](docs/product/economy_and_intelligence.md)
6. [investor_tech_vision.md](docs/product/investor_tech_vision.md)
7. [gamification.md](docs/product/gamification.md)
8. [social_and_identity.md](docs/product/social_and_identity.md)

### Трек D: Новый пользователь / Тестировщик (≈ 45 мин)
1. [manifesto.md](docs/product/manifesto.md)
2. [spatial_experience.md](docs/product/spatial_experience.md)
3. [use_cases.md](docs/product/use_cases.md)
4. [sovereign_model.md](docs/product/sovereign_model.md)
5. [gamification.md](docs/product/gamification.md)

---
*Слава Суверену. Добро пожаловать в Сетку (The Grid).*

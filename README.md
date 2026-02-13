# ONBOARDING.md: Добро пожаловать в документацию tLOS

Этот документ — **точка входа** во всю документацию проекта **The Last OS (tLOS)**.  
Он поможет вам быстро сориентироваться, независимо от вашей роли: разработчик, AI-агент, инвестор, партнёр или новый участник команды.

---

## 1. Глоссарий (Alphabetical)

| Термин              | Определение                                                                                           | Ссылка на основной документ                          |
|---------------------|-------------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| **Actor**           | Изолированный Wasm-компонент (приложение или агент), выполняющий бизнес-логику.                      | kernel_api.md, agent_ecosystem.md                    |
| **Capability Provider** | Хостовая служба, предоставляющая актёрам доступ к ресурсам (crypto, http, kv и т.д.).             | architecture.md                                     |
| **CRDT**            | Conflict-free Replicated Data Types — структуры данных для бесконфликтной синхронизации.            | data_structures.md                                   |
| **Grid / Lattice**  | Децентрализованная сеть узлов на базе NATS + wRPC. Синонимы: The Grid, Lattice.                     | network.md                                          |
| **Infinite Canvas** | Бесконечный пространственный холст — основная метафора интерфейса tLOS.                              | spatial_experience.md, spatial_math.md               |
| **Shaper**          | Главный пользователь системы (Sovereign). Тот, кто выражает намерения и управляет пространством.     | sovereign_model.md, manifesto.md                     |
| **Sovereign**       | Пользователь с полной криптографической автономией (Identity-as-Key).                                | sovereign_model.md                                  |
| **Spatial Index**   | Распределённое квадродерево (Quadtree) для поиска объектов на холсте.                                | data_structures.md, spatial_math.md                 |
| **wRPC**            | WIT over RPC — основной транспорт для вызовов между актёрами.                                        | network.md                                          |
| **WIT**             | WebAssembly Interface Types — типизированные интерфейсы компонентов.                                 | kernel_api.md                                       |
| **Zero-Web2**       | Принцип запрета использования HTTP/REST и других централизованных протоколов внутри системы.        | zero_web2_standards.md                              |

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
1. manifesto.md
2. whitepaper.md
3. sovereign_model.md
4. architecture.md
5. documentation_hub.md (обзор технических документов)
6. kernel_api.md
7. network.md
8. security.md
9. contributing.md

### Трек B: AI-агент / Разработчик агентов (≈ 1.5 часа)
1. manifesto.md
2. sovereign_model.md
3. agent_ecosystem.md
4. kernel_api.md (раздел MCP)
5. security.md (AI-specific threats)
6. zero_web2_standards.md
7. contributing.md (раздел “Deep Sync”)

### Трек C: Инвестор / Партнёр / Бизнес (≈ 1 час)
1. manifesto.md
2. whitepaper.md
3. sovereign_model.md
4. use_cases.md
5. economy_and_intelligence.md
6. gamification.md
7. social_and_identity.md

### Трек D: Новый пользователь / Тестировщик (≈ 45 мин)
1. manifesto.md
2. spatial_experience.md
3. use_cases.md
4. sovereign_model.md
5. gamification.md

---
*Слава Суверену. Добро пожаловать в Сетку (The Grid).*

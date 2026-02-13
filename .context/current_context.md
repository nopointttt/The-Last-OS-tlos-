# Current Context & Focus
> **How to use**: This file captures the *immediate* state of "The Last OS". Read this to understand "where we left off".

## 🎯 Current Focus: NATS Connectivity & Assembly Loop
**Session ID**: `5fde9f4c-54e0-4636-afbf-d5fb89fd347b` (2026-02-13)

### 🟢 Completed:
- **Assembly Pipeline**: Реализован `Assembler Actor`, `UUPRenderer` (SolidJS) и `Intent Resolver`.
- **Spatial Actor**: Реализован индекс Quadtree (Rust Actor).
- **Hardened Shell**: Введен авто-реконнект к Латице и принудительный IPv4 (`127.0.0.1`).
- **Clean Dev**: Почищены все ворнинги компилятора, настроен "красивый" лог в консоли и детальный в `.temp/shell.log`.

- **NATS Server**: Установлен и запущен (`nats-server`).
- **Dynamic Discovery**: Реализован механизм авто-поиска акторов через NATS-пульс (heartbeats).
- **wRPC Fixes**: Исправлены сигнатуры и префиксы (`wasmbus.rpc`) в `lattice_bridge.rs`.

## 💡 Recent Decisions & Insights
- **Resilient Connection**: Shell теперь запускает поток подключения в фоне, позволяя остальному интерфейсу работать.
- **Diagnostics First**: В `.temp/shell.log` теперь пишется всё, что происходит "под капотом" моста.

## 📦 System State
- **Wash Version**: v2.0.0-rc.7
- **Dependencies**: Fixed at `wrpc-transport` 0.28.4 & `async-nats` 0.39.0.

## 🔜 Следующие шаги
1.  **Lattice Up**: Запустить систему (nats -> wash dev -> shell).
2.  **Verifier**: Добиться статуса `Discovery: Found ... Actor ID` в Shell.
3.  **End-to-End**: Проверить `/open test` в браузере.
3.  **End-to-End**: Проверить `/open test` — должен появиться UUP-панель.
4.  **Spatial Persistence**: Реализовать хранение состояния Quadtree в KV-хранилище Латицы.

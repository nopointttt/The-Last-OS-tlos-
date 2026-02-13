# Spec: Spatial Actor (Quadtree Index)

**Status**: Draft

## 1. Контекст и Проблема
*   **Research**: [spatial_experience.md](file:///c:/nopoint/the-last-os/.docs/product/spatial_experience.md)
*   **Проблема**: В "The Last OS" сотни окон и агентов существуют на бесконечном холсте. Простой перебор всех объектов для отрисовки или взаимодействия (O(N)) приведет к лагам при росте системы.
*   **Почему это важно**: Пространственная эффективность — это ядро UX. Нам нужен быстрый поиск объектов в заданной области (Frustum Culling) и детекция коллизий.

## 2. Решение (The Bet)
*   **Концепция**: Создание выделенного wasmCloud-актора `Spatial`, который хранит состояние холста в структуре **Quadtree** (Четверичное дерево).
*   **Fat Marker Sketches**: 
    - Актор принимает координаты объектов (x, y, width, height).
    - При запросе `GetInRegion(rect)` возвращает список ID объектов.
    - Все данные хранятся в памяти актора (In-memory) для максимальной скорости.

## 3. Scope (Границы)
### In Scope (Что делаем)
*   [ ] Определение WIT-интерфейса `tlos:spatial/index`.
*   [ ] Реализация Quadtree на Rust (без внешних тяжелых зависимостей).
*   [ ] Поддержка операций: `Insert`, `Update` (Move), `Remove`, `QueryRegion`.
*   [ ] Интеграция с NATS Messaging для уведомлений о перемещении объектов.

### Out of Scope (Что НЕ делаем)
*   [ ] Персистентность Quadtree (в этой итерации — только In-memory).
*   [ ] 3D (Z-ось) — только 2D холст.
*   [ ] Сложная физика столкновений.

### Rabbit Holes (Risks)
*   **Wasm Memory Limits**: При огромном количестве объектов Quadtree может упереться в лимиты памяти Wasm (4GB). Для MVP это не проблема.
*   **Concurrency**: Множество одновременных обновлений координат может создать гонку данных. wasmCloud акторы однопоточны по своей природе (Stateless/Actor model), что упрощает задачу.

## 4. Технические Детали
*   **Стек**: Rust, wasmCloud Component Model (WASI P2), WIT.
*   **Интерфейс (WIT)**:
    ```wit
    package tlos:spatial;

    interface index {
        record point { x: f64, y: f64 }
        record rect { x: f64, y: f64, w: f64, h: f64 }
        record spatial-object { id: string, bounds: rect }

        insert: func(obj: spatial-object);
        update: func(id: string, new-bounds: rect);
        remove: func(id: string);
        query-region: func(region: rect) -> list<string>;
    }
    ```

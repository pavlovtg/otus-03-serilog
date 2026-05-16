# System Patterns

## Структура проекта
- `src/Serilog/` — основная библиотека (единственный публичный пакет).
- `test/Serilog.Tests/` — unit-тесты (xUnit).
- `test/Serilog.PerformanceTests/` — бенчмарки (BenchmarkDotNet).
- `test/Serilog.ApprovalTests/` — approval-тесты публичного API.
- `homework/` — учебные материалы и промпты ДЗ.
- `.clinerules/` — правила и скиллы для Cline.
- `docs/ai/memory-bank/` — memory bank агента.

## Ключевые паттерны
- **Pipeline:** `LoggerConfiguration` → `Logger` → `ILogEventSink` (chain of sinks).
- **Enrichment:** `ILogEventEnricher` добавляет свойства к каждому событию.
- **Destructuring:** `IDestructuringPolicy` / `PropertyValueConverter` — контроль сериализации объектов.
- **Fluent builder:** вся конфигурация через `LoggerConfiguration` (`.WriteTo`, `.Enrich`, `.Filter`, `.MinimumLevel`).
- **Immutable logger:** `Logger` — zero-shared-state; глобальный `Log.Logger` — опциональный синглтон.

## Ограничения
- Не менять публичный API без обновления `Serilog.approved.txt`.
- Не добавлять внешние зависимости в `src/Serilog/` (zero-dependency core).

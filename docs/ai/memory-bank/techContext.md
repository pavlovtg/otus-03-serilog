# Tech Context

- **Язык:** C# (.NET 8+, также поддерживает net462, netstandard2.0).
- **Сборка:** `dotnet build Serilog.sln`; версии управляются через `Directory.Version.props`.
- **Тесты:** `dotnet test` (xUnit); approval-тесты в `Serilog.ApprovalTests`.
- **Бенчмарки:** BenchmarkDotNet, запуск через `RunPerfTests.ps1`.
- **Пакет:** NuGet, публикуется как `Serilog`; zero external dependencies в core.
- **CI:** GitHub Actions (`.github/workflows/ci.yml` в upstream).
- **Инструмент AI:** Cline (VS Code), правила в `.clinerules/`, memory bank в `docs/ai/memory-bank/`.

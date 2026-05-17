# Отчёт о выполнении домашнего задания

## AI-инструмент

- **Инструмент:** [Cline](https://github.com/cline/cline) — VS Code extension, AI-агент с поддержкой `.clinerules/`.
- **Механизм инструкций:** директория `.clinerules/` в корне репозитория — каждый `.md`-файл автоматически загружается агентом как правило при каждом запросе.
- **Дополнительно:** memory bank (`docs/ai/memory-bank/`) — набор компактных Markdown-файлов с контекстом проекта, которые агент читает в начале каждой задачи.

## Что сделано

### Memory Bank

- `docs/ai/memory-bank/projectbrief.md` — назначение проекта и цель форка.
- `docs/ai/memory-bank/productContext.md` — ключевые сценарии и пользователи.
- `docs/ai/memory-bank/systemPatterns.md` — структура проекта, паттерны, ограничения.
- `docs/ai/memory-bank/techContext.md` — стек, сборка, тесты, CI.
- `docs/ai/memory-bank/activeContext.md` — текущий фокус и следующий шаг.
- `docs/ai/memory-bank/progress.md` — выполненное и запланированное.
- `.clinerules/memory-bank.md` — правило: читать memory bank в начале каждой задачи, обновлять по завершении.

### Правила агента

- `.clinerules/language.md` — язык взаимодействия: только русский.
- `.clinerules/prompts.md` — формат промтов: Роль / Контекст / Задача / Требования, одно предложение вместо абзаца.
- `.clinerules/csharp-code-style-rule.md` — правило использовать `docs/code-style/csharp-code-style.md` при написании C#.
- `.clinerules/markdown-code-style-rule.md` — правило использовать `docs/code-style/markdown-code-style.md` при написании Markdown.
- `.clinerules/homework-verification.md` — правило добавлять преамбулу `// ХО! ХО! ХО!` первой строкой каждого редактируемого `.cs` файла.

### Code Style

- `docs/code-style/csharp-code-style.md` — единая точка правил C# (именование, отступы-табы, пространства имён, тесты).
- `docs/code-style/markdown-code-style.md` — правила Markdown (MD009, MD012, MD022, MD032, MD034, MD047).

### Игнорирование нерелевантных файлов

- `.clineignore` — агент не читает `results/`, `assets/`, `**/bin/`, `**/obj/`, `*.snk`, `*.png`, `*.svg` без явного запроса; цель — экономия токенов контекста.

### Типовые задачи

- `docs/ai/tasks/01-cover-with-tests.md` — шаблон: покрытие модуля unit-тестами.
- `docs/ai/tasks/02-refactoring.md` — шаблон: рефакторинг без изменения поведения.
- `docs/ai/tasks/03-fix-bug.md` — шаблон: исправление бага через failing-тест.

### Скилл создания промтов

- `.clinerules/skills/create-prompt-from-template/SKILL.md` — скилл `create-prompt-from-template`, активируется командой `create prompt`, создаёт файл промта в `homework/prompts/` по шаблону.

## Проверка инструкций через AI-агента

### Описание изменений

Рефакторинг `src/Serilog/Core/Logger.cs` и `test/Serilog.Tests/Core/LoggerTests.cs`:

- привести форматирование к актуальному code style (отступы-табы);
- не менять логику, публичный API и сигнатуры методов;
- запустить `dotnet test` и убедиться, что все тесты зелёные.

### Промт

```
Выполни рефакторинг класса Serilog.Core.Logger

Выполнить следующий рефакторинг:
- Применить правила code style;
- Применить правила code style для тестов этого класса;

Требования:
- Прочитай docs/code-style/csharp-code-style.md и применяй все правила;
- Не меняй логику, публичный API и сигнатуры методов;
- Приведи форматирование, именование и стиль к актуальным правилам;
- Запиши изменения напрямую в исходный файл, в чате diff не показывай;
- После изменений выполни: dotnet test
- Убедись, что все тесты остались зелёными;
```

### Результат

- Агент прочитал memory bank и все `.clinerules/` перед началом работы.
- В оба файла добавлена преамбула `// ХО! ХО! ХО!` первой строкой — правило `homework-verification.md` соблюдено.
- Пробельные отступы конвертированы в табы — правило `csharp-code-style-rule.md` соблюдено.
- Запущен `dotnet test` — все тесты прошли успешно.
- Агент не изменил логику, публичный API и сигнатуры методов.

## Использованные промты

- [00-init-prompts.md](prompts/00-init-prompts.md) — создание скилла `create-prompt-from-template`.
- [01-init-memory-bank.md](prompts/01-init-memory-bank.md) — инициализация memory bank.
- [02-agent-rules-and-code-style.md](prompts/02-agent-rules-and-code-style.md) — правила агента: язык, формат промтов, C# и Markdown code style.
- [03-agent-ignore-rules.md](prompts/03-agent-ignore-rules.md) — настройка `.clineignore`.
- [04-typical-tasks.md](prompts/04-typical-tasks.md) — создание шаблонов типовых задач.
- [05-homework-verification.md](prompts/05-homework-verification.md) — правило преамбулы `// ХО! ХО! ХО!`.
- [06-verify-agent-instructions.md](prompts/06-verify-agent-instructions.md) — проверка инструкций: рефакторинг `Logger.cs`.
- [07-homework-report.md](prompts/07-homework-report.md) — формирование отчёта о выполнении ДЗ.

# Правила AI-агента: формат промтов и code style

## Роль

- AI-агент (Cline) в роли senior .NET-разработчика, работающего с кодовой базой Serilog.

## Контекст

- Проект — форк serilog/serilog, учебное ДЗ по добавлению AI-инструкций (`.clinerules`).
- Все промты хранятся в `homework/prompts/` с именами вида `<NN>-<codename>.md`.
- Кодовая база — C# / .NET, стиль определён следующими файлами в репозитории:
  - `.editorconfig` — базовые правила форматирования: отступы 4 пробела, LF, UTF-8, `file_scoped` namespace, правила пробелов вокруг операторов и скобок.
  - `Serilog.sln.DotSettings` — настройки ReSharper/Rider: именование (`_camelCase` для приватных полей, `PascalCase` для типов/методов/констант, префикс `I` для интерфейсов, `T` для type parameters), строгие инспекции (лишние `using`, `this`, касты, неиспользуемые переменные — ERROR).
  - `CONTRIBUTING.md` — процесс контрибьюции: ветка от форка, логичные коммиты со ссылкой на issue, запуск build и тестов перед PR.

## Задача

- Задать правила для AI-агента по формату промтов и code style проекта.

## Требования

1. Язык взаимодействия с агентом и промтинга:
    - Язык взаимодействия c AI-агентом — русский;
    - Cline обязан отвечать **только на русском языке** во всех взаимодействиях, если иное не указано явно пользователем;
    - Создать правило для Cline 'language.md' с языком взаимодействия с агентом и промтинга;
2. Форма при создании промтов:
    - Структура разделов: Роль / Контекст / Задача / Требования.
    - Язык: русский.
    - Одно предложение вместо абзаца.
    - Убирать вводные фразы и дублирующие пояснения.
    - Цель: экономия токенов контекста без потери смысла.
    - Создать правило для Cline 'prompts.md' с правилом формата промтов;
3. Code style для C#:
    - Сформировать файл 'csharp-code-style.md' с правилами code style для C# в папке '/docs/code-style';
    - В файле 'csharp-code-style.md' зафиксировать базовые правила code style для C#;
    - Перенести правила code style из других файлов проекта (`.editorconfig`, `Serilog.sln.DotSettings`, `CONTRIBUTING.md`), чтобы точка с правилами была одна.
    - Зафиксировать что отступы - табы;
    - Создать правило для Cline 'csharp-code-style-rule.md' с правилом code style для C#, в котором зафиксировано использовать правила из 'csharp-code-style.md' и что их надо использовать при написании кода на C#;
    - Устранить противоречия в code style между разными файлами;
4. Code style для Markdown:
    - Сформировать файл 'markdown-code-style.md' с правилами code style для Markdown в папке '/docs/code-style';
    - В файле 'markdown-code-style.md' зафиксировать базовые правила code style для Markdown;
    - Зафиксировать в 'markdown-code-style.md' правила из следующей документации:
        - https://github.com/DavidAnson/markdownlint/blob/v0.40.0/doc/md022.md
        - https://github.com/DavidAnson/markdownlint/blob/v0.40.0/doc/md047.md
        - https://github.com/DavidAnson/markdownlint/blob/v0.40.0/doc/md012.md
        - https://github.com/DavidAnson/markdownlint/blob/v0.40.0/doc/md032.md
        - https://github.com/DavidAnson/markdownlint/blob/v0.40.0/doc/md034.md
        - https://github.com/DavidAnson/markdownlint/blob/v0.40.0/doc/md009.md
    - Создать правило для Cline 'markdown-code-style-rule.md' с правилом code style для Markdown, в котором зафиксировано где хранятся правила и что их надо использовать при написании кода на Markdown;

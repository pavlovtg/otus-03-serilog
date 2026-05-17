# C# Code Style

## Форматирование

- Отступы — табы (`indent_style = tab`).
- Кодировка — UTF-8.
- Окончания строк — LF.
- Файл заканчивается пустой строкой (`insert_final_newline = true`).
- Trailing whitespace удаляется (`trim_trailing_whitespace = true`).
- Для `.csproj`, `.json`, `.config`, `.yml`, `.props` — отступ 2 пробела.

## Namespace

- Стиль объявления namespace — `file_scoped` (`csharp_style_namespace_declarations = file_scoped`).

## Пробелы

- Пробел после ключевых слов управляющих конструкций (`if`, `for`, `while` и т.д.).
- Пробелы вокруг бинарных операторов.
- Пробел после запятой, не перед запятой.
- Нет пробела после каста (`(int)x`, не `(int) x`).
- Нет пробела между именем метода и открывающей скобкой.
- Нет пробела внутри скобок параметров/аргументов.
- Нет пробела перед/после точки.
- Нет пробела перед/после квадратных скобок.

## Именование

- Типы, namespace, методы, свойства, события, enum-члены, публичные поля — `PascalCase`.
- Приватные поля (instance и static) — `_camelCase` (префикс `_`).
- Локальные переменные, параметры, локальные константы — `camelCase`.
- Интерфейсы — префикс `I` + `PascalCase` (например, `ILogger`).
- Type parameters — префикс `T` + `PascalCase` (например, `TValue`).
- Константы (публичные и приватные) — `PascalCase`.
- Static readonly поля — `PascalCase`.

## Инспекции (ERROR — не допускаются)

- Лишние `using` директивы (`RedundantUsingDirective`).
- Лишний квалификатор `this` (`RedundantThisQualifier`).
- Избыточные касты (`RedundantCast`).
- Неиспользуемые переменные (`UnusedVariable`, `NotAccessedVariable`).
- Неиспользуемые локальные поля (`NotAccessedField.Local`).
- Пустые конструкторы (`EmptyConstructor`).
- Пустые деструкторы (`EmptyDestructor`).
- Пустые catch-блоки без типа (`EmptyGeneralCatchClause`).
- Пустые namespace (`EmptyNamespace`).
- Избыточные присваивания (`RedundantAssignment`).
- Избыточные вызовы базового конструктора (`RedundantBaseConstructorCall`).
- Неиспользуемые параметры методов (`ValueParameterNotUsed`).
- Статические поля в generic-типах (`StaticFieldInGenericType`).
- Двойное отрицание (`DoubleNegationOperator`).

## Использование `var`

- Использовать `var` везде, где тип очевиден (`SuggestUseVarKeywordEvident = ERROR`).

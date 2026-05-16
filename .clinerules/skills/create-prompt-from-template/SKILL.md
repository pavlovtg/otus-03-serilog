---
name: create-prompt-from-template
description: Создаёт файл промта в папке homework/prompts/ по шаблону. Активируется командой "create prompt".
allowed-tools: list_files, read_file, write_to_file, ask_followup_question
---

# Skill: create-prompt-from-template

Активируется по команде `create prompt`.

## Workflow

1. **Запросить codename** у пользователя — краткое название промта латиницей через дефис (например, `add-logging`, `fix-tests`).

2. **Определить следующий индекс**:
   - Прочитать список файлов в папке `homework/prompts/`.
   - Найти файлы с именами вида `<NN>-*.md`.
   - Взять максимальный числовой префикс и прибавить 1.
   - Если файлов нет — начать с `01`.
   - Отформатировать индекс с ведущим нулём (01, 02, …, 09, 10, 11, …).

3. **Прочитать шаблон** из файла `.clinerules/skills/templates/prompt.md`.

4. **Создать файл** `homework/prompts/<index>-<codename>.md` с содержимым шаблона.

5. **Сообщить пользователю** путь к созданному файлу и предложить заполнить разделы.

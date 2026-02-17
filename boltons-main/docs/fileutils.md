# `fileutils`

Модуль `boltons_practical.fileutils` содержит утилиты для работы с файловой системой с упором на предсказуемость и целостность данных.

## `ensure_dir(path)` / `mkdir_p(path)`

Гарантированно создаёт директорию (включая родителей), аналог `mkdir -p`.

Пример:

```python
from boltons_practical import ensure_dir

ensure_dir("data/tmp")
```

## `iter_find_files(root, pattern="*", include_dirs=False)`

Лениво обходит дерево каталогов от `root` и возвращает `Path` по glob‑маске.

Пример:

```python
from boltons_practical import iter_find_files

for p in iter_find_files(".", "*.py"):
    print(p)
```

## `safe_write_text(path, data, encoding="utf-8", newline=None)`

Записывает текст через временный файл и затем атомарно заменяет целевой файл (`replace()`).

Полезно, когда:
- нельзя оставлять “обрубленный” файл при сбое;
- файл читается другими процессами.

Пример:

```python
from boltons_practical import safe_write_text

safe_write_text("out/config.json", "{\n  \"debug\": true\n}\n")
```

## `copy_file_atomic(src, dst)`

Копирует файл в `dst` через временный файл и атомарную замену. Если `src` не существует — бросает `FileNotFoundError`.

Пример:

```python
from boltons_practical import copy_file_atomic

copy_file_atomic("in.txt", "backup/in.txt")
```

## `read_text_lines(path, encoding="utf-8", strip_newline=True)`

Итератор по строкам файла. По умолчанию удаляет символы перевода строки.

Пример:

```python
from boltons_practical import read_text_lines

for line in read_text_lines("data.txt"):
    print(line)
```

## `touch(path)`

Создаёт пустой файл, если его не было, и обновляет timestamp.

Пример:

```python
from boltons_practical import touch

touch("logs/app.log")
```



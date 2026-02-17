# Публичный API

Пакет `boltons_practical` реэкспортирует основные функции/классы из внутренних модулей, чтобы ими было удобно пользоваться “из одного места”.

## Реэкспортируемые подмодули

- `boltons_practical.fileutils`
- `boltons_practical.dictutils`
- `boltons_practical.iterutils`
- `boltons_practical.functional`

## Реэкспортируемые функции и классы

### `fileutils`

- `ensure_dir(path)`
- `mkdir_p(path)`
- `iter_find_files(root, pattern="*", include_dirs=False)`
- `safe_write_text(path, data, encoding="utf-8", newline=None)`
- `read_text_lines(path, encoding="utf-8", strip_newline=True)`
- `copy_file_atomic(src, dst)`
- `touch(path)`

### `dictutils`

- `FrozenDict(data)`
- `merge_dicts(base, *others, deep=False)`
- `pick(d, keys)`
- `omit(d, keys)`

### `iterutils`

- `chunked(iterable, size)`
- `windowed(iterable, size)`
- `unique_everseen(iterable)`

### `functional`

- `compose(*funcs)`
- `memoize(ttl=None)`



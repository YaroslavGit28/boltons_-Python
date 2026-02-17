# Установка и использование

## Требования

- Python 3.10+

## Установка (локально, режим разработки)

1) Создайте и активируйте виртуальное окружение.

Windows (PowerShell):

```bash
python -m venv .venv
.venv\Scripts\Activate.ps1
```

Linux / macOS:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

2) Установите пакет:

```bash
pip install -e ".[dev]"
```

## Запуск тестов

```bash
pytest -q
```

## Быстрый старт

```python
from boltons_practical import (
    FrozenDict,
    chunked,
    compose,
    ensure_dir,
    memoize,
    safe_write_text,
)

ensure_dir("data/tmp")
safe_write_text("data/tmp/demo.txt", "one\ntwo\n")

print(list(chunked(range(7), 3)))

cfg = FrozenDict({"env": "dev"})
to_upper = compose(str.upper, str)
print(to_upper(cfg["env"]))

@memoize(ttl=0.1)
def add(a: int, b: int) -> int:
    return a + b

print(add(1, 2))
print(add(1, 2))  # из кеша
```



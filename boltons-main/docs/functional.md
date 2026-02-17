# `functional`

Модуль `boltons_practical.functional` содержит простые строительные блоки для функционального стиля.

## `compose(*funcs)`

Создаёт функцию-композицию:

`compose(f, g, h)(x)` эквивалентно `f(g(h(x)))`.

Пример:

```python
from boltons_practical import compose

def inc(x: int) -> int:
    return x + 1

def dbl(x: int) -> int:
    return x * 2

fn = compose(str, dbl, inc)  # str(dbl(inc(x)))
print(fn(3))  # "8"
```

Ошибки:
- если не передать ни одной функции → `ValueError`

## `memoize(ttl=None)`

Декоратор мемоизации:
- кеширует результат по аргументам функции (`args` + отсортированные `kwargs`)
- при `ttl=None` кеш “вечный”
- при `ttl=<секунды>` запись протухает и пересчитывается

Пример (TTL):

```python
import time
from boltons_practical import memoize

calls = {"count": 0}

@memoize(ttl=0.1)
def slow_add(a: int, b: int) -> int:
    calls["count"] += 1
    return a + b

slow_add(1, 2)
slow_add(1, 2)
print(calls["count"])  # 1 (из кеша)

time.sleep(0.11)
slow_add(1, 2)
print(calls["count"])  # 2 (TTL истёк)
```

Важно:
- все аргументы должны быть хэшируемыми (иначе ключ кеша не построить)



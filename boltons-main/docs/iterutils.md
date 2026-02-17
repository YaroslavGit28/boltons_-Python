# `iterutils`

Модуль `boltons_practical.iterutils` содержит функции для “потоковой” обработки данных через итераторы.

## `chunked(iterable, size)`

Разбивает вход на чанки фиксированного размера. Последний чанк может быть короче.

Пример:

```python
from boltons_practical import chunked

print(list(chunked(range(7), 3)))  # [[0, 1, 2], [3, 4, 5], [6]]
```

Ошибки:
- если `size <= 0` → `ValueError`

## `windowed(iterable, size)`

Возвращает скользящее окно размера `size`.

Пример:

```python
from boltons_practical import windowed

print(list(windowed([1, 2, 3, 4], 3)))  # [[1, 2, 3], [2, 3, 4]]
```

Ошибки:
- если `size <= 0` → `ValueError`

## `unique_everseen(iterable)`

Удаляет дубликаты, сохраняя порядок первых вхождений.

Пример:

```python
from boltons_practical import unique_everseen

items = [1, 2, 1, 3, 2, 4]
print(list(unique_everseen(items)))  # [1, 2, 3, 4]
```



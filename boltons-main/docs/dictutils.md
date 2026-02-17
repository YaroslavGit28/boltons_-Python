# `dictutils`

Модуль `boltons_practical.dictutils` содержит небольшие, но часто используемые операции над словарями.

## `FrozenDict`

Иммутабельный словарь, который:
- ведёт себя как `Mapping`
- поддерживает `hash()`, поэтому может быть ключом другого словаря или элементом множества

Пример:

```python
from boltons_practical import FrozenDict

cfg = FrozenDict({"env": "dev", "debug": True})
cache = {cfg: "cached value"}
print(cache[cfg])
```

## `merge_dicts(base, *others, deep=False)`

Сливает словари в `base` (модифицируя его).

- При `deep=False` вложенные словари **перезаписываются**
- При `deep=True` вложенные словари **сливаются рекурсивно**

Пример:

```python
from boltons_practical import merge_dicts

base = {"a": 1, "nested": {"x": 1}}
other = {"b": 2, "nested": {"y": 2}}

print(merge_dicts(dict(base), other, deep=False)["nested"])  # {"y": 2}
print(merge_dicts(dict(base), other, deep=True)["nested"])   # {"x": 1, "y": 2}
```

## `pick(d, keys)`

Возвращает новый словарь, содержащий только указанные ключи. Отсутствующие ключи игнорируются.

Пример:

```python
from boltons_practical import pick

d = {"a": 1, "b": 2, "c": 3}
print(pick(d, ["a", "c", "z"]))  # {"a": 1, "c": 3}
```

## `omit(d, keys)`

Возвращает новый словарь без указанных ключей.

Пример:

```python
from boltons_practical import omit

d = {"a": 1, "b": 2, "c": 3}
print(omit(d, ["b"]))  # {"a": 1, "c": 3}
```



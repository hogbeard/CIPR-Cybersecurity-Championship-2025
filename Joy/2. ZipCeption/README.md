# ZipCeption

![alt text](Joy.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [level1.zip](level1.zip)
---
**Описание**:
---
Один архив? Не интересно. Два? Становится теплее. Больше 1000? Серьёзно? Кто это вообще сделал?..

**Description**:
---
One archive? Not interesting. Two? It's getting warmer. More than 1000? Seriously? Who did this anyway?..

**Решение**:
---
Дано 8192 архива, в последнем флаг. Можно решить, к примеру, через скрипт:

```
import os
import zipfile

current = "level1.zip"
for i in range(1, 8193):
    with zipfile.ZipFile(current) as z:
        name = z.namelist()[0]
        print(name)
        z.extract(name)
    os.remove(current)
    current = name

with open("flag.txt") as f:
    print(f.read)
```

Флаг: solar{z1pp3d_1n_d33p}

**Solution**:
---
Given 8192 archives, the last one has a flag. You can solve it, for example, via a script:

```
import os
import zipfile

current = "level1.zip"
for i in range(1, 8193):
    with zipfile.ZipFile(current) as z:
        name = z.namelist()[0]
        print(name)
        z.extract(name)
    os.remove(current)
    current = name

with open("flag.txt") as f:
    print(f.read)
```

Flag: solar{z1pp3d_1n_d33p}
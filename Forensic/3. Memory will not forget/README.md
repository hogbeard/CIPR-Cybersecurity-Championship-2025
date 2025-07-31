# Memory will not forget

![alt text](Forensic.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [mem.zip](mem.zip)
---
**Описание**:
---
Мы выгрузили память процесса на подозрительном сервере. Мы подозреваем, что она содержала зашифрованный сеансовый ключ. Но сам ключ не хранится в открытом доступе. Можете ли вы его найти?

**Description**:
---
We dumped a process memory on a suspicious server. We suspect it contained an encrypted session key. But the key itself is not stored in plaintext. Can you find it?

**Решение**:
---
Можно посмотреть на бинарь через **strings** и найти, что есть строка ENCODED, которая зашифрована в base64, далее расшифровываем и получаем флаг:

Флаг: solar{w0rk1ng_w1t4_m3m0ry_1s_f4n}

**Solution**:
---
You can look at the binary via **strings** and find that there is a string ENCODED, which is encrypted in base64, then decrypt it and get a flag:

Flag: solar{w0rk1ng_w1t4_m3m0ry_1s_f4n}
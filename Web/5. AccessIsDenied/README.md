# AccessIsDenied

![alt text](WEB.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [access.zip](access.zip)
---
**Описание**:
---
«Безопасный» портал администратора был развернут самоуверенными стажерами JSOC. 

Он включает вход в систему, сеансы, файлы cookie и даже защиту от перебора. 

Но что-то в логике сеанса и привилегий кажется неправильным...

У вас есть полный доступ к исходному коду приложения, и вы можете запустить его локально. 

Ваша задача — найти уязвимости, использовать их как цепочку и отправить их коды CWE в формате флага ниже. 

В коде или пользовательском интерфейсе нет скрытых флагов.

Единственно правильным представлением является ваш анализ уязвимости.

Формат флага: solar{CWE-XX,CWE-YY,CWE-ZZ}

Пожалуйста, отправьте все коды CWE в том порядке, в котором вы их используете.

**Description**: 
---
The "secure" admin portal was deployed by overconfident JSOC interns.

It includes login, sessions, cookies, and even brute force protection.

But something about the session and privilege logic seems wrong...

You have full access to the application source code and can run it locally.

Your job is to find vulnerabilities, use them as a chain, and submit their CWE codes in the flag format below.

There are no hidden flags in the code or UI.

The only correct representation is your vulnerability analysis.

Flag format: solar{CWE-XX,CWE-YY,CWE-ZZ}

Please submit all CWE codes in the order you use them.

**Решение**:
---
Необходимо было либо вручную, либо при помощи специализированных инструментов проанализировать исходный код, найти уязвимость и указать в виде флага CWE данной уязвимости.

Флаг: solar{CWE-502,CWE-269,CWE-22} (Deserialization, Improper Privilege Management, Path Traversal)

**Solution**:
---
It was necessary to either manually or with the help of specialized tools analyze the source code, find the vulnerability and indicate it as a CWE flag for this vulnerability.

Flag: solar{CWE-502,CWE-269,CWE-22} (Deserialization, Improper Privilege Management, Path Traversal)
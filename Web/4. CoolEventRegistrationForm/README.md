# CoolEventRegistrationForm

![alt text](WEB.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [reg.zip](reg.zip)
---
**Описание**:
---
Ваш друг попросил вас зарегистрироваться на супер крутое мероприятие и отправил вам ссылку. 

Вы замечаете подозрительную форму регистрации. Можете ли вы определить, что с ней не так? 

У вас есть полный доступ к исходному коду приложения, и вы можете запустить его локально. 

Ваша задача — найти уязвимости, использовать их как цепочку и отправить их коды CWE в формате флага ниже. 

В коде или пользовательском интерфейсе нет скрытых флагов. Единственной правильной отправкой является ваш анализ уязвимости. 

Формат флага: solar{CWE-XX,CWE-YY} Пожалуйста, отправьте оба кода CWE в том порядке, в котором вы их используете.

**Description**: 
---
Your friend asked you to register for a super cool event and sent you a link.

You notice a suspicious registration form. Can you figure out what's wrong with it?

You have full access to the application's source code and can run it locally.

Your job is to find vulnerabilities, use them as a chain, and submit their CWE codes in the flag format below.

There are no hidden flags in the code or UI. The only valid submission is your vulnerability analysis.

Flag format: solar{CWE-XX,CWE-YY} Please submit both CWE codes in the order you use them.

**Решение**:
---
Необходимо было либо вручную, либо при помощи специализированных инструментов проанализировать исходный код, найти уязвимость и указать в виде флага CWE данной уязвимости.

Флаг: solar{CWE-1333,CWE-1336} (Inefficient Regular Expression Complexity (ReDOS), SSTI).

**Solution**:
---
It was necessary to either manually or with the help of specialized tools analyze the source code, find the vulnerability and indicate it as a CWE flag for this vulnerability.

Flag: solar{CWE-1333,CWE-1336} (Inefficient Regular Expression Complexity (ReDOS), SSTI).
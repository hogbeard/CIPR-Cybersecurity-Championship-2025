# CoolLogin2000

![alt text](WEB.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [coollogin.zip](coollogin.zip)
---
**Описание**:
---
Наша «передовая» система входа была написана стажерами JSOC, которые клянутся, что ее невозможно взломать. 
Мы предлагаем вам взглянуть поближе! 

У вас есть полный доступ к исходному коду приложения, и вы можете запустить его локально. 

Ваша задача — найти уязвимости, использовать их как цепочку и отправить их коды CWE в формате флага ниже. 

В коде или пользовательском интерфейсе нет скрытых флагов. 

Единственная правильная отправка — это ваш анализ уязвимости. 

Формат флага: solar{CWE-XX,CWE-YY} 

Пожалуйста, отправьте оба кода CWE в том порядке, в котором вы их используете.

**Description**:
--- 
Our "cutting edge" login system was written by JSOC interns who swear it's unhackable.

We invite you to take a closer look!

You have full access to the application source code and can run it locally.

Your job is to find vulnerabilities, use them as a chain, and submit their CWE codes in the flag format below.

There are no hidden flags in the code or UI.

The only valid submission is your vulnerability analysis.

Flag format: solar{CWE-XX,CWE-YY}

Please submit both CWE codes in the order you use them.

**Решение**:
---
Необходимо было либо вручную, либо при помощи специализированных инструментов проанализировать исходный код, найти уязвимость и указать в виде флага CWE данной уязвимости.

Флаг: solar{CWE-79,CWE-384} (XSS, Session Fixation)

**Solution**:
---
It was necessary to either manually or with the help of specialized tools analyze the source code, find the vulnerability and indicate it as a CWE flag for this vulnerability.

Flag: solar{CWE-79,CWE-384} (XSS, Session Fixation)
# Warmup

![alt text](WEB.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [warm.zip](warm.zip)
---
**Описание**:
---
Ты — инженер по безопасности в команде AppSec.  
Разработчики прислали тебе клиентскую часть тестового веб-прототипа. Бэкенд пока не готов, но они уверяют, что «логика логина реализована корректно и безопасно» — и попросили сделать быструю проверку.

**Description**: 
---
You are a security engineer on the AppSec team.
The developers have sent you the client side of a test web prototype. The backend is not ready yet, but they assure you that "the login logic is implemented correctly and securely" - and asked you to do a quick check.

**Решение**:
---
>[!WARNING] 
>Здесь были две ошибки со стороны разработки в части:

>```h = (h * 31 + str.charCodeAt(i)) % 1000000007;```

>что значительно затрудняет подбор необходимого пароля,

>а также со стороны искомого пароля (он не словарный).

Сама задачка простая - необходимо посмотреть на код и понять, что флаг зависит от пароля, который вводим в форме логина. Далее необходимо было написать функцию, обратную данной в коде и получить пароль. 

Пароль - s0urceC0de. 

Флаг: solar{client_side_logic_revealed}

**Solution**:
---
>[!WARNING]
>There were two errors on the development side in the part:

>```h = (h * 31 + str.charCodeAt(i)) % 1000000007;```

>which significantly complicates the selection of the required password,

>as well as on the part of the sought password (it is not a dictionary password).

The task itself is simple - you need to look at the code and understand that the flag depends on the password that we enter in the login form. Then it was necessary to write a function inverse to the one given in the code and get the password.

Password - s0urceC0de.

Flag: solar{client_side_logic_revealed}
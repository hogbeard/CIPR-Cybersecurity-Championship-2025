# Phantom Payload

![alt text](Forensic.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [phantom.zip](phantom.zip)
---
**Описание**: 
---
Подозрительная активность была обнаружена на рабочей станции сотрудника company.sol.
Трафик выглядит как обычный DNS и HTTP, но... слишком много аномалий.
В отчете об инциденте указано: "данные могли передаваться по сети скрытым образом".

**Description**: 
---
Suspicious activity was detected from a company.sol employee's workstation.
The traffic appears to be normal DNS and HTTP, but... too many anomalies.
The incident report states: "data may have been transmitted over the network in a covert manner."

**Решение**:
---
Нужно понять аномалии в трафике:
1.	Много DNS-запросов на поддомены типа (s.company.sol, x.company.sol...)
2.	Есть пакеты на 10.10.10.10. без payload'а на TCP.window, который сильно больше обычного
3.	Часть ICMP-пакетов содержит IP Options типа 31 с длиной 3 и байтом данных

Первый кусок флага можно увидеть просто через фильтр (DNS-запросы):

```
    solar{F0ll
```

Для второго куска нужно понять логику передачи. Основное, что TCP.window нестандартное, а дальше нужно поанализировать и прийти к тому, что данные только в TCP.window % 4 == 0, а также что данные представлены в ASCII со смещением (val >> 2). Можно написать скрипт, который поможет это все достать:

```
tcp_chars = []

for pkt in packets:
    if TCP in pkt and pkt[IP].dst == "10.10.10.10":
        val = pkt[TCP].window
        if val % 4 == 0:
            ch = val >> 2
            if 32 <= ch <= 126:
                tcp_chars.append((pkt[TCP].seq, chr(ch)))

tcp_chars.sort(key=lambda x: x[0])
part2 = ''.join([c for _, c in tcp_chars])
print("TCP part:", part2)
```

И получим вторую часть флага:

```
    0w_th3_DN3
```

Третий кусок флага можно достать через фильтры (IPOption.type и пр.).
•	IPOption.type == 31
•	порядок по IP.ttl
либо через скрипт:

```
ipopt_chars = []

for pkt in packets:
    if IP in pkt and pkt[IP].dst == "172.16.0.1":
        for o in pkt[IP].options:
            try:
                if o.option == 31 and len(o.value) >= 1 and o.value[0] < 128:
                    ipopt_chars.append((pkt[IP].ttl, chr(o.value[0])))
            except:
                pass

ipopt_chars.sort(key=lambda x: x[0])
part3 = ''.join([c for _, c in ipopt_chars])
print("IP Options part:", part3)
```

И получим третью часть флага:

```
    R@bbit}
```

Собираем флаг вместе и получаем: solar{F0ll0w_th3_DN3_R@bbit}

**Solution**:
---
You need to understand the anomalies in the traffic:
1. Many DNS requests for subdomains like (s.company.sol, x.company.sol...)
2. There are packets for 10.10.10.10. without payload on TCP.window, which is much larger than usual
3. Some ICMP packets contain IP Options of type 31 with length 3 and a data byte

The first piece of the flag can be seen simply through the filter (DNS requests):

```
    solar{F0ll
```

For the second piece, you need to understand the logic of transmission. The main thing is that TCP.window is non-standard, and then you need to analyze and come to the conclusion that the data is only in TCP.window % 4 == 0, and also that the data is presented in ASCII with an offset (val >> 2). You can write a script that will help you get all this:

```
tcp_chars = []

for pkt in packets:
    if TCP in pkt and pkt[IP].dst == "10.10.10.10":
        val = pkt[TCP].window
        if val % 4 == 0:
            ch = val >> 2
            if 32 <= ch <= 126:
                tcp_chars.append((pkt[TCP].seq, chr(ch)))

tcp_chars.sort(key=lambda x: x[0])
part2 = ''.join([c for _, c in tcp_chars])
print("TCP part:", part2)
```

And we get the second part of the flag:

```
    0w_th3_DN3
```

The third piece of the flag can be obtained through filters (IPOption.type, etc.).
• IPOption.type == 31
• order by IP.ttl
or via script:

```
ipopt_chars = []

for pkt in packets:
    if IP in pkt and pkt[IP].dst == "172.16.0.1":
        for o in pkt[IP].options:
            try:
                if o.option == 31 and len(o.value) >= 1 and o.value[0] < 128:
                    ipopt_chars.append((pkt[IP].ttl, chr(o.value[0])))
            except:
                pass

ipopt_chars.sort(key=lambda x: x[0])
part3 = ''.join([c for _, c in ipopt_chars])
print("IP Options part:", part3)
```

And we get the third part flag:

```
    R@bbit}
```

We put the flag together and get: solar{F0ll0w_th3_DN3_R@bbit}
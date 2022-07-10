# devops-DZ3.6
## Домашнее задание к занятию "3.6. Компьютерные сети, лекция 1"
>1.  Работа c HTTP через телнет.
   Подключитесь утилитой телнет к сайту stackoverflow.com ```telnet stackoverflow.com 80 ```
   отправьте HTTP запрос
```
GET /questions HTTP/1.0
HOST: stackoverflow.com
[press enter]
[press enter]
```
В ответе укажите полученный HTTP код, что он означает?
### Ответ ###     
```bash
  Trying 151.101.65.69...
Connected to stackoverflow.com.
Escape character is '^]'.
GET /questions HTTP/1.0
HOST: stackoverflow.com

HTTP/1.1 301 Moved Permanently
cache-control: no-cache, no-store, must-revalidate
location: https://stackoverflow.com/questions
x-request-guid: 667ac72f-b102-4db5-b7a0-7ff9b9c30579
feature-policy: microphone 'none'; speaker 'none'
content-security-policy: upgrade-insecure-requests; frame-ancestors 'self' https://stackexchange.com
Accept-Ranges: bytes
Date: Sun, 10 Jul 2022 17:46:42 GMT
Via: 1.1 varnish
Connection: close
 ```
 Код возврата 301 Moved Permanently — запрошенный документ был окончательно перенесен на новый URI, указанный в поле Location заголовка. 
 Коды  класса 3хх сообщают клиенту, что для успешного выполнения операции необходимо сделать другой запрос, как правило, по другому URI. 
>2.Повторите задание 1 в браузере, используя консоль разработчика F12.

- откройте вкладку `Network`
- отправьте запрос http://stackoverflow.com
- найдите первый ответ HTTP сервера, откройте вкладку Headers
- укажите в ответе полученный HTTP код.
- проверьте время загрузки страницы, какой запрос обрабатывался дольше всего?
- приложите скриншот консоли браузера в ответ.

### Ответ ###     

[Скриншот](https://github.com/VovetZ/devops-DZ3.6/blob/39ef1d4ff347f355169b41ed5aed048d47431bb3/1.png)

Код 200 OK — успешный запрос. Если клиентом были запрошены какие-либо данные, то они находятся в заголовке и/или теле сообщения. 
Дольше всего обрабатывался запрос основного документа запрашиваемой страницы - длительность 1.5 с

>3. Какой IP адрес у вас в интернете?
### Ответ ###  
Мой адрес 91.188.184.23 - так показывает http://whoer.net

>4. Какому провайдеру принадлежит ваш IP адрес? Какой автономной системе AS? Воспользуйтесь утилитой `whois`
### Ответ ###     
```bash
 inetnum:        91.188.184.0 - 91.188.184.255
netname:        DigitOne-M-NET-91-188-184
descr:          DigitOne M Network
country:        RU
admin-c:        DNOC3-RIPE
tech-c:         DNOC3-RIPE
status:         ASSIGNED PA
mnt-by:         TELECALL-MNT
created:        2011-04-22T07:16:02Z
last-modified:  2020-09-03T06:49:12Z
source:         RIPE # Filtered

role:           Digit One Network Operations Center
address:        1 Veshnyakovsky pr, 1s8
address:        109456, Moscow, Russian Federation
remarks:        ------------------------------------------
remarks:        Routing and peering issues: noc@almatel.ru
remarks:        Report SPAM and abuse: abuse@almatel.ru
remarks:        Customer support: support@almatel.ru
remarks:        General information: noc@almatel.ru
remarks:        ------------------------------------------
admin-c:        AM45650-RIPE
tech-c:         NB7706-RIPE
nic-hdl:        DNOC3-RIPE
created:        2010-03-29T11:04:54Z
last-modified:  2019-06-05T10:38:17Z
source:         RIPE # Filtered
mnt-by:         MNT-DIGIT1
mnt-by:         MNT-SETEL

% Information related to '91.188.176.0/20AS8905'

route:          91.188.176.0/20
descr:          Digit One LLC
origin:         AS8905
mnt-by:         TELECALL-MNT
mnt-by:         MNT-DIGIT1
created:        2011-08-11T04:45:08Z
last-modified:  2012-11-22T09:06:23Z
source:         RIPE

```

Провайдер - Цифра1 (DigitOne M Network), AS8905
 


>5. Через какие сети проходит пакет, отправленный с вашего компьютера на адрес 8.8.8.8? Через какие AS? Воспользуйтесь утилитой `traceroute`
### Ответ ###     
```bash
  vk@vk-desktop:~$ traceroute -IAn 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  192.168.1.1 [*]  0.476 ms  0.433 ms  0.424 ms
 2  10.119.192.1 [*]  1.426 ms  1.418 ms  1.411 ms
 3  91.188.184.1 [AS8905]  1.403 ms  1.644 ms  1.635 ms
 4  72.14.203.49 [AS15169]  2.875 ms  2.871 ms  2.866 ms
 5  142.251.64.109 [AS15169]  1.612 ms  1.941 ms  1.936 ms
 6  108.170.250.66 [AS15169]  2.843 ms  2.073 ms  2.051 ms
 7  142.250.238.214 [AS15169]  19.729 ms  19.695 ms  19.673 ms
 8  142.250.235.68 [AS15169]  23.410 ms  23.403 ms  23.395 ms
 9  209.85.254.135 [AS15169]  18.895 ms  18.888 ms  18.881 ms
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  8.8.8.8 [AS15169]  16.614 ms  16.608 ms  16.601 ms
  
```
>6. Повторите задание 5 в утилите mtr. На каком участке наибольшая задержка - delay?
### Ответ ###     
```bash
  vk@vk-desktop:~$ mtr -zn -r -c 3  8.8.8.8
Start: 2022-07-10T21:42:42+0300
HOST: vk-desktop                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. AS???    192.168.1.1          0.0%     3    0.3   0.4   0.3   0.6   0.1
  2. AS???    10.119.192.1         0.0%     3    1.3   1.3   1.3   1.5   0.1
  3. AS8905   91.188.184.1         0.0%     3    3.7   2.5   1.3   3.7   1.2
  4. AS15169  72.14.203.49         0.0%     3    2.8   2.5   2.4   2.8   0.3
  5. AS15169  142.251.64.109       0.0%     3    1.8   1.7   1.5   1.8   0.2
  6. AS15169  108.170.250.66       0.0%     3    2.2   2.2   2.0   2.4   0.2
  7. AS15169  142.250.238.214      0.0%     3   19.7  19.9  19.6  20.4   0.5
  8. AS15169  142.250.235.68       0.0%     3   19.5  19.6  19.4  19.8   0.2
  9. AS15169  209.85.254.135       0.0%     3   18.8  18.9  18.8  19.0   0.1
 10. AS???    ???                 100.0     3    0.0   0.0   0.0   0.0   0.0
 11. AS???    ???                 100.0     3    0.0   0.0   0.0   0.0   0.0
 12. AS???    ???                 100.0     3    0.0   0.0   0.0   0.0   0.0
 13. AS???    ???                 100.0     3    0.0   0.0   0.0   0.0   0.0
 14. AS???    ???                 100.0     3    0.0   0.0   0.0   0.0   0.0
 15. AS???    ???                 100.0     3    0.0   0.0   0.0   0.0   0.0
 16. AS???    ???                 100.0     3    0.0   0.0   0.0   0.0   0.0
 17. AS???    ???                 100.0     3    0.0   0.0   0.0   0.0   0.0
 18. AS???    ???                 100.0     3    0.0   0.0   0.0   0.0   0.0
 19. AS15169  8.8.8.8              0.0%     3   16.7  17.6  16.6  19.5   1.7
  
```

Наибольшая задержка - участок AS15169  209.85.254.135 - AS15169  8.8.8.8        

>7. Какие DNS сервера отвечают за доменное имя dns.google? Какие A записи? воспользуйтесь утилитой `dig`
### Ответ ###     
```bash
vk@vk-desktop:~$ dig  @8.8.8.8 dns.google

; <<>> DiG 9.18.1-1ubuntu1.1-Ubuntu <<>> @8.8.8.8 dns.google
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61627
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;dns.google.			IN	A

;; ANSWER SECTION:
dns.google.		351	IN	A	8.8.8.8
dns.google.		351	IN	A	8.8.4.4

;; Query time: 19 msec
;; SERVER: 8.8.8.8#53(8.8.8.8) (UDP)
;; WHEN: Sun Jul 10 21:54:34 MSK 2022
;; MSG SIZE  rcvd: 71
```
Ответ на вопрос видим как
dns.google.		351	IN	A	8.8.8.8
dns.google.		351	IN	A	8.8.4.4

>8. Проверьте PTR записи для IP адресов из задания 7. Какое доменное имя привязано к IP? воспользуйтесь утилитой `dig`
### Ответ ###     
```bash
 vk@vk-desktop:~$ dig -x 8.8.4.4 

; <<>> DiG 9.18.1-1ubuntu1.1-Ubuntu <<>> -x 8.8.4.4
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13077
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;4.4.8.8.in-addr.arpa.		IN	PTR

;; ANSWER SECTION:
4.4.8.8.in-addr.arpa.	64259	IN	PTR	dns.google.

;; Query time: 8 msec
;; SERVER: 192.168.1.1#53(192.168.1.1) (UDP)
;; WHEN: Sun Jul 10 21:59:23 MSK 2022
;; MSG SIZE  rcvd: 73

vk@vk-desktop:~$ dig -x 8.8.8.8 

; <<>> DiG 9.18.1-1ubuntu1.1-Ubuntu <<>> -x 8.8.8.8
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17021
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;8.8.8.8.in-addr.arpa.		IN	PTR

;; ANSWER SECTION:
8.8.8.8.in-addr.arpa.	71380	IN	PTR	dns.google.

;; Query time: 4 msec
;; SERVER: 192.168.1.1#53(192.168.1.1) (UDP)
;; WHEN: Sun Jul 10 21:59:40 MSK 2022
;; MSG SIZE  rcvd: 73
   
```
Ответ PTR	dns.google


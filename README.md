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
```bash
    
```
>4. Какому провайдеру принадлежит ваш IP адрес? Какой автономной системе AS? Воспользуйтесь утилитой `whois`
### Ответ ###     
```bash
    
```
>5. Через какие сети проходит пакет, отправленный с вашего компьютера на адрес 8.8.8.8? Через какие AS? Воспользуйтесь утилитой `traceroute`
### Ответ ###     
```bash
    
```
>6. Повторите задание 5 в утилите mtr. На каком участке наибольшая задержка - delay?
### Ответ ###     
```bash
    
```
>7. Какие DNS сервера отвечают за доменное имя dns.google? Какие A записи? воспользуйтесь утилитой `dig`
### Ответ ###     
```bash
    
```
>8. Проверьте PTR записи для IP адресов из задания 7. Какое доменное имя привязано к IP? воспользуйтесь утилитой `dig`
### Ответ ###     
```bash
    
```

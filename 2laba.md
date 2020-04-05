<center>![](logo.png)</center><br>
<center><font face="Times New Roman" size="4">МИНОБРНАУКИ РОССИИ</font></center>
<center><font face="Times New Roman" size="4">Федеральное государственное бюджетное</font></center>
<center><font face="Times New Roman" size="4">образовательное учреждение высшего образования</font></center>
<center><font face="Times New Roman" size="5">**«МИРЭА – Российский технологический униврситет»**</font></center><br>
<center><font face="Times New Roman" size="4">Отчет по лабораторной работе № 2 по дисциплине:</font></center>
<center><font face="Times New Roman" size="4">«Программные средства оперативно-аналитического поиска»</font></center><br>
<center><font face="Times New Roman" size="4">Тема: поиск информации о компаниях</font></center><br><br><br><br><br><br><br>
<div style="text-align: right"><font face="Times New Roman" size="4">Выполнила:</font></div>
<div style="text-align: right"><font face="Times New Roman" size="4">Студент 4 курса</font></div>
<div style="text-align: right"><font face="Times New Roman" size="4">Специальности 10.05.05</font></div>
<div style="text-align: right"><font face="Times New Roman" size="4">Группа ББСО-01-16</font></div>
<div style="text-align: right"><font face="Times New Roman" size="4">Босачева Т.В.</font></div><br>
<div style="text-align: right"><font face="Times New Roman" size="4">Проверил:</font></div>
<div style="text-align: right"><font face="Times New Roman" size="4">Захарчук И.И.</font></div><br><br><br><br><br><br><br>
<center><font face="Times New Roman" size="4">Москва 2020</font></center><br><br><br>
<center><font face="Times New Roman" size="5">**Лабораторная работа №2**</font></center><br><br>
<font face="Times New Roman" size="4"><u>**Цель работы:**</u></font><br>
<font face="Times New Roman" size="4">Проанализировать сетевые параметры публичных DNS серверов, сделать мотивированный вывод о предпочтительных серверах</font><br><br>

<font face="Times New Roman" size="4"><u>**Исходные данные:**</u></font><br>
<font face="Times New Roman" size="3"><table>
| Наименование устройства  | Программа виртуализации   | Операционная система| 
| ------------------------ | ------------------------- | --------------------|
| Asus UX32V Notebook PC   | VMware Workstation Pro 15 |  Kali linux         |
</table></font>
<font face="Times New Roman" size="5"><u>**Используемое ПО:**</u></font><br>

<font face="Times New Roman" size="4">1. Rstudio IDE</font><br>
<font face="Times New Roman" size="4">2. Traceroute/tracert</font><br>
<font face="Times New Roman" size="4">3. Ping</font><br>
<font face="Times New Roman" size="4">4. Whois</font><br>


<font face="Times New Roman" size="5"><u>**Исследуемые провайдеры DNS**</u></font>

<font face="Times New Roman" size="4">1. Google Public DNS</font><br>
<font face="Times New Roman" size="4">2. Cloudflare DNS</font><br>
<font face="Times New Roman" size="4">3. OpenDNS</font><br>
<font face="Times New Roman" size="4">4. DNS вашего провайдера</font><br>


<font face="Times New Roman" size="5"><u>**Варианты решения задачи**</u></font>

<font face="Times New Roman" size="4">1. Использовать утилиту tracert</font><br>
<font face="Times New Roman" size="4">2. Использовать утилиту tracerout</font><br>


<font face="Times New Roman" size="5"><u>**Общий план выполнения**</u></font>

<font face="Times New Roman" size="4">1. По исследуемым серверам собрать следующие данные:</font><br>
<font face="Times New Roman" size="4">1.1.маршрут</font><br>
<font face="Times New Roman" size="4">1.2.местоположение каждого узла маршрута к DNS-серверу</font><br>
<font face="Times New Roman" size="4">1.3.организацию, владеющую каждым узлом маршрута к DNS-серверу</font><br>
<font face="Times New Roman" size="4">1.4.среднюю RTT (round trip time) к DNS-серверу</font><br>
<font face="Times New Roman" size="4">2. Выделить те узлы маршрута, которые вносят наибольшую временную задержку при передаче</font><br>
<font face="Times New Roman" size="4">3. Сравнить сетевые параметры DNS серверов</font><br>

<font face="Times New Roman" size="5"><u>**Процесс выполнения работы**</u></font>

<font face="Times New Roman" size="5"><u>**1.Google Public DNS**</u></font><br>

```{r cache=TRUE}
system("tracert 8.8.8.8", intern = TRUE)
```
<font face="Times New Roman" size="4"><table>
|  №  | Первый ping | Второй ping | Третий ping |              Узел                       |     Месторасположение      |Организация  |Средняя RTT|Вносит наибольшую временную задержку при передаче|
|:---:|:-----------:|:-----------:|:-----------:|:---------------------------------------:|:--------------------------:|:-----------:|:---------:|:-----------------------------------------------:|
|  1  |    5ms      |    2ms      |    2ms      |          192.168.0.1                    |      Россия, Москва        |   Роутер    |     3ms   |                                                 |
|  2  |    5ms      |    2ms      |    2ms      |lo.bras3.podolsknet.local [10.254.254.13]|     Лос-Анжелес, США       |    IANA     |     3ms   |                                                 |
|  3  |    4ms      |    4ms      |    7ms      | host-0-129.podolsknet.ru [109.94.0.129] |     Россия, Подольск       |Кварц-телеком|     5ms   |                                                 |
|  4  |    5ms      |    3ms      |    3ms      | msk.piter-ix.google.com [31.44.187.11]  |   Германия, Франкфурт      | Google LLC  |    3,7ms  |                                                 |
|  5  |    28ms     |    3ms      |    3ms      |          108.170.250.51                 |США, Калифорния, Маунтин Вью| Google LLC  |    11,4ms |                                                 |
|  6  |    19ms     |    19ms     |    19ms     |          216.239.51.32                  |США, Калифорния, Маунтин Вью| Google LLC  |     19ms  |                                                 |
|  7  |    29ms     |    21ms     |    21ms     |         108.170.232.251                 |США, Калифорния, Маунтин Вью| Google LLC  |    23,7ms |                            Да                   |
|  8  |    25ms     |    22ms     |    23ms     |         216.239.48.97                   |США, Калифорния, Маунтин Вью| Google LLC  |    23,4ms |                            Дa                   |
|  9  |     *       |     *       |     *       |        Request timed out.               |                            |             |           |                                                 |
|  10 |     *       |     *       |     *       |        Request timed out.               |                            |             |           |                                                 |
|  11 |     *       |     *       |     *       |        Request timed out.               |                            |             |           |                                                 |
|  12 |     *       |     *       |     *       |        Request timed out.               |                            |             |           |                                                 |
|  13 |     *       |     *       |     *       |        Request timed out.               |                            |             |           |                                                 |
|  14 |     *       |     *       |     *       |        Request timed out.               |                            |             |           |                                                 |
|  15 |     *       |     *       |     *       |        Request timed out.               |                            |             |           |                                                 |
|  16 |     *       |     *       |     *       |        Request timed out.               |                            |             |           |                                                 |
|  17 |     *       |     *       |     *       |        Request timed out.               |                            |             |           |                                                 |
|  18 |    22ms     |    21ms     |    23ms     |       dns.google [8.8.8.8]              |       США, Нью-Йорк        | Google LLC  |    22ms   |                            Да                   |   
</table></font>


<font face="Times New Roman" size="5"><u>**2.Cloudflare DNS**</u></font><br>

```{r cache=TRUE}
system("tracert 1.1.1.1", intern = TRUE)
```
<font face="Times New Roman" size="4"><table>
|  №  | Первый ping | Второй ping | Третий ping |                   Узел                           |Месторасположение | Организация   |Средняя RTT|Вносит наибольшую временную задержку при передаче|
|:---:|:-----------:|:-----------:|:-----------:|:------------------------------------------------:|:----------------:|:-------------:|:---------:|:-----------------------------------------------:|
|  1  |    4ms      |    2ms      |    2ms      |                192.168.0.1                       |  Россия, Москва  |     Роутер    |   2,7ms   |                                                 |
|  2  |    5ms      |    5ms      |    6ms      |   lo.bras3.podolsknet.local [10.254.254.13]      | Лос-Анжелес, США |      IANA     |   5,4ms   |                                                 |
|  3  |    3ms      |    8ms      |    2ms      |     host-0-129.podolsknet.ru [109.94.0.129]      | Россия, Подольск | Кварц-телеком |   4,4ms   |                                                 |
|  4  |    5ms      |    3ms      |    3ms      |msk-m9-b1-ae4-vlan1080.fiord.net [62.140.243.34]  |  Россия, Москва  |    FiordPtP   |   3,7ms   |                                                 |
|  5  |    5ms      |    5ms      |    4ms      |msk-m9-b3-ae10-vlan1299.fiord.net [62.140.243.186]|  Россия, Москва  |    FiordPtP   |   4,7ms   |                                                 |
|  6  |    15ms     |    6ms      |    8ms      |  cloudflare-peering.fiord.net [80.77.167.7]      |  Россия, Москва  |    FiordNet   |   9,7ms   |                     Да                          |                      
|  7  |    4ms      |    3ms      |    3ms      |         one.one.one.one [1.1.1.1]                |Брисбен, Австралия|Cloudflare DNS |   3,4ms   |                                                 |
</table></font>


<font face="Times New Roman" size="5"><u>**3.OpenDNS**</u></font><br>

```{r cache=TRUE}
system("tracert 208.67.220.220", intern = TRUE)
```
<font face="Times New Roman" size="4"><table>
|  №  | Первый ping | Второй ping | Третий ping |                   Узел                         |   Месторасположение  |Организация  |Средняя RTT|Вносит наибольшую временную задержку при передаче|
|:---:|:-----------:|:-----------:|:-----------:|:----------------------------------------------:|:--------------------:|:-----------:|:---------:|:-----------------------------------------------:|
|  1  |   128ms     |    4ms      |    2ms      |                192.168.0.1                     |     Россия, Москва   |   Роутер    |    45ms   |               Да                                |      
|  2  |    5ms      |    3ms      |    3ms      |   lo.bras3.podolsknet.local [10.254.254.13]    |    США, Лос-АНжелес  |     IANA    |   3,7ms   |                                                 | 
|  3  |    5ms      |    3ms      |    2ms      |quartz-bras3.m9-gw.skynet-msk.ru [91.227.188.4] |     Россия, Москва   |LLC "Skynet" |   3,4ms   |                                                 |
|  4  |   23ms      |    8ms      |    6ms      |ae12-488.RT1.M9.MSK.RU.retn.net [87.245.255.177]|     Россия, Москва   |     ReTN    |   12,4ms  |                                                 |
|  5  |   49ms      |   49ms      |   48ms      |ae10-11.RT.THV.PAR.FR.retn.net [87.245.232.252] |Великобритания, Лондон|     RETN    |   48,7ms  |               Да                                |
|  6  |   49ms      |   49ms      |   49ms      |  opendns.par.franceix.net [37.49.236.210]      |     Франция, Париж   |  FranceIX   |    49ms   |               Да                                | 
|  7  |   50ms      |   48ms      |   50ms      |   resolver2.opendns.com [208.67.220.220]       |   США, Сан-Франциско |Cisco OpenDNS|   49,4ms  |               Да                                |
</table></font>


<font face="Times New Roman" size="5"><u>**4.Кварц Телеком DNS**</u></font><br>

```{r cache=TRUE}
system("tracert 109.94.0.3", intern = TRUE)
```
<font face="Times New Roman" size="4"><table>
|  №  | Первый ping | Второй ping | Третий ping |                  Узел                   |Меторасположение|   Организация   |Средняя RTT|Вносит наибольшую временную задержку при передаче|
|:---:|:-----------:|:-----------:|:-----------:|:---------------------------------------:|:--------------:|:---------------:|:---------:|:-----------------------------------------------:|
|  1  |    4ms      |    2ms      |    2ms      |             192.168.0.1                 |Россия, Москва  |      Роутер     |    2,7ms  |                                                 |
|  2  |     *       |    7ms      |    4ms      |lo.bras3.podolsknet.local [10.254.254.13]|США, Лос-АНжелес|       IANA      |    5,5ms  |               Да                                | 
|  3  |    8ms      |    6ms      |    3ms      | bras3.gw.podolsknet.ru [109.94.0.93]    |Россия, Подольск|Кварц Телеком LLC|    5,7ms  |               Да                                |
|  4  |    3ms      |    5ms      |    4ms      |     ns1.podolsknet.ru [109.94.0.3]      |Россия, Подольск|Кварц Телеком LLC|     4ms   |                                                 |
</table></font>

 
<font face="Times New Roman" size="5"><u>**Сравнительная диаграмма**</u></font>


<font face="Times New Roman" size="5"><u>Используемые цвета:</u></font>

<font face="Times New Roman" size="4">1. Google DNS - красный</font><br>
<font face="Times New Roman" size="4">2. Cloudflare DNS - зеленый</font><br>
<font face="Times New Roman" size="4">3. OpenDNS - желтый </font><br>
<font face="Times New Roman" size="4">4. Кварц-телеком - голубой</font><br>

```{r, echo=FALSE}
x <- c(0,2,4,6,8,10,12,14,16,18,20,22,24,26,28,30,32,34,36,38,40,42,44,46,48,50,52)
y <- c(0,0.5,1,1.5,2,2.5,3,3.5,4,4.5,5,5.5,6,6.5,7,7.5,8,8.5,9,9.5,10,10.5,11,11.5,12,12.5,13)
x_1 <- c(3,3,5,3.7,11.4,19,23.7,23.4,22)
y_1 <- c(1,2,3,4,5,6,7,8,9)
x_2 <- c(2.7,5.4,4.4,3.7,4.7,9.7,3.4)
y_2 <- c(1,2,3,4,5,6,7)
x_3 <- c(45,3.7,3.4,12.4,48.7,49,49.4)
y_3 <- c(1,2,3,4,5,6,7)
x_4 <- c(2.7,5.5,5.7,4)
y_4 <- c(1,2,3,4)

plot(y,x,main = "Сравнительная диаграмма RTT к серверам", xlab = "Шаг", ylab = "RTT",type = "n")
points(y_1,x_1, col = "red")
lines(y_1,x_1, col = "red")
points(y_2,x_2, col = "green")
lines(y_2,x_2, col = "green")
points(y_3,x_3, col = "yellow")
lines(y_3,x_3, col = "yellow")
points(y_4,x_4, col = "blue")
lines(y_4,x_4, col = "blue")
```


<font face="Times New Roman" size="5"><u>**Оценка результатов:**</u></font><br>
<font face="Times New Roman" size="4">Основываясь на полученных данных, можно сделать вывод, что меньше всего времени потребовалось для обращения к Кварц-телеком, а больше всего - к OpenDNS.</font><br>


<font face="Times New Roman" size="5"><u>**Вывод:**</u></font><br>
<font face="Times New Roman" size="4">Выполняя данную лабораторную работу я проанализировала сетевые параметры публичных DNS серверов и сделала мотивированный вывод о предпочтительных серверах.</font><br>























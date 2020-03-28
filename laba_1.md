<div align="center">
  <br>
  <img src="https://i.ibb.co/DkYw4wF/logo.png" alt="logo" border="0"><br><br>
  МИНОБРНАУКИ РОССИИ<br>
  Федеральное государственное бюджетное<br>
  образовательное учреждение высшего образования
  
#### **«МИРЭА – Российский технологический униврситет»**
  
  Лабораторная работа по дисциплине:<br>
  «Программные средства оперативно-аналитического поиска»
</div>
<br><br><br><br><br>
<div align="right">
  <br>
  Выполнила:<br>
  Студент 4 курса<br>
  Специальности 10.05.05<br>
  Группа ББСО-01-16<br>
  Босачева Т.В.<br>
  
  Проверил:<br>
  Захарчук И.И.<br>
</div>
<br><br><br><br><br><br><br>

<p align="center">
  Москва 2020
</p>
<br><br><br>

<div align="center">

#### **Лабораторная работа № 1**

</div>

<p>

#### **Цель работы**

Используя специализированные утилиты и сайты произвести сбор информации по каждой жертве (компании)
</p>

<p>

#### **Исходные данные**


| Наименование устройства  | Программа виртуализации   | Операционная система  |
| ------------------------ | ------------------------- | --------------------- |
| Asus UX32V Notebook PC   | VMware Workstation Pro 15 |      Kali linux       |

</p>

<p>

#### **Наименования компаний**

1. [Cisco Systems Inc](www.cisco.com)<br>
2. [Chevron Corporation](www.chevron.com)<br>
3. [UnitedHealth Group Incorporated](unitedhealthgroup.com)<br>
4. [Pfizer Inc.](www.pfizer.com)<br>
5. [Home Depot Inc.](corporate.homedepot.com)<br>
</p>

<p>

#### **Используемые ресурсы и утилиты**

1. Утилиты nslookup, whois, nmap<br>
2. Сайты:
    * [Shodan](shodan.io)
    * [Censys](censys.io)
    * [Maxmind](maxmind.com)
    * [2ip](2ip.ru)
    * [Wappalyzer](wappalayzer.com)
</p>


#### **Процесс выполнения работы**

<p>

* **Cisco Systems Inc.**

|Признак       |Значение                               |
|--------------|---------------------------------------|
|Компания      |Cisco Systems Inc / 72.163.4.185       |
|Сайт          |https://www.cisco.com/                 |
|Ipnetblock    |72.163.0.0 – 72.163.255.255            |
|Местоположение|US, CA, San Jose, 170 West Tasman Drive|
|Телефон       |+1-408-526-8888                        |
|Email         |arin-tech@cisco.com                    |
|Хостинг       |Cisco Systems                          |
|Порты         |80, 443                                |
|Веб-технологии|AngularJS, Facebook, Dojo, Linkedin,   |
|              |Java Servlet, YouTube, CoinHive,       |
|              |Google Plus, reCAPTCHA, Twitter, PHP,  |
|              |Slick, Tealium                         |
</p>


<p>

* **Chevron Corporation**

|Признак       |Значение                                    |
|--------------|--------------------------------------------|
|Компания      |Chevron Corporation / 146.23.28.130         |
|Сайт          |https://www.chevron.com/                    |
|Ipnetblock    |146.22.0.0 - 146.46.255.255                 |
|Местоположение|US, CA, San Ramon, 6001 Bollinger Canyon Rd.|
|Телефон       |+1-925-842-1000, +1-207-719-3032            |
|Email         |steve.hodgkiss@chevron.com                  |
|Хостинг       |Chevron                                     |
|Порты         |80, 443                                     |
|Веб-технологии|Stackla, Akamai, Marketo, Modernixr,        |
|              |Bootstrap, Sizmek, amCharts, Windows Server,|
|              |Google Tag Manager                          |
</p>

<p>

* **UnitedHealth Group Incorporated**

|Признак       |Значение                                         |
|--------------|-------------------------------------------------|
|Компания      |UnitedHealth Group Incorporated / 149.111.148.162|
|Сайт          |https://www.unitedhealthgroup.com/               |
|Ipnetblock    |149.111.0.0 - 149.111.255.255                    |
|Местоположение|US, MN, Plymouth, 6150 Trenton Lane              |
|Телефон       |+1-763-744-1588                                  |
|Email         |inet_ops@uhc.com                                 |
|Хостинг       |UnitedHealth Group Incorporated                  |
|Порты         |80, 443                                          |
|Веб-технологии|Java, Google Analytics, jQuery, Facebook,        |
|              |Adobe DTM, Apache, Bootstrap, Handlebars,        |
|              |reCAPTCHA                                        |

</p>

<p>

* **Pfizer Inc.**

|Признак       |Значение                        |
|--------------|--------------------------------|
|Компания      |Pfizer Inc. / 104.18.12.178     |
|Сайт          |https://www.pfizer.com/         |
|Ipnetblock    |104.16.0.0 - 104.31.255.255     |
|Местоположение|US, NY, New York, 235 E. 42nd.St|
|Телефон       |+1-212-573-2273                 |
|Email         |domainregistrations@pfizer.com  |
|Хостинг       |Cloudflare                      |
|Порты         |80, 443, 2087                   |
|Веб-технологии|Twitter, Apache, Drupal, PHP,   |
|              |Varnish, VideoJS, Hammer.js,    |
|              |New Relic, Polyfill, AddThis,   |
|              |Percona, MySQL                  |

</p>

<p>

* **Home Depot Inc.**

|Признак       |Значение                                     |
|--------------|---------------------------------------------|
|Компания      |Home Depot Inc. / 23.185.0.3                 |
|Сайт          |https://corporate.homedepot.com/             |
|Ipnetblock    |23.185.0.0 - 23.185.0.255                    |
|Местоположение|US, CA, San Francisco, 717 California ST FL 3|
|Телефон       |+1-415-800-1969                              |
|Email         |david@davidstrauss.net                       |
|Хостинг       |Pantheon                                     |
|Порты         |80, 443                                      |
|Веб-технологии|Nginx, Varnish, PHP, Pantheon, Lodash, Slick,|
|              |Drupal, MariaDB, AddThis, HeadJS, HTTP/2,    | 
|              |Modernizr                                    |
</p>

#### **Вывод**

<p>
Выполняя данную лабораторную работу, я повторила основы сбора информации о жертве, используя различные утилиты и сайты.
</p>


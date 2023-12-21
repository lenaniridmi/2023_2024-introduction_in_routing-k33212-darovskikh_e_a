University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)  
Year: 2023/2024  
Group: K33212  
Author: Darovskikh Elena Alekseevna  
Lab: Lab4  
Date of create: 21.12.2023  
Date of finished: 22.12.2023  

## Лабораторная работ №4 "Эмуляция распределенной корпоративной сети связи, настройка iBGP, организация L3VPN, VPLS"  

## Описание  

Компания "RogaIKopita Games" выпустила игру "Allmoney Impact", нагрузка на арендные сервера возрасли и вам поставлена задача стать LIR и организовать свою AS чтобы перенести все сервера игры на свою инфраструктуру. После организации вашей AS коллеги из отдела DEVOPS попросили вас сделать L3VPN между 3 офисами для служебных нужд. (Рисунок 1) Данный L3VPN проработал пару недель и коллеги из отдела DEVOPS попросили вас сделать VPLS для служебных нужд.

## Цель работы 

Изучить протоколы BGP, MPLS и правила организации L3VPN и VPLS.

## Ход работы

Первая часть:

* Настроить iBGP RR Cluster.  
* Настроить VRF на 3 роутерах.  
* Настроить RD и RT на 3 роутерах.  
* Настроить IP адреса в VRF.  
* Проверить связность между VRF  

Вторая часть:

* Разобрать VRF на 3 роутерах (или отвязать их от интерфейсов).  
* Настроить VPLS на 3 роутерах.  
* Настроить IP адресацию на PC1,2,3 в одной сети.  
* Проверить связность.  


### Сеть  

Код по построению сети представлен в директории проекта (./lab4).

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/66fce58e-5cf0-4af1-80eb-264fe922c42c)

Для удобства определим подсети связности уустройств. Используем команду ```sudo clab graph -t my_lab4_iBGP.yaml``` и какой нибудь графический редактор.

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/9b3a3caa-b689-457c-96e9-c03edcdfcef5)

## Первая чать ЛР

Соответственно настраиваем связность интерфейсов

* NY

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/fbcbe1e8-4562-45f6-9b2f-29daf456ca60)

* LND

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/dbe43e95-eec9-4c44-bf0d-d8610132a18e)

* LBN

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/9a06f5c6-dff8-4cb0-aa27-48c999e06ffe)

* SVL

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/c1ce49d6-a313-4025-9f35-575177ec27c4)

* HKI

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/eb2e86ea-f556-4a44-b869-d21d40fa58d3)

* SPB

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/cc0682fe-a653-474b-a602-cb7634bf7740)

### VRF
Для того чтобы наша таблица маршрутизации VRF_DEVOPS не попадала под действие протокола OSPF, сначала настраиваем VRF на устройствах, связанных с PC.

* NY

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/3e76d8a0-1885-41fb-8288-0997e8a653cf)

* SVL

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/0c59713b-9920-4cc4-b0a1-1612bedb4d67)

* SPB

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/717f04ef-dad3-4eb6-a4cd-fccab3148ae1)

### OSPF и MPLS

Далее настраиваем OSPF; при определении network area=backbone и заданных интерфейсвх автоматически появится связность для сетевого устройства

* LND (Пример, аналогично для остальных роутеров)

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/dd57c26a-4ca3-45b9-8a5f-234d1d72ddd4)

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/3e632d4c-18c8-435f-9d7f-12f016298cc6)

После настройки OSPF мы сможем увидеть расширенную таблицу маршрутизации, соответственно без VRF_DEVOPS

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/a4dfc3bb-2582-44f8-b215-a9f165b9b679)


Для настройки MPLS у каждого роутера в настройках LDP прописываем его transport address

* LND (Пример, для остальных аналогично их данным)

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/d6d31781-acac-4084-a420-b07dba7443e0)

После чего задаем соседей, связанных и исходным роутером сетевыми устройствами.

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/d96f4bde-eaeb-48da-890f-4a2bc29c7518)

Как только закончим настраивать MPLS на связанных устройствах, в разделе LDP Neighbor у каждого из них появятся соответственные соседи

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/36f79c8d-1967-4e59-9130-4e7400bd1659)

### IBGP

Протокол BGP прописывается к ближайшим интерфейсам узла. При настройке указываем нужные нам протоколы.

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/db94034a-f514-4bfb-8d9e-b999865b4e97)

На примере (NY <---> LND)

* LND

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/0c5aef6f-f24f-4806-91d8-a0fdbf7d8bdf)

* NY

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/98929295-7a3e-47fe-8cb3-67cabdc2478c)

После данных настроек мы увидим значение установленного соединения на каждом из устройств.

* LND

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/b8471e17-37df-4b79-a90b-ca906bb34f7e)

* NY

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/90482df4-378f-4d91-9135-0af8067785d3)

Такую же настройку делаем для остальных роутеров.

Также, на устройствах, связанных с PC настраиваем VRF для iBGP

* NY (пример, также для SPB, SVL)

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/c666e54c-370c-45ec-a450-7b2bc040ba6c)

После этого у нас автоматически появятся vrf в разделе bgp-vpn4 routes

* NY
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/1ec4251d-dd9c-4a97-87b4-8d374718e7aa)

Соответственно в таблице маршрутизации VRF_DEVOPS

* NY

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/1947c976-a3f8-4a85-a031-c39824b985c4)

* SPB

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/2bb9d23e-779f-47a8-9dce-57e202a1c95e)

* SVL

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/1f5df0e0-e10a-46e1-832b-5fbb4501d475)


### Проверка

* PC2 -> PC3; PC2 -> PC1  

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/33bd9419-a9b6-4f45-a53e-efe3f1d1adda)


* PC1 -> PC3; PC1 -> PC2

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/6d8d36e8-5301-409b-a919-1fbd601888a0)

* PC3 -> PC2; PC3 -> PC1

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/9a04980e-2d37-4abe-811f-c896b84c4f88)

## Вторая часть ЛР

### VPLS

### Проверка


## Вывод

В ходе выполнения данной лабораторной работы мы познакомились на практике с протоколами BGP, MPLS и правилами организации L3VPN и VPLS.

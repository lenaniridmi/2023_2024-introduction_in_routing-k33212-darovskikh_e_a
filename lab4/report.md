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

### IBGP

### OSPF и MPLS

### VRF

### Проверка

## Вторая часть ЛР

### VPLS

### Проверка


## <a name="section6">Вывод</a>

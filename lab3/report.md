University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)  
Year: 2023/2024  
Group: K33212  
Author: Darovskikh Elena Alekseevna  
Lab: Lab3  
Date of create: 20.12.2023  
Date of finished: 21.12.2023

## Лабораторная работ №3 "Эмуляция распределенной корпоративной сети связи, настройка OSPF и MPLS, организация первого EoMPLS"

## Описание 

Наша компания "RogaIKopita Games" с прошлой лабораторной работы выросла до серьезного игрового концерна, ещё немного и они выпустят свой ответ Genshin Impact - Allmoney Impact. И вот для этой задачи они купили небольшую, но очень старую студию "Old Games" из Нью Йорка, при поглощении выяснилось что у этой студии много наработок в области компьютерной графики и совет директоров "RogaIKopita Games" решил взять эти наработки на вооружение. К сожалению исходники лежат на сервере "SGI Prism", в Нью-Йоркском офисе никто им пользоваться не умеет, а из-за короновируса сотрудники офиса из Санкт-Петерубурга не могут добраться в Нью-Йорк, чтобы забрать данные из "SGI Prism". Ваша задача подключить Нью-Йоркский офис к общей IP/MPLS сети и организовать EoMPLS между "SGI Prism" и компьютером инженеров в Санк-Петербурге.

## Цель работы  

Изучить протоколы OSPF и MPLS, механизмы организации EoMPLS.

## Ход работы  

* Помимо этого вам необходимо настроить IP адреса на интерфейсах.  
* Настроить OSPF и MPLS.  
* Настроить EoMPLS.  
* Назначить адресацию на контейнеры, связанные между собой EoMPLS.  

### Сеть  

Для начала запустим нашу сеть (код .yaml прикреплен в директории ./lab3) и определим подсети на "бумаге" для удобства.

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/3c49bca5-e02c-45a3-8b0a-6f80d4383c0a)

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/1e12fa12-6ce5-40fc-aed8-73b4d7915cca)

### SGI_Prism и Router NYC  
MPLS - технология коммутации пакетов, которая позволяет маршрутизаторам принимать решения на основе меток (labels). Протокол LDP нужен для обмена информацией о метках с соседними маршрутизаторами.

Для установки MPLS-связей создаем интерфейсы Loopback (Lo) и bridge_EoMPLS для установки уникальных ip устройствам сети и для транспорта Ethernet-трафика через MPLS-сеть соответственно.

* Router NYC ```telnet 172.31.31.9```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/cb8f62aa-e37d-45e7-9884-af9fda1dadb6)
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/2bf03f7b-ad1d-4c62-aeb6-b876e72da981)


* SGI_Prism ```telnet 172.31.31.2```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/076d0971-0bf0-4646-a6e8-43df490f2186)


### PC1 и Router SPB  

* Router SPB ```telnet 172.31.31.8```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/de9ec162-084c-41a4-bfe9-c0385c06c7f6)
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/75c5a98e-f335-4b36-9834-9e75c263928f)
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/6ca14995-deb2-4ab8-8ca1-e2910c281618)

* PC1 ```172.31.31.6```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/3494167d-4145-4bea-8e4e-c366c3e6add2)


### Router MSK

* Router MSK ```telnet 172.31.31.3```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/318230a9-8fc2-4727-92e0-29e93b60e8bc)

### Router HKI

* Router HKI ```telnet 172.31.31.7```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/cdc47b72-33b4-4387-b902-82d0afa35ebc)

### Router LND

* Router LND ```telnet 172.31.31.5```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/c82da598-68d0-4274-ae3a-824e29136b4f)

### Router LBN

* Router LBN ```telnet 172.31.31.4```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/ccc7b6d0-d2c7-409f-851a-cd51429e4108)

### Проверка

* SGI_Prism -> PC1

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/c1f75c1f-0374-493f-9d81-a06adb16a40a)

* PC1 -> SGI_Prism

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/af631e8a-05c7-4e5b-888d-4bb7ba526e17)

* R01_SPB -> R01_NYC

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/5fd676e2-96fb-42f7-b7a0-d04a0560d687)

* MPLS Forwarding Table на роутере SPB

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/312cac5c-3cfb-464b-88d9-0395b932353f)

* IP routes на роутере SPB

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/c71b1b8f-8acc-497b-84ab-7852c74735f5)


### Вывод
В ходе выполнения данной лабораторной работы мы настроили IP адреса на интерфейсах,настроили OSPF и MPLS, а также EoMPLS. Назначили адресацию на контейнеры, связанные между собой EoMPLS.

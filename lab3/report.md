University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)  
Year: 2023/2024  
Group: K33212  
Author: Darovskikh Elena Alekseevna  
Lab: Lab2  
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

### PC1 и Router SPB  
MPLS - технология коммутации пакетов, которая позволяет маршрутизаторам принимать решения на основе меток (labels). Протокол LDP нужен для обмена информацией о метках с соседними маршрутизаторами.

Для установки MPLS-связей создаем интерфейсы Loopback (Lo) и bridge_EoMPLS для установки уникальных ip устройствам сети и для транспорта Ethernet-трафика через MPLS-сеть соответственно.

* Router SPB ```telnet 172.31.31.8```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/d965bcea-6b79-4928-a3ce-0d6dfff6b939)
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/6ca14995-deb2-4ab8-8ca1-e2910c281618)

* PC1 ```172.31.31.6```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/3494167d-4145-4bea-8e4e-c366c3e6add2)

### SGI_Prism и Router NYC  

* Router NYC ```telnet 172.31.31.9```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/cb8f62aa-e37d-45e7-9884-af9fda1dadb6)
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/f0fc8541-5b6b-426f-8d5e-d61cacd93825)

* SGI_Prism ```telnet 172.31.31.2```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/45d62953-28dc-46c4-bde9-3bbc9c3b720b)

### Router MSK

* Router MSK ```telnet 172.31.31.3```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/9fd92995-c54c-4c65-994c-a4d683222d53)

### Router HKI

* Router HKI ```telnet 172.31.31.7```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/79e87fcf-9135-4974-b185-c1df962172d9)

### Router LND

* Router LND ```telnet 172.31.31.5```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/c82da598-68d0-4274-ae3a-824e29136b4f)

### Router LBN

* Router LBN ```telnet 172.31.31.4```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/ccc7b6d0-d2c7-409f-851a-cd51429e4108)

### Проверка

### Вывод


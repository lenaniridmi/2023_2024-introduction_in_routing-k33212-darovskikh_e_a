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

* Router SPB ```telnet 172.31.31.8```

* PC1 ```172.31.31.6```

### SGI_Prism и Router NYC  

* Router NYC ```telnet 172.31.31.9```

* SGI_Prism ```telnet 172.31.31.2```

### Router HKI

* Router HKI ```telnet 172.31.31.7```


### Router MSK

* Router MSK ```telnet 172.31.31.3```

### Router LBN

* Router LBN ```telnet 172.31.31.4```

### Router LND

* Router LND ```telnet 172.31.31.5```

### Проверка

### Вывод


University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)  
Year: 2023/2024  
Group: K33212  
Author: Darovskikh Elena Alekseevna  
Lab: Lab2  
Date of create: 19.12.2023  
Date of finished: 20.12.2023

## Лабораторная работа №2 "Эмуляция распределенной корпоративной сети связи, настройка статической маршрутизации между филиалами"

## Описание 

В данной лабораторной работе вы первый раз познакомитесь с компанией "RogaIKopita Games" LLC которая занимается разработкой мобильных игр с офисами в Москве, Франкфурте и Берлине. Для обеспечения работы своих офисов "RogaIKopita Games" вам как сетевому инженеру необходимо установить 3 роутера, назначить на них IP адресацию и поднять статическую маршрутизацию. В результате работы сотрудник из Москвы должен иметь возможность обмениваться данными с сотрудником из Франкфурта или Берлина и наоборот.

## Цель работы  

Ознакомиться с принципами планирования IP адресов, настройке статической маршрутизации и сетевыми функциями устройств.

## Ход работы  

### Сеть  

Необходимо сделать сеть связи в трех геораспределенных офисах "RogaIKopita Games" в ContainerLab. 

Код файла .yaml представлен в директории проекта ./lab2

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/c553167a-3fc3-4668-9297-f71596a41347)

Для начала нужно определить связность нашей сети, для этого воспользуемся командой ```sudo clab graph -t my_lab2_static.yaml``` и каким нибудь графическим редактором для удобства построения сети.

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/39b540c5-2db4-4729-b366-fe46fe0df324)


### Настройка роутера MSK и Компьютера Msk (PC1)

* Роутер Msk ```telnet 172.22.100.5```

 ![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/74bea150-d98f-47fc-8f67-6e9054260e0a)  
 ![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/ee05bfe4-acfc-49df-ab91-9c30e2ce3759)

* Компьютер Msk (PC1) ```telnet 172.22.100.2```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/2bbc9953-81f2-4337-a891-842a8ad04ae4)

 ### Настройка роутера FRT и Компьютера FRT (PC2)

* Роутер Frt ```telnet 172.22.100.7```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/ba3d8a31-405a-402a-9805-45174a375a1f)

* Компьютер Frt (PC2) ```telnet 172.22.100.4```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/7ef5d1a1-7e7e-4543-aa68-87dc335212a7)

 ### Настройка роутера BRL и Компьютера BRL (PC3)

* Роутер Brl ```telnet 172.22.100.3```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/7a8006cf-c79c-4cda-a23e-d05228f7c659) 

* Компьютер Brl (PC3) ```telnet 172.22.100.6```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/9acca54d-358b-4ac7-9fee-12bab2914e06)

## Проверка

* От PC.BRL к PC.MSK  
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/c041252f-5cf8-4367-a61a-86d114c23a72)

* От PC.BRL к PC.FRT  
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/a9056ea4-8464-4011-9861-8df3ff2f20ca)

* От PC.FRT к PC.MSK  
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/2d7f771e-3259-4c57-8f45-2e19955d377d)

* От PC.FRT к PC.BRL    
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/470a7473-5af7-46dc-9cd3-96720d57f991)

* От PC.MSK к PC.BRL  
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/dea72d08-a745-45fa-8bf1-18cf22404b33)

* От PC.MSK к PC.FRT  
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/3c9b90a1-2fb5-49d4-8a31-a006d373972a)

## Вывод

University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)  
Year: 2023/2024  
Group: K33212  
Author: Darovskikh Elena Alekseevna  
Lab: Lab1  
Date of create: 01.10.2023  
Date of finished: 19.12.2023


## Лабораторная работ №1 "Установка ContainerLab и развертывание тестовой сети связи"

## Описание  
В данной лабораторной работе вы познакомитесь с инструментом ContainerLab, развернете тестовую сеть связи, настроите оборудование на базе Linux и RouterOS.  

## Цель работы  
Ознакомиться с инструментом ContainerLab и методами работы с ним, изучить работу VLAN, IP адресации и т.д.

## Ход работы  

### Сеть  

В начале выполнения работы была установлена утилита make, сам Containerlab с помощью команды ```bash -c "$(curl -sL https://get.containerlab.dev)"``` и репозиторий hellt/vrnetlab, после уже была развёрнута сетевая лаборатория на базе контейнеров с помощью команды ```sudo clab deploy -t my_lab1_vlan.yaml``` (файл .yaml в директории проекта ./lab1). 

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/3d59a576-38d8-4a37-94e9-25d5fba3d8dc)

С помощью команды ```sudo clab graph -t my_lab1_vlan.yaml```

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/e5d24632-0653-4fcd-96f5-ac7bf80dde61)

### Настройка роутера R01  
```telnet 192.168.50.7```  

Dhcp сервера для 2 компьютеров будут находиться на главном роутере. 
В containerlab ether1 всегда занят VPN Address 172.31.255.30, потому что это адрес виртуальной сети, которая используется для подключения контейнеров, поэтому при настройке интерфейсов всегда считаем +1 к нужному порту

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/6fed2703-dc22-43d0-a4ae-9700630df02a)

### Настройка SW01.L3.01  
```telnet 192.168.50.6``` 

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/70e68d4a-bc47-4cda-86b6-69df8d842032)

### Настройка SW02.L3.01  
```telnet 192.168.50.5```  

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/91096915-7d09-48a5-98c8-fe90e48bfea9)  
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/8ce7c34f-c445-4b54-81c6-026be6ca56b9)  



### Настройка SW02.L3.02  
```telnet 192.168.50.4```  

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/7a2bc4ca-938f-4ff1-ba4f-6f61ce91fb65)  
![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/d63e09c5-497b-41f7-b840-6b2404b8f29b)  





## Проверка  

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/a1daa817-ed41-460f-9dcf-6cf881fb4ff9)

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/4afcd7a9-eb3c-4314-a185-4ed631859a87)

![image](https://github.com/lenaniridmi/2023_2024-introduction_in_routing-k33212-darovskikh_e_a/assets/90695447/93782815-c832-4e82-b2fd-5e27eece335a)


## Вывод

В ходе выполнения данной лабораторной работы мы ознакомились с инструментом ContainerLab, была развернута тестовая сеть связи, а также настроено оборудование на базе Linux и RouterOS.


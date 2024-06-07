# Chrony Time Linux
_________________
Настраиваем сервер времени с параметрами необходимыми в задании:  
```
nano /etc/chrony.conf

server 127.0.0.1 iburst prefer
hwtimestamp *
local stratum 5
allow 0/0
```

Перезагружаем машину  
Проверяем:  
```
chronyc sources
chronyc tracking | grep Stratum
timedatectl
```

Настройка клиента
```
nano /etc/chrony.conf
server адрес сервера (10.0.0.1) iburst prefer
```

```
systemctl enable --now chronyd 
```
Перезагружаем машину 
__________________


**2. Настройте синхронизацию времени между сетевыми устройствами по протоколу NTP**

**a. В качестве сервера должен выступать роутер HQ-R со стратумом 5**
**b. Используйте Loopback интерфейс на HQ-R, как источник сервера времени**
**c. Все остальные устройства и сервера должны синхронизировать свое время с роутером HQ-R**
**d. Все устройства и сервера настроены на московский часовой пояс (UTC +3)**

## **HQ-R**  
Настраиваем сервер времени с параметрами необходимыми в задании:  
```
nano /etc/chrony.conf
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/88686ceb-da29-4e4e-83bb-24fcfa1e206b)  
Перезагружаем машину  
Проверяем:  
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/b95120d5-61b4-4832-a057-746bba721b01)  
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/6b268d7e-13c9-42a9-8da4-7c5a06a9f635)  
Далее производим настройку клиентов (настройка на всех машинах идентична):  
## **HQ-SRV**  

```
nano /etc/chrony.conf
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/ee598d6b-181c-430a-b2db-f72025c76c0a)  
```
systemctl enable --now chronyd
```
Перезагружаем машину  
Проверяем:  
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/1a3b0be2-3919-49ef-8ee7-97cf1987dfaf)  



## **CLI**  
```
nano /etc/chrony.conf
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/dc931139-5cbf-4bf8-92d1-c6e23f4e2156)  

```
systemctl enable --now chronyd
```
Перезагружаем машину  

## **BR-R**  
```
nano /etc/chrony.conf
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/35d731d2-8976-40ed-8bf3-a25d64a8653b)  
```
systemctl enable --now chronyd
```
Перезагружаем машину  

## **BR-SRV**  
```
nano /etc/chrony.conf
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/99f15f8d-1abc-4a33-a2a5-dbad3b99c266)
```
systemctl enable --now chronyd
```
Перезагружаем машину  
Выполняем проверку:  

## **HQ-R**  
```
chronyc clients
```
В таблице должны появиться все клиенты, которые синхронизируют время с сервером.  
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/cc364a0a-2ed1-44c9-b917-57f5e6fa53f6)  

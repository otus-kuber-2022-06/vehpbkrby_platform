# vehpbkrby_platform

vehpbkrby Platform repository

# Выполнено ДЗ №1



 - [x] Основное ДЗ

 - [x] Задание со *



## В процессе сделано:

 - Изучен инстурмент GIT
 - Выполнена настройка локального окружения. 
 - Выполнен запускпервого контейнера.
 - Применен kubectl
 - Создан DockerFile
  

 Причины автоматического запуска пода core-dns наличие параметров livenes probe пода в деплойменте:
 В деплойменте COREDNS присутствует Livenes Probe
        livenessProbe:

          failureThreshold: 5

          httpGet:

            path: /health

            port: 8080

            scheme: HTTP

          initialDelaySeconds: 60

          periodSeconds: 10

          successThreshold: 1

          timeoutSeconds: 5
		  
управление остальными подами выполняется на основе  конфигурации кубелет kubelet conf
 


Задание со звездочкой: 
Причина не запуска является отстутсвие в манифесте заданных параметров сред окружения(ENV). 


## Как запустить проект:

 - Создать образ из докерфайла, запустить.
 ИЛИ
 - Применить манифест kubectl apply -f 



## Как проверить работоспособность:

 - kubectl port-forward --address 0.0.0.0 pod/web 8000:8000
 - перейти по ссылке http://localhost:8000/index.html
 

## PR checklist:

 - [ ] Выставлен label с темой домашнего задания

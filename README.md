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
 - Применить манифест kubectl apply -f web-pod.yml



## Как проверить работоспособность:

 - kubectl port-forward --address 0.0.0.0 pod/web 8000:8000
 - перейти по ссылке http://localhost:8000/index.html
 

## PR checklist:

 - [ ] Выставлен label с темой домашнего задания


ДЗ 2

Изучены ReplicaSet, Deployment, DaemonSet
Выявлены причины не запуска подов - необходимо указывать env
Обновление репликасет не привело к обновлению под, ввиду того, что функционал реплика сет основан на поддержании заданного количества подов. Обновление произойдет после удаления подов.

Реализованы 2 сценария развертывания
Реализован Daemonset с возможностью запуска подов на мастерноде




Домашнее задание 3


task01
Созданы Service Account bob , дана роль admin в рамках всего кластера
Создана  Service Account dave без доступа к кластеру

task02
Создан Namespace prometheus
Создан Service Account carol в этом Namespac
Service Account в Namespace prometheus которые могут get , list , watch в отношении Pods всего кластера

task03
Создан Namespace dev
Создан Service Account jane в Namespace dev
Дана jane роль admin в рамках Namespace dev
Создан Service Account ken в Namespace dev
Дана ken роль view в рамках Namespace dev


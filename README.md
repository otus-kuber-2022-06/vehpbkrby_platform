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
  

 

## Как запустить проект:

 - Создать образ из докерфайла, запустить.
 ИЛИ
 - Применить манифест kubectl apply -f web-pod.yaml



## Как проверить работоспособность:

 - kubectl port-forward --address 0.0.0.0 pod/web 8000:8000
 - перейти по ссылке http://localhost:8000/index.html
 

## PR checklist:

 - [ ] Выставлен label с темой домашнего задания

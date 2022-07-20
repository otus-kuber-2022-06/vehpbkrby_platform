Выполнено ДЗ №1
 Основное ДЗ

 Задание со *

В процессе сделано:
Изучен инстурмент GIT
Выполнена настройка локального окружения.
Выполнен запускпервого контейнера.
Применен kubectl
Создан DockerFile
Причины автоматического запуска пода core-dns наличие параметров livenes probe пода в деплойменте: В деплойменте COREDNS присутствует Livenes Probe livenessProbe:

      failureThreshold: 5

      httpGet:

        path: /health

        port: 8080

        scheme: HTTP

      initialDelaySeconds: 60

      periodSeconds: 10

      successThreshold: 1

      timeoutSeconds: 5
управление остальными подами выполняется на основе конфигурации кубелет kubelet conf

Задание со звездочкой: Причина не запуска является отстутсвие в манифесте заданных параметров сред окружения(ENV).

Как запустить проект:
Создать образ из докерфайла, запустить. ИЛИ
Применить манифест kubectl apply -f web-pod.yml
Как проверить работоспособность:
kubectl port-forward --address 0.0.0.0 pod/web 8000:8000
перейти по ссылке http://localhost:8000/index.html
PR checklist:
 Выставлен label с темой домашнего задания
ДЗ 2

Изучены ReplicaSet, Deployment, DaemonSet Выявлены причины не запуска подов - необходимо указывать env Обновление репликасет не привело к обновлению под, ввиду того, что функционал реплика сет основан на поддержании заданного количества подов. Обновление произойдет после удаления подов.

Реализованы 2 сценария развертывания Реализован Daemonset с возможностью запуска подов на мастерноде

Домашнее задание 3

task01 Созданы Service Account bob , дана роль admin в рамках всего кластера Создана Service Account dave без доступа к кластеру

task02 Создан Namespace prometheus Создан Service Account carol в этом Namespac Service Account в Namespace prometheus которые могут get , list , watch в отношении Pods всего кластера

task03 Создан Namespace dev Создан Service Account jane в Namespace dev Дана jane роль admin в рамках Namespace dev Создан Service Account ken в Namespace dev Дана ken роль view в рамках Namespace dev


Домашнее задание 4

Выполнены все задания. 
Ответы на контрольные вопросы: Предлагаемые ливенес проба формирует присутствие процесса, но не определеяет его работоспособность.  Подобная проба актуальна только как  поверхностная оценка здоровья пода.

Созданы все указанные деплойменты, проверены все предлагаемые сетевые сервисы. 
Задания со звездочками:
1. Скопирован манифест Дашборда, добавлен ингрес для доступа к сервису kubernetes-dasbord
2. Созданы 2 приложения с 2 разными выводами при обращении. Созданы 2 ингреса, основной для V1 приложения и второй для V2
Для выполнения теста канареечного деплоя можно выполнить CURL с указанием хедера и его значения: test: test
curl -s -H "test: test" http://192.168.49.2/version
В этом случае балансировка будет на v2. В остальных случаях - V1


<<<<<<< HEAD
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


Домашнее задание 4


Выполнены все задания. Ответы на контрольные вопросы: Предлагаемые ливенес проба формирует присутствие процесса, но не определеяет его работоспособность. Подобная проба актуальна только как поверхностная оценка здоровья пода.

Созданы все указанные деплойменты, проверены все предлагаемые сетевые сервисы. Задания со звездочками:

Скопирован манифест Дашборда, добавлен ингрес для доступа к сервису kubernetes-dasbord
Созданы 2 приложения с 2 разными выводами при обращении. Созданы 2 ингреса, основной для V1 приложения и второй для V2 Для выполнения теста канареечного деплоя можно выполнить CURL с указанием хедера и его значения: test: test curl -s -H "test: test" http://192.168.49.2/version В этом случае балансировка будет на v2. В остальных случаях - V1


Домашнее задание 5. 
Выполнена установка minioубедились в работоспособности ПО проверкой запусков основных элементов (Поды, стэтефулсеты и т.д.)
Запустив порт-форвардинг убедились в доступности вэбинтерфейса. 
В манифесте стейтефулсета были заменены имя пользователя и пароль на секреты. 
Создан манифест секрета. 



ДЗ HELM

Выполнено ДЗ в яндекс клауде. 
Выполнены часть дз со *. 
Не смог выполнить Kustomize

Решены задачи с чартмузеумом, харбором, ингесс, кубсфг

1. Nginix-Ingress


$ helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

$ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Skip local chart repository
...Successfully got an update from the "stable" chart repository
...Successfully got an update from the "ingress-nginx" chart repository
...Successfully got an update from the "coreos" chart repository
Update Complete. ⎈ Happy Helming!⎈


$ helm install quickstart ingress-nginx/ingress-nginx

NAME: quickstart
... lots of output ...


$ kubectl apply -f issuer.yaml -n cert-manager 

https://chartmuseum.51.250.80.42.nip.io/

Применение:
helm push 
helm repo update









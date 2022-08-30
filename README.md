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







Домашнее задание Operator



Задачи решены по варианту без символа "Змейки"

kubectl get jobs
NAME                         COMPLETIONS   DURATION   AGE
backup-mysql-instance-job    1/1           19s        3m23s
restore-mysql-instance-job   1/1           66s        111s

export MYSQLPOD=$(kubectl get pods -l app=mysql-instance -o jsonpath="{.items[*].metadata.name}")
kubectl exec -it $MYSQLPOD -- mysql -potuspassword -e "select * from test;" otus-database

+----+-------------+
| id | name        |
+----+-------------+
|  1 | some data   |
|  2 | some data-2 |








HomeWork Vault

NAME: vault

LAST DEPLOYED: Mon Aug 22 22:00:13 2022

NAMESPACE: default

STATUS: deployed

REVISION: 1

NOTES:

Thank you for installing HashiCorp Vault!

Now that you have deployed Vault, you should look over the docs on using

Vault with Kubernetes available here:

https://www.vaultproject.io/docs/

Your release is named vault. To learn more about the release, try:

$ helm status vault

$ helm get manifest vault

rtem@artem-otus:~/otus/vehpbkrby_platform/kubernetes-vault/vault/vault-helm$ kubectl exec -it vault-0 -- vault operator unseal 'DsmnLGenJGCJ0QyrV2vkmtEvWr1gDVemOYo7y0jYZKg='

Key Value

Seal Type shamir

Initialized true

Sealed false

Total Shares 1

Threshold 1

Version 1.11.2

Build Date 2022-07-29T09:48:47Z

Storage Type consul

Cluster Name vault-cluster-a19328ac

Cluster ID c8c4ceb1-8a95-e71a-5c64-c346d10346d6

HA Enabled true

HA Cluster https://vault-0.vault-internal:8201

HA Mode active

Active Since 2022-08-22T19:13:45.196743113Z

artem@artem-otus:~/otus/vehpbkrby_platform/kubernetes-vault/vault/vault-helm$ kubectl exec -it vault-1 -- vault operator unseal 'DsmnLGenJGCJ0QyrV2vkmtEvWr1gDVemOYo7y0jYZKg='

Key Value

Seal Type shamir

Initialized true

Sealed false

Total Shares 1

Threshold 1

Version 1.11.2

Build Date 2022-07-29T09:48:47Z

Storage Type consul

Cluster Name vault-cluster-a19328ac

Cluster ID c8c4ceb1-8a95-e71a-5c64-c346d10346d6

HA Enabled true

HA Cluster https://vault-0.vault-internal:8201

HA Mode standby

Active Node Address http://10.112.129.164:8200

artem@artem-otus:~/otus/vehpbkrby_platform/kubernetes-vault/vault/vault-helm$ kubectl exec -it vault-2 -- vault operator unseal 'DsmnLGenJGCJ0QyrV2vkmtEvWr1gDVemOYo7y0jYZKg='

Key Value

Seal Type shamir

Initialized true

Sealed false

Total Shares 1

Threshold 1

Version 1.11.2

Build Date 2022-07-29T09:48:47Z

Storage Type consul

Cluster Name vault-cluster-a19328ac

Cluster ID c8c4ceb1-8a95-e71a-5c64-c346d10346d6

HA Enabled true

HA Cluster https://vault-0.vault-internal:8201

HA Mode standby

Active Node Address http://10.112.129.164:8200

artem@artem-otus:~/otus/vehpbkrby_platform/kubernetes-vault/vault/vault-helm$

oken (will be hidden):

Success! You are now authenticated. The token information displayed below

is already stored in the token helper. You do NOT need to run "vault login"

again. Future Vault requests will automatically use this token.

Key Value

token hvs.QO14uhuepDF8QcuSRDnxWkAh

token_accessor gOMVIH7XH7s5FbrV2tiX0Gb6

token_duration ∞

token_renewable false

token_policies ["root"]

identity_policies []

policies ["root"]

Path Type Accessor Description

token/ token auth_token_d3aebc02 token based credentials

Key Value

refresh_interval 768h

password asajkjkahs

username otus

Path Type Accessor Description

kubernetes/ kubernetes auth_kubernetes_b199899f n/a

token/ token auth_token_d3aebc02 token based credentials

Key Value

ca_chain [-----BEGIN CERTIFICATE-----

MIIDnDCCAoSgAwIBAgIUTzGIuatqOwJehpGVvi10ZeQmprMwDQYJKoZIhvcNAQEL

BQAwFTETMBEGA1UEAxMKZXhtYXBsZS5ydTAeFw0yMjA4MjkxNzE5MDNaFw0yNzA4

MjgxNzE5MzNaMCwxKjAoBgNVBAMTIWV4YW1wbGUucnUgSW50ZXJtZWRpYXRlIEF1

dGhvcml0eTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAPn+dP3ZDeoJ

L3FIy/bO6QZgzeHJsum53ZdaDj7iWftA0uiTyBPQ8japVOyWQa28GE+IAQtQF60f

YkWPSNkTGYUKRQ4lImXES324r2Dw8ItgJRUMmSI+E+5jNBbwK+OmbB6O39BRHC9A

ZkWtfajCl98YW96m83EJpyLo31u9u+Mb7kp4QR9KcetsmWT8d+bg42xhWya2Uyoc

9A27Rl6MwR3lXMPVRL2glNKRrCt6o2T/o8UrayJ6EA/wkzfuAJF4P9I10OerqdSG

1UiTFH7cM7hX6wiy2y5Lop24A9k5kqOeACi2XOCs1o9k41hKkqXCEhxQbsQgSPWi

OEJBSw986b8CAwEAAaOBzDCByTAOBgNVHQ8BAf8EBAMCAQYwDwYDVR0TAQH/BAUw

AwEB/zAdBgNVHQ4EFgQUur3gFy7cNhyYyAEGezWPl/OqKMEwHwYDVR0jBBgwFoAU

oSpUG/8NzLPyDBCE0V3hkTMKgWowNwYIKwYBBQUHAQEEKzApMCcGCCsGAQUFBzAC

hhtodHRwOi8vdmF1bHQ6ODIwMC92MS9wa2kvY2EwLQYDVR0fBCYwJDAioCCgHoYc

aHR0cDovL3ZhdWx0OjgyMDAvdjEvcGtpL2NybDANBgkqhkiG9w0BAQsFAAOCAQEA

V2GbcGypNZAUWCh8xkV4cKtUsNgWVaub97oigm2zkkWaCgPn7zvFIDQJp6wTp1NC

yK6Gxj7me+TJpLxR2/0fc0J078n6RSjEsl7jXuaQ9eTqZbyYAGViQBUfAvDQ+iM3

jk+3HPOY2MFhTleYFLvmhGgFSSRFzZiL1pfF5S94aUMjcI6JA6v5AZYO5CckhZoB

2DsY6m/nMb7GhAThWsIvKjbsK+s5J8rql8DbqwFzSF5KgMBsH/b8gVHbZoQv5Mve

o4xejDdlVwnS7J33kVKlxTrcSWRnC5r3bOFhGLc4aDWer6wl4roIjjjKfsNarePU

3f2OXCyXbutfzGe1p/x/Ig==

-----END CERTIFICATE----- -----BEGIN CERTIFICATE-----

MIIDMjCCAhqgAwIBAgIUEF6vsHzqiME+GiD+ji7TMYp+AXIwDQYJKoZIhvcNAQEL

BQAwFTETMBEGA1UEAxMKZXhtYXBsZS5ydTAeFw0yMjA4MjkxNzA1NDRaFw0zMjA4

MjYxNzA2MTNaMBUxEzARBgNVBAMTCmV4bWFwbGUucnUwggEiMA0GCSqGSIb3DQEB

AQUAA4IBDwAwggEKAoIBAQDGEs6xMBmhFElx7g4Sx9b4fjtRHgvMqURtIL8vFvVQ

tosjLu4nKl0W5A0ZFX/i7qHpT+uxTG9yDNQX9eD9v3t+/dRc3Bu7S8wZ7cTAMkKM

8jl2+juT8cMmy0rB0rmxmSaLjLvYAdT5gsRF9rRSPXCTESRSHjDRK81FuJBCNKGG

hY7mYNUORKXbqOgRMPWcfFQCBM0myI30kcpBH6Cx12mhqwPTT3kOu4FMd1WykZlf

DylKvEOYkF66T/4QLGG1T63C6hgpbKpKicQj77Lhy8NxF9K5OFNA8c/k3Hg0TuFr

Uu3T/tZzFOLCfSswGD39OYFsbGMqsecDo6lzRdnraYmtAgMBAAGjejB4MA4GA1Ud

DwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0GA1UdDgQWBBShKlQb/w3Ms/IM

EITRXeGRMwqBajAfBgNVHSMEGDAWgBShKlQb/w3Ms/IMEITRXeGRMwqBajAVBgNV

HREEDjAMggpleG1hcGxlLnJ1MA0GCSqGSIb3DQEBCwUAA4IBAQCO6Z2qeJjhOHrK

EwZ6DUycG4Qo9KNcw9LdOcJUMaEYMeL3PvORmQNkc0FEILKwKypiSoz3GeieZf6Q

t+7Drh2L1gmfm6DwnjBseeR0ihgF+8Q7p8n9HOvQCpSFtAvmMG0iUQvxSww5G7PD

VobeTrWsZWvxkPfpJ2lEZzcntKsmY9wkRNHimvJeUpP2aw6Dq7qKuLmDtn8xFjjW

ZpwYEwUHR2JOkliZHP15OQa7vEAdfWniv+NVV3d+eUHfK2X5VHqF8/E/IQFXMrLA

XDH9ndoy3OmJhZSN6Va5wCgO/BZP/BADDAtQlkixhRpFQwUL6uTpqaAmQVlzuHjv

R3XRrXmP

-----END CERTIFICATE-----]

certificate -----BEGIN CERTIFICATE-----

MIIDZzCCAk+gAwIBAgIUFP8XS21Br29DnI7JVP1/XKbV0SIwDQYJKoZIhvcNAQEL

BQAwLDEqMCgGA1UEAxMhZXhhbXBsZS5ydSBJbnRlcm1lZGlhdGUgQXV0aG9yaXR5

MB4XDTIyMDgyOTE3MjQyOVoXDTIyMDgzMDE3MjQ1OVowHDEaMBgGA1UEAxMRZ2l0

bGFiLmV4YW1wbGUucnUwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCu

KWruxVkdPWsl0apd5gw0aoCP9fCI06Y6TBnhjcMqY3fiQoBBMiZgeNGAqklKjmOa

Id+2cfeK2hRl70dGV+SS2UdvMmenqtSuKdhBFDT3WyIEWl4RHYaTkOY0oo7YvZkP

2A7ZAbMhd6x/QczaqlyRB/geRO+/+uGyL426Kbl0ORmoJMQF0fwoEB37qmLeGo1n

f++jRMBLZ2leXeTKM5b24vqabQZAzJu7kVHCqIJUvf35IrslMCeQBe/xIA9YtZWT

h5XL0gIrGW8DRb/L9jxfLhBAsEGqQ8T5iomMCx9jiHFJvWWGgdnQ5c2TPO0NHsoz

9T1Z6E5RON8kh3y5+HdlAgMBAAGjgZAwgY0wDgYDVR0PAQH/BAQDAgOoMB0GA1Ud

JQQWMBQGCCsGAQUFBwMBBggrBgEFBQcDAjAdBgNVHQ4EFgQUid1bkipuRL6rzkwD

ALrWoqgH0ygwHwYDVR0jBBgwFoAUur3gFy7cNhyYyAEGezWPl/OqKMEwHAYDVR0R

BBUwE4IRZ2l0bGFiLmV4YW1wbGUucnUwDQYJKoZIhvcNAQELBQADggEBACPaKKFV

oEJyR7J2IJ0IdzYFa2+UO2dhydbB2lfv7PfOEMMrbSF8RxOmTVwiBaO6O+10cvOK

5YHGELIVxeRIFIptIaQH15O6fwDdjmUP6tDIjJvnt8GH5gRwPGI5+T6hgma+mn8x

JyfDLktcXi3DAqqRlHALoPU5+EBG0USxZod3bMBLTRo/ewMsrcQMNVImLjLNZ13Q

W9pliFrsgvU08d6TB82T1fKCYW1ykHIaMKFY0rHGLrrXrYAysOPqIev/+uQGAaIn

GXQl1Ihm9KiApujskigkbDpIalemHVFlC+XEvxHm/7uFjLfSwW+vPPI8+ZsWE929

Mf7jFFYhM+C/ISA=

-----END CERTIFICATE-----

expiration 1661880299

issuing_ca -----BEGIN CERTIFICATE-----

MIIDnDCCAoSgAwIBAgIUTzGIuatqOwJehpGVvi10ZeQmprMwDQYJKoZIhvcNAQEL

BQAwFTETMBEGA1UEAxMKZXhtYXBsZS5ydTAeFw0yMjA4MjkxNzE5MDNaFw0yNzA4

MjgxNzE5MzNaMCwxKjAoBgNVBAMTIWV4YW1wbGUucnUgSW50ZXJtZWRpYXRlIEF1

dGhvcml0eTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAPn+dP3ZDeoJ

L3FIy/bO6QZgzeHJsum53ZdaDj7iWftA0uiTyBPQ8japVOyWQa28GE+IAQtQF60f

YkWPSNkTGYUKRQ4lImXES324r2Dw8ItgJRUMmSI+E+5jNBbwK+OmbB6O39BRHC9A

ZkWtfajCl98YW96m83EJpyLo31u9u+Mb7kp4QR9KcetsmWT8d+bg42xhWya2Uyoc

9A27Rl6MwR3lXMPVRL2glNKRrCt6o2T/o8UrayJ6EA/wkzfuAJF4P9I10OerqdSG

1UiTFH7cM7hX6wiy2y5Lop24A9k5kqOeACi2XOCs1o9k41hKkqXCEhxQbsQgSPWi

OEJBSw986b8CAwEAAaOBzDCByTAOBgNVHQ8BAf8EBAMCAQYwDwYDVR0TAQH/BAUw

AwEB/zAdBgNVHQ4EFgQUur3gFy7cNhyYyAEGezWPl/OqKMEwHwYDVR0jBBgwFoAU

oSpUG/8NzLPyDBCE0V3hkTMKgWowNwYIKwYBBQUHAQEEKzApMCcGCCsGAQUFBzAC

hhtodHRwOi8vdmF1bHQ6ODIwMC92MS9wa2kvY2EwLQYDVR0fBCYwJDAioCCgHoYc

aHR0cDovL3ZhdWx0OjgyMDAvdjEvcGtpL2NybDANBgkqhkiG9w0BAQsFAAOCAQEA

V2GbcGypNZAUWCh8xkV4cKtUsNgWVaub97oigm2zkkWaCgPn7zvFIDQJp6wTp1NC

yK6Gxj7me+TJpLxR2/0fc0J078n6RSjEsl7jXuaQ9eTqZbyYAGViQBUfAvDQ+iM3

jk+3HPOY2MFhTleYFLvmhGgFSSRFzZiL1pfF5S94aUMjcI6JA6v5AZYO5CckhZoB

2DsY6m/nMb7GhAThWsIvKjbsK+s5J8rql8DbqwFzSF5KgMBsH/b8gVHbZoQv5Mve

o4xejDdlVwnS7J33kVKlxTrcSWRnC5r3bOFhGLc4aDWer6wl4roIjjjKfsNarePU

3f2OXCyXbutfzGe1p/x/Ig==

-----END CERTIFICATE-----

private_key -----BEGIN RSA PRIVATE KEY-----

MIIEpAIBAAKCAQEArilq7sVZHT1rJdGqXeYMNGqAj/XwiNOmOkwZ4Y3DKmN34kKA

QTImYHjRgKpJSo5jmiHftnH3itoUZe9HRlfkktlHbzJnp6rUrinYQRQ091siBFpe

ER2Gk5DmNKKO2L2ZD9gO2QGzIXesf0HM2qpckQf4HkTvv/rhsi+Nuim5dDkZqCTE

BdH8KBAd+6pi3hqNZ3/vo0TAS2dpXl3kyjOW9uL6mm0GQMybu5FRwqiCVL39+SK7

JTAnkAXv8SAPWLWVk4eVy9ICKxlvA0W/y/Y8Xy4QQLBBqkPE+YqJjAsfY4hxSb1l

hoHZ0OXNkzztDR7KM/U9WehOUTjfJId8ufh3ZQIDAQABAoIBACvfORWu1vT7rMsZ

Ft6Sfc6SaZJaNN5y2nPjCb381QYPinqPn/lMZch1hujvfIjwd3yzPcSazu3GY88N

yJmauHSZkVoci2n8KZk550T1jyYkadxI21taYbU4khT+QhetIyqPlaXqvLIYkHZ6

H92RfsH2DPWrDe4Bh+s3+W7E5fe1o8Zx39vNVa6jHIOZcTgrw5UNqcd6jhz11gcs

r9IrZUD/5lr4R04IkPCsol59zRVrIZGYVMfc/GSbVFT+CDPLuPxDdF+X5PxFtfe8

IAgenLUaKxkQzHk2sovarss5ibH4VW3wbrRUCiohY1p4X1WigBUJjVqnaRYnmtEH

834g7d0CgYEAwQdDRK8IuZX8tB3VHamW7stw4ybdw/0a6vHvwLci51rQ7DLleRN0

shyykWRlD5Wv2kG1M4GHkETzwO2pPDSwNjVtvJo4ceEddWrJ+SANXNPqUUu4iERP

lusFsY8gHxDmuLNc6PGpRCDRll3BG2brOm8hNMT+rciFXhFj4Z2JC48CgYEA5vqD

1RCleoTp8kCchMXnuBcF5wUC1YvwToXxc6BECZ6wU9xkxAT7Qq/zGHW0+rSho66X

MMSNR5xUlZHfOnLviuEsFwSoRT/g7XZl+i5Tk9RJnq8QqobzDThyCh9eY0dTr2c5

It0InedaDOC6dBjkN95boiwbRJ33NPVC4+nsY8sCgYEApYlf8+gTmGx7MdAfsvd8

O792SSdMqcZGrlPbIy8rHLMyVk1zo7i+q/yWWr95N7tL+uW8yrX7lwq666olJz+c

GnEJcePkIi1HQSname4V55TI7vz7/MhwZOGamWI/zsSEyMLxG8gbPBTVCJnQgHpr

okopdQK30jsTvM83FAYwwBsCgYEAwPNHC8cTJW1A7XESD0wvzTXWZW1nN7Ll9QKp

eBjKnWqmC/gRaTpsFwJaxfUWUVRxrwWbIU8gYlDyy9uGqhH3j4GYzkXCt86r/FKq

z7rBcL2nHltKRdnj0gh0I4ae17pu6xkEvt38Y8QvEpDs0S02AIHM9IV55fE74E5+

KVxxb88CgYBb1sOcPtp376lkSedVePiAsbnKTWfQmKJo5s6TSD46ACF/oJbznJLY

AE5964O3q4DugUYrEwY1P7nBNxJaplGAtyMssk2nTNT0KVTl8R0k8cvywIrILUtL

pyOdTKnzZtEug4/wRwWl4znBNYFVJZRiSkKFqRZsIuxOJcTTg7HS6g==

-----END RSA PRIVATE KEY-----

private_key_type rsa

serial_number 14:ff:17:4b:6d:41:af:6f:43:9c:8e:c9:54:fd:7f:5c:a6:d5:d1:22

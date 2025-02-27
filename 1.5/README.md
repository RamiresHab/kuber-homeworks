# Домашнее задание к занятию «Сетевое взаимодействие в K8S. Часть 2»

------

### Задание 1. Создать Deployment приложений backend и frontend

1. Создать Deployment приложения _frontend_ из образа nginx с количеством реплик 3 шт.
2. Создать Deployment приложения _backend_ из образа multitool. 
3. Добавить Service, которые обеспечат доступ к обоим приложениям внутри кластера. 
4. Продемонстрировать, что приложения видят друг друга с помощью Service.
5. Предоставить манифесты Deployment и Service в решении, а также скриншоты или вывод команды п.4.

------

### Ответ:

Ссылка на деплоймент фронтэнда: https://github.com/RamiresHab/kuber-homeworks/blob/main/1.5/deployment-frontend.yaml

Ссылка на деплоймент бэкэнда: https://github.com/RamiresHab/kuber-homeworks/blob/main/1.5/deployment-backend.yaml

Ссылка на сервис фронтэнда: https://github.com/RamiresHab/kuber-homeworks/blob/main/1.5/service-frontend.yaml

Ссылка на сервис бэкэнда: https://github.com/RamiresHab/kuber-homeworks/blob/main/1.5/service-backend.yaml

Скриншот вывода kubectl apply для деплойментов и сервисов
![Alt text](image.png)

Скриншот вывода команды curl из пода бэкэнда до сервиса фронтенда
![Alt text](image-1.png)

Скриншот вывода команды curl из пода фронтэнда до сервиса бэкэнда
![Alt text](image-2.png)

------

### Задание 2. Создать Ingress и обеспечить доступ к приложениям снаружи кластера

1. Включить Ingress-controller в MicroK8S.
2. Создать Ingress, обеспечивающий доступ снаружи по IP-адресу кластера MicroK8S так, чтобы при запросе только по адресу открывался _frontend_ а при добавлении /api - _backend_.
3. Продемонстрировать доступ с помощью браузера или `curl` с локального компьютера.
4. Предоставить манифесты и скриншоты или вывод команды п.2.

------

### Ответ:

Ссылка на ингресс: https://github.com/RamiresHab/kuber-homeworks/blob/main/1.5/ingress.yaml

Скриншот включения ingress контроллера через helm
![Alt text](image-3.png)

Скриншот вывода kubectl apply для ингресса
![Alt text](image-4.png)

Доступ до бэкэнда с помощью команды curl с локального компьютера
![Alt text](image-5.png)

Доступ до фронтэнда с помощью команды curl с локального компьютера
![Alt text](image-6.png)

------

### Правила приема работы

1. Домашняя работа оформляется в своем Git-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl` и скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.

------
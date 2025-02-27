# Домашнее задание к занятию «Как работает сеть в K8s»

-----

### Задание 1. Создать сетевую политику или несколько политик для обеспечения доступа

1. Создать deployment'ы приложений frontend, backend и cache и соответсвующие сервисы.
2. В качестве образа использовать network-multitool.
3. Разместить поды в namespace App.
4. Создать политики, чтобы обеспечить доступ frontend -> backend -> cache. Другие виды подключений должны быть запрещены.
5. Продемонстрировать, что трафик разрешён и запрещён.

### Правила приёма работы

1. Домашняя работа оформляется в своём Git-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд, а также скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.

-----

### Решение

Файл с деплойментами: https://github.com/RamiresHab/kuber-homeworks/blob/main/3.3/deployment.yml

Файл с сервисами: https://github.com/RamiresHab/kuber-homeworks/blob/main/3.3/service.yml

Файл с манифестом неймспейса: https://github.com/RamiresHab/kuber-homeworks/blob/main/3.3/namespace.yml

Файл с network policies: https://github.com/RamiresHab/kuber-homeworks/blob/main/3.3/np.yml

Файл с манифестом ingress-deny-all: https://github.com/RamiresHab/kuber-homeworks/blob/main/3.3/ingress-deny-all.yml

Подготовим кластер
![Alt text](image.png)

Создадим namespace app
![Alt text](image-1.png)

Запустим деплойменты
![Alt text](image-2.png)

Запустим сервисы
![Alt text](image-3.png)

Проверяем поды
![Alt text](image-5.png)

Бэк и кэш доступны из пода фронта
![Alt text](image-4.png)

Применим запрещающую политику
![Alt text](image-6.png)

Бэк и кэш недоступны из пода фронта
![Alt text](image-7.png)

Применим network policies
![Alt text](image-8.png)

Подключимся к поду фронта, есть доступ до бэка и нет доступа до кэша
![Alt text](image-9.png)

Подключимся к поду бэка, есть доступ до фронта и кэша
![Alt text](image-10.png)

Подключимся к поду кэша, есть доступ до бэка и нет доступа до фронта
![Alt text](image-11.png)

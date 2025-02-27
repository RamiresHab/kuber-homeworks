# Домашнее задание к занятию «Хранение в K8s. Часть 2»

------

### Задание 1

**Что нужно сделать**

Создать Deployment приложения, использующего локальный PV, созданный вручную.

1. Создать Deployment приложения, состоящего из контейнеров busybox и multitool.
2. Создать PV и PVC для подключения папки на локальной ноде, которая будет использована в поде.
3. Продемонстрировать, что multitool может читать файл, в который busybox пишет каждые пять секунд в общей директории. 
4. Удалить Deployment и PVC. Продемонстрировать, что после этого произошло с PV. Пояснить, почему.
5. Продемонстрировать, что файл сохранился на локальном диске ноды. Удалить PV.  Продемонстрировать что произошло с файлом после удаления PV. Пояснить, почему.
5. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

------

### Решение

Файл с деплойментом приложения, StorageClass, PV и PVC: https://github.com/RamiresHab/kuber-homeworks/blob/main/2.2/deployment-2.2.yaml

Результат выполнения команды "kubectl apply -f deployment-2.2.yaml"
![Alt text](image.png)

Чтение файла из контейнера multitool
![Alt text](image-1.png)

Мы удалили deployment и PVC, но PV остался в статусе Released из-за persistentVolumeReclaimPolicy: Retain в манифесте PV.
![Alt text](image-2.png)

Файл сохранился на ноде
![Alt text](image-3.png)


------

### Задание 2

**Что нужно сделать**

Создать Deployment приложения, которое может хранить файлы на NFS с динамическим созданием PV.

1. Включить и настроить NFS-сервер на MicroK8S.
2. Создать Deployment приложения состоящего из multitool, и подключить к нему PV, созданный автоматически на сервере NFS.
3. Продемонстрировать возможность чтения и записи файла изнутри пода. 
4. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

------

### Решение

------

Файл с деплойментом приложения, PV и PVC: https://github.com/RamiresHab/kuber-homeworks/blob/main/2.2/deployment-nfc-2.2.yaml

Сервер включен
![Alt text](image-4.png)
![Alt text](image-6.png)
![Alt text](image-5.png)

Возможность чтения и записи изнутри пода (запись идёт контейнером busybox каждые пять секунд):
![Alt text](image-7.png)

Файл существует на ноде:

![Alt text](image-8.png)

### Правила приёма работы

1. Домашняя работа оформляется в своём Git-репозитории в файле README.md. Выполненное задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl`, а также скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.
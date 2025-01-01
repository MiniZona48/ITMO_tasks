# ITMO_tasks

![Описание изображения](/images/picture.jpg)

Ход работы:

1) Установил Docker, Kubectl, Minikube
2) Разработал Dockerfile (ссылка), который включает в себя следующее:

- Создается на основе python:3-alpine;
- Создается каталог /app;
- Добавляется в него html файл;
- Запускается CMD инструкция "python -m http.server 8000" от имени пользователя с uid 1001

3) Собрал образ c помощью команды "docker build -t web_app:1.0.0 ."
4) Проверил работоспособность

5) загрузил его на Docker Hub с помощью команды "docker push web_app:1.0.0"

6) Разработал Kubernetes Deployment manifest с 2 репликами и LivenessProde. (ссылка)

7) Установил manifest в кластер kubernetes с помощью команды ""

8) Разработал Service NodePort для Deployment (ссылка)

перейти по http://<Node Ip>:<Node port>/hello.html

Источники:

- <https://habr.com/ru/companies/slurm/articles/692450/>
- <https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/>
- <https://kubernetes.io/docs/concepts/services-networking/service/#type-nodeport>
- <https://habr.com/ru/articles/651653/>

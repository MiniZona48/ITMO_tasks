
Ход работы:

1) Установил Docker, Kubectl, Minikube
2) Разработал [Dockerfile](/devops/DockerFile), который включает в себя следующее:

- Создается на основе python:3-alpine;
- Создается каталог /app;
- Добавляется в него html файл;
- Запускается CMD инструкция "python -m http.server 8000" от имени пользователя с uid 1001

3) Собрал образ c помощью команды "docker build -t web_app:1.0.0 ."

4) Проверил работоспособность с помощью команды "docker run -p 8000:8000 -it web_app:1.0.0" и перехода по ссылке <http://localhost:8000/hello.html>

![Проверка работы образа](/devops/images/test_docker.jpg)

5) Загрузил образ на Docker Hub с помощью команды "docker push web_app:1.0.0"

6) Разработал [Kubernetes Deployment manifest](/devops/manifest.yaml) с 2 репликами и LivenessProde.

7) Установил manifest в кластер kubernetes с помощью команды "kubectl apply -f manifest_path", где вместо manifest_path должен быть указан разработанный yaml файл Kubernetes Deployment manifest.

![Установка манифеста](/devops/images/apply.jpg)

![Получение списка деплойментов](/devops/images/get_depl.jpg)

![Получение списка подов](/devops/images/get_pods.jpg)

![Проброска портов](/devops/images/port_forward.jpg)

![Проверка деплоймента](/devops/images/test_dep.jpg)

8) Разработал [Service NodePort](/devops/service_web.yml) для Deployment, который в теории должен открываться на "http://<Node Ip>:<Node port>/hello.html". Манифест применялся с помощью команды "kubectl create -f path"

![Описание деплоймента](/devops/images/describe_dep.jpg)

![Описание узла](/devops/images/describe_node.jpg)

![Описание сервиса](/devops/images/describe_service.jpg)

![Проброска сервиса](/devops/images/test_service.jpg)

Источники:

- <https://habr.com/ru/companies/slurm/articles/692450/>
- <https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/>
- <https://kubernetes.io/docs/concepts/services-networking/service/#type-nodeport>
- <https://habr.com/ru/articles/651653/>

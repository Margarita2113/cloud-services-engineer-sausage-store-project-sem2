# Sausage Store

![image](https://user-images.githubusercontent.com/9394918/121517767-69db8a80-c9f8-11eb-835a-e98ca07fd995.png)

## Технологии проекта

* Frontend – TypeScript, Angular.
* Backend  – Java 16, Spring Boot, Spring Data.
* Database – H2.

## Общие цели проекта

- Собрать и задеплоить backend, frontend и backend-report.
- Развернуть образы в Docker Hub.
- Создать multi-stage Dockerfile для фронтенда: первый этап собирает статику, второй — копирует в образ nginx.
- Исправить ошибки сборки backend-report.
- В backend реализовать Flyway-миграции с V001–V004.
- Добавить необходимые миграции для данных (V003) и индексы (V004).
- Описать манифесты и чарты для Kubernetes: PostgreSQL/Postgres и MongoDB зависимости, Ingress, TLS, PVC, HPA/VPA, LivenessProbe.
- Включить optional Job для автоматизации создания базы и пользователя MongoDB.
- Настроить Nexus Helm-релизы и workflow для пайплайна: add_helm_chart_to_nexus и deploy_helm_chart_to_kubernetes.
- Включить шаги пайплайна по добавлению Nexus Helm-репозитория, настройке kubeconfig и деплою helm upgrade.

## Предварительные требования

Перед запуском убедитесь, что на вашей машине установлены следующие инструменты:

- kubectl
- helm

## Руководство по установке
### Backend

Install Java 16 and maven and run:

```bash
cd backend
mvn package
cd target
java -jar sausage-store-0.0.1-SNAPSHOT.jar
```

### Frontend

Install NodeJS and npm on your computer and run:

```bash
cd frontend
npm install
npm run build
npm install -g http-server
sudo http-server ./dist/frontend/ -p 80 --proxy http://localhost:8080
```

## Для запуска через Kubernetes:

1. Перейдите в директорию с Helm chart'ом:
 
```cd sausage-store-chart```
   
2. Установите Helm-чарт:

```helm upgrade --install sausage-store . --namespace r-devops-magistracy-project-3sem-2019126118```

3. Убедитесь, что все поды успешно запущены:

```kubectl get pods```

## Проект доступен по ссылке 

https://front-margo.2sem.students-projects.ru/

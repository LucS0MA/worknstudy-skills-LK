# Microservices

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les différences avec l'architecture monolithique ✔️
- la communication asynchrone entre services ✔️
- le deploiement d'un cluster ❌ 


## 💻 J'utilise

### Un exemple personnel commenté  ✔️

## Voici le docker-compose de mon projet, où l'on retrouve les microservices de mon application et leur orchestration ##
services:
  db:
    image: postgres
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: example
      POSTGRES_DB: postgres
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -d postgres -U postgres"]
      interval: 1s
      timeout: 2s
      retries: 100

  adminer:
    image: adminer
    depends_on:
      db:
        condition: service_healthy

  backend:
    environment:
      - CHOKIDAR_USEPOLLING=true
      - WATCHPACK_POLLING=true 
    build: ./backend
    volumes:
      - ./backend/src:/app/src
    healthcheck:
      test: 'curl --fail --request POST --header ''content-type: application/json'' --url ''http://localhost:4000'' --data ''{"query":"query { __typename }"}'' || exit 1'
      interval: 1s
      timeout: 2s
      retries: 100
    depends_on:
      db:
        condition: service_healthy

  frontend:
    environment:
      - CHOKIDAR_USEPOLLING=true
      - WATCHPACK_POLLING=true 
    build: ./frontend
    volumes:
      - ./frontend/src:/app/src
    depends_on:
      backend:
        condition: service_healthy
    healthcheck:
      test: "curl --fail --request GET --url 'http://localhost:5173' || exit 1"
      interval: 1s
      timeout: 2s
      retries: 100
  api_gateway:
    image: nginx
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      backend:
        condition: service_healthy
      frontend:
        condition: service_healthy
    ports:
      - 7000:80
  img:
    build: ./img
    healthcheck:
      test: "curl --fail --request GET --url 'http://localhost:4000' || exit 1"
      interval: 1s
      timeout: 2s
      retries: 100
    volumes:
      - ./img/uploads:/app/uploads

### Utilisation dans un projet ✔️

[lien github](https://github.com/LucS0MA/APIrest)

Description :

### Utilisation en production si applicable ✔️

[lien github](https://github.com/LucS0MA/APIrest)

Description :

### Utilisation en environement professionnel ❌ 

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️

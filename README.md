# Chatbot Widget Suite

## Descripción

Proyecto completo que integra el **frontend** y **backend** del Chatbot Widget.  
Permite a los usuarios interactuar con un asistente inteligente a través de una interfaz web moderna (Angular 20), conectada a una API robusta (NestJS) que gestiona la lógica, almacenamiento y procesamiento de las conversaciones.  
Incluye integración con servicios de IA (OpenAI, Qdrant), persistencia en PostgreSQL mediante Prisma, y soporte con Redis para cache y gestión eficiente de datos.

---

## Tecnologías utilizadas

- **Angular 20** (Frontend)
- **NestJS + TypeScript** (Backend)
- **Prisma (PostgreSQL)**
- **Qdrant (Vector DB)**
- **OpenAI (LLM)**
- **Redis**
- **Docker**
- **npm**

---

## Acceso

- **Frontend:** [http://localhost:4200](http://localhost:4200)
- **Backend API:** [http://localhost:3000](http://localhost:3000)

---

## Estructura del proyecto

```
ChatbotIA/
├─ frontend/
│  ├─ Dockerfile
│  ├─ package.json
│  ├─ angular.json
│  └─ src/
├─ backend/
│  ├─ Dockerfile
│  ├─ package.json
│  ├─ tsconfig.json
│  ├─ prisma/
│  │   ├─ schema.prisma
│  │   └─ migrations/
│  └─ src/
├─ docker-compose.yml
```

---

## Configuración

- **Frontend:**  
  Configura las variables en `src/environments/environment.ts` y `src/environments/environment.prod.ts`  
  Ejemplo:
  ```typescript
  export const environment = {
    production: false,
    apiBaseUrl: 'http://localhost:3000'
  };
  ```

- **Backend:**  
  Configura el archivo `.env` en la carpeta `backend`  
  Ejemplo:
  ```env
  PORT=3000
  NODE_ENV=development
  CORS_ORIGIN=http://localhost:4200
  LOG_LEVEL=info
  DATABASE_URL="postgresql://postgres:postgres@localhost:5432/chatbot_db"
  REDIS_URL=redis://localhost:6379
  OPENAI_API_KEY=
  QDRANT_URL=http://localhost:6333
  QDRANT_COLLECTION=docs
  RAG_TEST_MODE=false
  RAG_MODE=qdrant
  ```

---

## Despliegue con Docker Compose

Levanta todo el stack con:
```bash
docker compose up -d --build
```

---

## Contribución

1. Clona el repositorio
2. Configura las variables de entorno en ambos entornos (`frontend` y `backend`)
3. Construye las imágenes Docker con los respectivos `Dockerfile`
4. Inicializa Prisma y migraciones en el backend
5. Desarrolla nuevas funcionalidades en `frontend/src` y `backend/src`
6. Abre Pull Request y documenta los cambios

---

## Licencia

Este proyecto es **privado y de uso comercial**.  
Queda estrictamente prohibida la distribución, copia, modificación o uso total o parcial sin la autorización expresa y por escrito del titular.  
Para obtener acceso, soporte técnico o licencias comerciales, contacta a [MartiPE](mailto:martirspe@gmail.com)
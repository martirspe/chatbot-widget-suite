# Chatbot Widget Suite

## Descripción

Proyecto completo que integra el **frontend** y **backend** del Chatbot Widget.  
Permite a los usuarios interactuar con un asistente inteligente a través de una interfaz web moderna (Angular 20), conectada a una API robusta (NestJS) que gestiona la lógica, almacenamiento y procesamiento de las conversaciones.  
Incluye integración con servicios de IA (OpenAI, Qdrant), persistencia en PostgreSQL mediante Prisma, y soporte con Redis para cache y gestión eficiente de datos.

---

## Repositorios principales

- [chatbot-widget-frontend](https://github.com/martirspe/chatbot-widget-frontend)
- [chatbot-widget-backend](https://github.com/martirspe/chatbot-widget-backend)

## Submódulos

Este repositorio incluye los submódulos:
- `frontend/` → [chatbot-widget-frontend](https://github.com/martirspe/chatbot-widget-frontend)
- `backend/` → [chatbot-widget-backend](https://github.com/martirspe/chatbot-widget-backend)

### Clonar con submódulos

```bash
git clone --recurse-submodules https://github.com/martirspe/chatbot-widget-suite.git
```

### Actualizar submódulos

```bash
git submodule update --remote
```
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

## Despliegue con Docker Compose y configuración de variables de entorno

Levanta todo el stack con:
```bash
docker compose up -d --build
```

Si ejecutas el proyecto con Docker, asegúrate de que las URLs de conexión para servicios como PostgreSQL, Redis y Qdrant utilicen el **nombre del servicio definido en Docker Compose** en lugar de `localhost` o direcciones IP.

Por ejemplo, en tu archivo `.env`:

- Para PostgreSQL:  
  `DATABASE_URL=postgresql://<usuario>:<contraseña>@<nombre_del_servicio_postgres>:<puerto>/<base_de_datos>`

- Para Qdrant:  
  `QDRANT_URL=http://<nombre_del_servicio_qdrant>:<puerto>`

- Para Redis:  
  `REDIS_URL=redis://<nombre_del_servicio_redis>:<puerto>`

Esto permite que los contenedores se comuniquen correctamente dentro de la red de Docker.  
**No uses `localhost` ni IPs locales para estos servicios cuando trabajes con Docker.**

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
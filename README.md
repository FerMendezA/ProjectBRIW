# ProjectBRIW

Proyecto de la asignatura Búsqueda y Recuperación de Información en la Web

## Integrantes

| Nombre  | Foto |
| ------- | ----- |
| Julián Enrique Chan Palomo | <img src="https://github.com/user-attachments/assets/1d7206b4-cc8a-4155-9542-cca7fb2bf927" width="200"> |
| Isaac Mauricio Ehuan Ávila | <img src="https://github.com/user-attachments/assets/e25374a5-138e-43cf-9ef4-e6abbeacbfac" width="200"> |
| Jesús Fernando Méndez Avilés | <img src="https://github.com/user-attachments/assets/400f5776-8ad2-48a0-8cd6-47d56c160444" width="200"> |
| Rafael Alberto Perea Hernández | 

## **Requisitos Previos**
- Docker y Docker Compose instalados.
- Espacio suficiente en disco.
- Archivos de configuración y Dockerfiles en las rutas correctas.

---

## **Estructura del Proyecto**
```
.
├── docker-compose.yml
├── solr/
│   └── Dockerfile
├── front-end/
│   └── Dockerfile
├── Back/
│   └── Dockerfile
└── api-gen-archivos/
    └── Dockerfile
```

---

## **Configuración de la Red**
Red personalizada `app_network` con la subred `10.10.10.0/24` y direcciones IP fijas para cada servicio.

---

## **Servicios**
1. **Solr**
   - **Puerto:** `8983`
   - **Dirección IP:** `10.10.10.2`
   - **Acceso:** [http://10.10.10.2:8983](http://10.10.10.2:8983)

2. **Front**
   - **Puerto:** `80`
   - **Dirección IP:** `10.10.10.3`
   - **Acceso al frontend:** [http://10.10.10.3](http://10.10.10.3)

3. **PHP-Webserver**
   - **Puerto:** `8080`
   - **Dirección IP:** `10.10.10.4`
   - **Acceso:** [http://10.10.10.4:8080](http://10.10.10.4:8080)

4. **API-Gen-Archivos**
   - **Puerto:** `3000`
   - **Dirección IP:** `10.10.10.5`
   - Variables de entorno:
     - `SOLR_HOST=10.10.10.2`
     - `SOLR_PORT=8983`
     - `SOLR_CORE=ProyectoFinal`
   - **Acceso:** [http://10.10.10.5:3000](http://10.10.10.5:3000)

---

## **Instrucciones**

1. **Clonar el repositorio:**
   ```bash
   git clone <url-del-repositorio>
   cd <directorio-del-repositorio>
   ```

2. **Levantar los servicios:**
   ```bash
   docker-compose up --build
   ```

3. **Verificar los servicios:**
   ```bash
   docker ps
   ```

4. **Acceso a los servicios:**
   - **Solr:** [http://10.10.10.2:8983](http://10.10.10.2:8983)
   - **Front:** [http://10.10.10.3](http://10.10.10.3)
   - **PHP-Webserver:** [http://10.10.10.4:8080](http://10.10.10.4:8080)
   - **API:** [http://10.10.10.5:3000](http://10.10.10.5:3000)

---

## **Notas**
- Verifica que los puertos estén disponibles.
- Para detener los servicios:
  ```bash
  docker-compose down -v
  ```

---

## **Solución de Problemas**
1. **Error de conexión entre contenedores:**
   ```bash
   docker network inspect app_network
   ```

2. **Puertos en uso:**
   - Modifica los puertos en el archivo `docker-compose.yml`.

3. **Errores al construir imágenes:**
   - Confirma que los Dockerfiles están en las rutas correctas.

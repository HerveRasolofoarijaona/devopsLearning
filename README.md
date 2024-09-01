# Operation Center - Docker Setup

Ce dépôt contient les configurations Docker Compose pour les applications utilisées dans mon centre d'opérations. Vous trouverez ci-dessous les détails pour chaque service.

## Applications Incluses

### 1. WSO2 API Manager (WSO2 APIM)

- **Image**: `wso2/wso2am:4.1.0`
- **Ports**:
  - HTTP Gateway: `8280`
  - HTTPS Gateway: `8243`
  - Management Console: `9443`
  - HTTP Servlet Transport: `9763`
  - HTTPS Servlet Transport: `9444`
  - DevPortal: `9445`
  
### 2. WSO2 Enterprise Integrator (WSO2 EI)

- **Image**: `wso2/wso2e:latest`
- **Ports**:
  - HTTP Pass-Through Transport: `8290`
  - HTTPS Pass-Through Transport: `8253`
  - Carbon Management Console: `9444`
- **Base de Données**:
  - **Hôte**: `postgres`
  - **Port**: `5432`
  - **Nom**: `wso2ei_db`
  - **Utilisateur**: `wso2ei_user`
  - **Mot de passe**: `ei_password`

### 3. ActiveMQ

- **Image**: `rmohr/activemq:latest`
- **Ports**:
  - JMS: `61616`
  - Web Console: `8161`
- **Volume de Données**: `./activemq_data:/data`

### 4. PostgreSQL

- **Image**: `postgres:latest`
- **Ports**:
  - `5432`
- **Variables d'Environnement**:
  - `POSTGRES_DB`: `wso2ei_db`
  - `POSTGRES_USER`: `wso2ei_user`
  - `POSTGRES_PASSWORD`: `ei_password`
- **Volume de Données**: `postgres_data:/var/lib/postgresql/data`

### 5. Apache NiFi

- **Image**: `apache/nifi:latest`
- **Ports**:
  - Web UI: `8080`

### 6. Elasticsearch

- **Image**: `elasticsearch:latest`
- **Ports**:
  - HTTP: `9200`
  - Transport: `9300`

## Utilisation

Pour démarrer tous les services, exécutez :

```bash
docker-compose up -d

```

# Vérification de l'Installation

## Services Disponibles

- **WSO2 API Manager**:
  - DevPortal: [http://localhost:9445/devportal](http://localhost:9445/devportal)
  - Console Admin: [http://localhost:9443/carbon](http://localhost:9443/carbon)

- **WSO2 Enterprise Integrator**:
  - Console de Gestion: [http://localhost:9444/carbon](http://localhost:9444/carbon)

- **ActiveMQ**:
  - Console Web: [http://localhost:8161/admin](http://localhost:8161/admin)

- **PostgreSQL**:
  - Connexion via un client de base de données à `localhost:5432`

- **Apache NiFi**:
  - Interface Web: [http://localhost:8080/nifi](http://localhost:8080/nifi)

- **Elasticsearch**:
  - HTTP: [http://localhost:9200](http://localhost:9200)

## Arrêter tous les services

Pour arrêter tous les services, exécutez :

```bash
docker-compose down
```

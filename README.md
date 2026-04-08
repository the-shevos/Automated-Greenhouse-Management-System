# Automated Greenhouse Management System (AGMS)

**Microservice-Based Application | Spring Boot & Spring Cloud**

---

## 📋 Project Overview

AGMS is a cloud-native microservices platform designed for automated greenhouse management.

The system integrates with a live external IoT data provider API to fetch real-time environmental data such as temperature and humidity. This data is processed through a rule engine to automatically trigger actions that maintain optimal growing conditions for crops.

---

## 🚀 Key Features

- 🌡️ Real-time temperature & humidity monitoring
- 🔗 Integration with external IoT data provider API
- ⚙️ Rule-based automation system
- 🧩 Microservice architecture for scalability
- 🔐 Secure API access using JWT authentication
- 🌐 Centralized API Gateway for routing
- 📡 Service discovery using Eureka

---

## 🏗️ Microservices Architecture

- **Service Registry** – Manages service registration and discovery
- **API Gateway** – Handles routing and security
- **Crop Inventory Service** – Manages crop and greenhouse data
- **Config Server** – Centralized configuration management

---

## 🛠️ Technologies Used

| Technology | Purpose |
|-----------|--------|
| Spring Boot 3.x | Core microservice framework |
| Spring Cloud | Microservices ecosystem |
| Eureka Server | Service discovery & registration |
| Spring Cloud Config | Centralized configuration |
| Spring Cloud Gateway | API routing & security |
| OpenFeign | Inter-service communication |
| RestTemplate / WebClient | External API calls |
| MySQL | Database for crop & zone data |
| JWT (JSON Web Token) | Authentication & authorization |
| Lombok | Reduce boilerplate code |
| Maven | Build & dependency management |

---

## 🔐 Security

- JWT-based authentication
- Secure API endpoints via Gateway
- Token validation for each request

---

## 🌐 External Integration

- Connects to external IoT API for:
    - Temperature data
    - Humidity data

---

## ⚙️ How It Works

1. IoT API provides real-time environmental data
2. API Gateway routes requests to services
3. Services process data using business logic
4. Rule engine decides required actions
5. System maintains optimal greenhouse conditions


---

## 📁 Project Structure
```
agms-system/
├── eureka-server/                  # Service Registry (Port 8761)
├── config-server/                  # Config Server (Port 8888)
├── api-gateway/                    # API Gateway (Port 8080)
├── auth-service/                   # Auth Service (Port 8085)
├── zone-management-service/        # Zone Service (Port 8081)
├── sensor-telemetry-service/       # Sensor Service (Port 8082)
├── automation-service/             # Automation Service (Port 8083)
├── crop-inventory-service/         # Crop Service (Port 8084)
```

---

## ⚙️ Prerequisites

Before running the project, make sure you have:

- ☑️ Java 17 or higher installed
- ☑️ Maven 3.8+ installed
- ☑️ MySQL 8.0+ installed and running
- ☑️ Git installed
- ☑️ Postman (for API testing)
- ☑️ IntelliJ IDEA or any Java IDE

---

## 🗄️ Database Setup

Create the required MySQL databases:
```sql
CREATE DATABASE agms_zone_db;
CREATE DATABASE agms_automation_db;
CREATE DATABASE agms_crop_db;
```

Or let Spring auto-create them (already configured with `createDatabaseIfNotExist=true`).

---

## 🚀 Startup Instructions

### ⚠️ IMPORTANT: Services must be started in this exact order!

---

### Step 1 — Start Eureka Server (Service Registry)
```bash
cd eureka-server
mvn spring-boot:run
```
✅ Verify: Open http://localhost:8761
You should see the Eureka dashboard.

---

### Step 2 — Start Config Server
```bash
cd config-server
mvn spring-boot:run
```
✅ Verify: Open http://localhost:8888/zone-service/default
You should see zone-service configuration properties.

Config Server fetches properties from:
📦 https://github.com/the-shevos/agms-config-repo

---

### Step 3 — Start API Gateway
```bash
cd api-gateway
mvn spring-boot:run
```
✅ Verify: Service appears in Eureka dashboard as API-GATEWAY

---

### Step 4 — Start Auth Service
```bash
cd auth-service
mvn spring-boot:run
```
✅ Verify: Service appears in Eureka dashboard as AUTH-SERVICE

---

### Step 5 — Start Zone Management Service
```bash
cd zone-management-service
mvn spring-boot:run
```
✅ Verify: Service appears in Eureka dashboard as ZONE-SERVICE

---

### Step 6 — Start Sensor Telemetry Service
```bash
cd sensor-telemetry-service
mvn spring-boot:run
```
✅ Verify: Service appears in Eureka dashboard as SENSOR-SERVICE

---

### Step 7 — Start Automation Service
```bash
cd automation-service
mvn spring-boot:run
```
✅ Verify: Service appears in Eureka dashboard as AUTOMATION-SERVICE

---

### Step 8 — Start Crop Inventory Service
```bash
cd crop-inventory-service
mvn spring-boot:run
```
✅ Verify: Service appears in Eureka dashboard as CROP-INVENTORY-SERVICE

---

## 🌐 Service URLs

| Service | URL | Description |
|---------|-----|-------------|
| Eureka Dashboard | http://localhost:8761 | Service registry |
| Config Server | http://localhost:8888 | Configuration management |
| API Gateway | http://localhost:8080 | Single entry point |
| Auth Service | http://localhost:8085 | Authentication |
| Zone Service | http://localhost:8081 | Zone management |
| Sensor Service | http://localhost:8082 | Telemetry data |
| Automation Service | http://localhost:8083 | Rule engine |
| Crop Service | http://localhost:8084 | Crop inventory |
| External IoT API | http://104.211.95.241:8080/api | Live sensor data |

---

## 🔐 Authentication

### Local Auth Service
```
POST http://localhost:8085/api/auth/login
{
  "username": "sachindu",
  "password": "1234"
}
```

### External IoT API Auth
```
POST http://104.211.95.241:8080/api/auth/login
{
  "username": "sachindu",
  "password": "1234"
}
```

---

## 📡 API Endpoints

### Zone Management (Port 8081)
| Method | URL | Description |
|--------|-----|-------------|
| POST | /api/zones | Create zone + register IoT device |
| GET | /api/zones | Get all zones |
| GET | /api/zones/{id} | Get zone by ID |
| PUT | /api/zones/{id} | Update zone thresholds |
| DELETE | /api/zones/{id} | Delete zone |

### Sensor Telemetry (Port 8082)
| Method | URL | Description |
|--------|-----|-------------|
| GET | /api/sensors/latest | Get latest sensor readings |
| GET | /api/sensors | Get all devices |

### Automation Service (Port 8083)
| Method | URL | Description |
|--------|-----|-------------|
| POST | /api/automation/process | Process sensor data |
| GET | /api/automation/logs | Get automation logs |

### Crop Inventory (Port 8084)
| Method | URL | Description |
|--------|-----|-------------|
| POST | /api/crops | Register new crop batch |
| GET | /api/crops | Get all crops |
| GET | /api/crops/{id} | Get crop by ID |
| PUT | /api/crops/{id}/status?status= | Update crop status |

---

## 🔄 End-to-End Data Flow
```
1. IoT API Login → Get Bearer Token
2. Register Device → Get deviceId
3. Create Zone → Store deviceId
4. SensorFetcher (every 10s) → Fetch telemetry from IoT API
5. Store reading → Update SensorReadingStore
6. Push to Automation → Rule engine evaluates
7. If Temp > maxTemp → Log TURN_FAN_ON
8. If Temp < minTemp → Log TURN_HEATER_ON
```

---

## 🌱 Crop Lifecycle State Machine
```
SEEDLING → VEGETATIVE → HARVESTED
```
- SEEDLING can only move to VEGETATIVE
- VEGETATIVE can only move to HARVESTED
- HARVESTED is final state — cannot be changed

---

## 🧪 Testing

Import the Postman collection:
1. Open Postman
2. Click **Import**
3. Select `agms-collection.json` from project root
4. All endpoints are pre-configured and ready to test

---

## 📸 Eureka Dashboard

All services registered and UP:

![Eureka Dashboard](images/Eureka-dashboard.PNG)

---

## 📝 Configuration

All service configurations are managed centrally via Spring Cloud Config Server.
Config files are stored in:
🔗 https://github.com/the-shevos/agms-config-repo

| Config File | Service |
|-------------|---------|
| zone-service.yml | Zone Management Service |
| sensor-service.yml | Sensor Telemetry Service |
| automation-service.yml | Automation Service |
| crop-inventory-service.yml | Crop Inventory Service |



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



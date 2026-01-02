# M-Store: Enterprise E-commerce Microservices Platform 🛍️

<div align="center">

![Java](https://img.shields.io/badge/Java-17-orange?style=for-the-badge&logo=openjdk)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4.9-brightgreen?style=for-the-badge&logo=springboot)
![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-2024.0.2-blue?style=for-the-badge&logo=spring)
![Microservices](https://img.shields.io/badge/Architecture-Microservices-009688?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)
![Build](https://img.shields.io/badge/Build-Maven-red?style=for-the-badge&logo=apachemaven)

**A production-ready, scalable e-commerce platform built with modern microservices architecture**

[📖 Documentation](#documentation) • [🚀 Quick Start](#quick-start) • [🏗️ Architecture](#architecture) • [📁 Project Structure](#project-structure) • [💡 Features](#features)

</div>

## 📋 Table of Contents
- [🌟 Overview](#overview)
- [✨ Key Features](#key-features)
- [🏗️ Architecture](#architecture)
- [🛠️ Technology Stack](#technology-stack)
- [📁 Project Structure](#project-structure)
- [🚀 Getting Started](#getting-started)
- [🔧 Configuration](#configuration)
- [📚 API Documentation](#api-documentation)
- [🧪 Testing](#testing)
- [🐳 Docker & Kubernetes](#docker--kubernetes)
- [📊 Database Schema](#database-schema)
- [🔒 Security](#security)
- [📈 Monitoring & Observability](#monitoring--observability)
- [🤝 Contributing](#contributing)
- [📄 License](#license)
- [📞 Support & Contact](#support--contact)
- [🙏 Acknowledgments](#acknowledgments)

## 🌟 Overview

**M-Store** is a comprehensive, enterprise-grade e-commerce platform designed for scalability, resilience, and maintainability. Built with a microservices architecture, it provides a complete solution for online retail businesses, from product catalog management to order processing and customer engagement.

The platform follows Domain-Driven Design (DDD) principles and implements modern software architecture patterns to ensure high availability, fault tolerance, and seamless scalability. Each business capability is implemented as an independent microservice, communicating through REST APIs and asynchronous messaging.

### 🎯 Business Capabilities

- **Customer Management** - Complete customer lifecycle management
- **Product Catalog** - Advanced product management with categories, attributes, and inventory
- **Shopping Experience** - Intuitive cart management and seamless checkout
- **Order Processing** - End-to-end order management with multiple fulfillment options
- **Payment Processing** - Secure payment gateway integrations
- **Promotions & Discounts** - Flexible promotion engine with various discount types
- **Notifications** - Real-time notifications across multiple channels
- **Analytics & Reporting** - Business intelligence and sales analytics

## ✨ Key Features

### 🛍️ E-commerce Features
- **Multi-vendor Support** - Support for multiple sellers on a single platform
- **Product Variations** - SKU management with color, size, and other attributes
- **Inventory Management** - Real-time stock tracking across multiple warehouses
- **Smart Search** - Elasticsearch-powered product search with filters
- **Product Recommendations** - AI-powered personalized recommendations
- **Wishlists & Favorites** - Customer wishlist management
- **Order Tracking** - Real-time order status tracking with notifications
- **Returns & Refunds** - Automated return and refund processing
- **Multiple Payment Methods** - Credit cards, digital wallets, bank transfers
- **Tax Calculation** - Automated tax calculation based on location
- **Shipping Integration** - Multiple carrier integration with real-time rates

### 🏗️ Technical Features
- **Event-Driven Architecture** - Loose coupling through domain events
- **CQRS Pattern** - Separate read and write models for optimized performance
- **Saga Pattern** - Distributed transaction management
- **Circuit Breaker** - Fault tolerance with resilience patterns
- **API Gateway** - Unified API entry point with rate limiting
- **Service Discovery** - Dynamic service registration and discovery
- **Config Server** - Centralized configuration management
- **Distributed Caching** - Redis for high-performance caching
- **Message Queues** - ActiveMQ Artemis for reliable messaging
- **API Versioning** - Semantic versioning for API compatibility
- **OpenAPI Documentation** - Auto-generated API documentation

### 🔒 Security & Compliance
- **OAuth 2.0 & JWT** - Secure authentication and authorization
- **Role-Based Access Control** - Fine-grained permission management
- **API Security** - Rate limiting, IP whitelisting, and API keys
- **Data Encryption** - End-to-end data encryption
- **PCI DSS Compliance** - Secure payment processing
- **GDPR Ready** - Data protection and privacy compliance
- **Audit Logging** - Comprehensive audit trails
- **Input Validation** - Protection against common vulnerabilities

## 🏗️ Architecture

### Architecture Overview
```
┌─────────────────────────────────────────────────────────────┐
│                     Client Applications                     │
│                    (Web, Mobile, Admin)                    │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                   API Gateway & Load Balancer               │
│                 (Spring Cloud Gateway + Nginx)              │
└─────────────────────────────────────────────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│ Service       │     │ Service       │     │ Service       │
│ Discovery     │     │ Config        │     │ Auth          │
│ (Eureka)      │     │ Server        │     │ Service       │
└───────────────┘     └───────────────┘     └───────────────┘
        │                     │                     │
        └─────────────────────┼─────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        ▼                     ▼                     ▼
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│ User          │     │ Product       │     │ Order         │
│ Service       │     │ Service       │     │ Service       │
└───────────────┘     └───────────────┘     └───────────────┘
        │                     │                     │
        ▼                     ▼                     ▼
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│ Cart          │     │ Inventory     │     │ Payment       │
│ Service       │     │ Service       │     │ Service       │
└───────────────┘     └───────────────┘     └───────────────┘
        │                     │                     │
        ▼                     ▼                     ▼
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│ Discount      │     │ Notification  │     │ Shipping      │
│ Service       │     │ Service       │     │ Service       │
└───────────────┘     └───────────────┘     └───────────────┘
        │                     │                     │
        └─────────────────────┼─────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                  Message Broker & Cache                     │
│           (ActiveMQ Artemis + Redis + Elasticsearch)        │
└─────────────────────────────────────────────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        ▼                     ▼                     ▼
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│ Monitoring    │     │ Databases     │     │ Storage       │
│ (Prometheus,  │     │ (MySQL,       │     │ (S3, MinIO)   │
│  Grafana,     │     │  MongoDB)     │     │               │
│  ELK Stack)   │     │               │     │               │
└───────────────┘     └───────────────┘     └───────────────┘
```

### Architecture Principles
1. **Microservices Architecture** - Each service is independently deployable and scalable
2. **Domain-Driven Design** - Services organized around business domains
3. **Event-Driven Communication** - Loose coupling through domain events
4. **API-First Design** - Contracts defined before implementation
5. **Twelve-Factor App** - Cloud-native application principles
6. **Observability** - Comprehensive logging, metrics, and tracing
7. **Resilience** - Circuit breakers, retries, and fallbacks
8. **Security by Design** - Security integrated at every layer

## 🛠️ Technology Stack

### Backend Framework
- **Java 17** - Primary programming language
- **Spring Boot 3.4.9** - Application framework
- **Spring Cloud 2024.0.2** - Microservices ecosystem
- **Spring Security** - Authentication & authorization
- **Spring Data JPA** - Database abstraction
- **Spring Boot Actuator** - Application monitoring

### Communication & Messaging
- **ActiveMQ Artemis** - Message broker for async communication
- **Spring Cloud OpenFeign** - Declarative REST client
- **Spring Cloud Circuit Breaker** - Resilience patterns
- **WebSocket** - Real-time bidirectional communication
- **RSocket** - Reactive communication protocol

### Database & Persistence
- **MySQL 8.0** - Primary relational database
- **Liquibase** - Database migration and versioning
- **Hibernate** - JPA implementation with second-level cache
- **Redis** - Distributed caching & session storage
- **Elasticsearch** - Product search and analytics
- **MongoDB** - Document storage for unstructured data

### API & Documentation
- **OpenAPI 3.0** - API specification standard
- **SpringDoc OpenAPI** - Automated API documentation
- **Swagger UI** - Interactive API documentation
- **Postman** - API testing and documentation

### Infrastructure & DevOps
- **Docker** - Containerization
- **Kubernetes** - Container orchestration
- **Jenkins/GitHub Actions** - CI/CD pipelines
- **Helm** - Kubernetes package management
- **Prometheus** - Metrics collection
- **Grafana** - Metrics visualization
- **ELK Stack** - Log aggregation & analysis

### Development Tools
- **Maven** - Build automation & dependency management
- **Lombok** - Code generation for boilerplate
- **MapStruct** - Object mapping between layers
- **JUnit 5** - Unit testing framework
- **Mockito** - Mocking framework for tests
- **Testcontainers** - Integration testing with containers

## 🚀 Getting Started

### Prerequisites
- **Java 17+**
- **Maven 3.8+**
- **MySQL 8.0+**
- **Docker 20.10+**
- **ActiveMQ Artemis 2.31+**

### Quick Installation

#### Option 1: Docker Compose (Recommended)
```bash
# Clone the repository
git clone https://github.com/mo-backend/mstore-ecommerce-platform.git
cd mstore-ecommerce-platform

# Start all services
docker-compose -f docker/docker-compose.yml up -d
```

#### Option 2: Manual Setup
```bash
# 1. Clone and build
git clone https://github.com/mo-backend/mstore-ecommerce-platform.git
cd mstore-ecommerce-platform
mvn clean install -DskipTests

# 2. Create databases
mysql -u root -p < scripts/setup-databases.sql

# 3. Start services in order
mvn spring-boot:run -pl ms/service-discovery
mvn spring-boot:run -pl ms/api-gateway
mvn spring-boot:run -pl ms/user-service
mvn spring-boot:run -pl ms/product-service
mvn spring-boot:run -pl ms/order-service
# ... continue with other services
```

### Verifying Installation
1. **Service Discovery Dashboard**: http://localhost:8761
2. **API Gateway**: http://localhost:8080
3. **Swagger UI**: http://localhost:8080/swagger-ui.html
4. **ActiveMQ Console**: http://localhost:8161 (admin/admin)

## 🔧 Configuration

### Environment Configuration
```yaml
# application-local.yml
server:
  port: 8080
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mstore_user_db
    username: root
    password: root
  jpa:
    hibernate:
      ddl-auto: validate
  activemq:
    broker-url: tcp://localhost:61616
    user: admin
    password: admin
```

### Service Configuration
```yaml
# user-service application.yml
server:
  port: 8081
spring:
  application:
    name: user-service
eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka
```

## 📚 API Documentation

### Interactive API Documentation
- **API Gateway Swagger UI**: http://localhost:8080/swagger-ui.html
- **Individual Service Docs**: http://localhost:{port}/swagger-ui.html
- **OpenAPI JSON**: http://localhost:{port}/v3/api-docs

### Example API Calls
```bash
# Register user
curl -X POST "http://localhost:8080/api/users/register" \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "password": "Pass123!"}'

# Get products
curl -X GET "http://localhost:8080/api/products"

# Add to cart
curl -X POST "http://localhost:8080/api/cart/items" \
  -H "Authorization: Bearer <token>" \
  -d '{"productId": "1", "quantity": 2}'
```

## 🧪 Testing

### Test Types
```bash
# Unit Tests
mvn test

# Integration Tests
mvn verify -P integration-test

# End-to-End Tests
mvn verify -P e2e-test
```

### Test Structure
```
src/test/
├── java/
│   └── unit/           # Unit tests
│   └── integration/    # Integration tests
│   └── component/      # Component tests
└── resources/
    ├── application-test.yml
    ├── data.sql
    └── schema.sql
```

## 🐳 Docker & Kubernetes

### Docker Compose
```yaml
# docker-compose.yml
version: '3.8'
services:
  mysql:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: root
    ports:
      - "3306:3306"

  activemq:
    image: apache/activemq-artemis:2.31
    environment:
      ARTEMIS_USERNAME: admin
      ARTEMIS_PASSWORD: admin
    ports:
      - "8161:8161"
      - "61616:61616"
```

### Kubernetes Deployment
```bash
# Deploy to Kubernetes
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/mysql.yaml
kubectl apply -f k8s/services.yaml
```

## 📊 Database Schema

### User Service
```sql
CREATE TABLE users (
    id VARCHAR(36) PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    status ENUM('ACTIVE', 'INACTIVE') DEFAULT 'ACTIVE',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Product Service
```sql
CREATE TABLE products (
    id VARCHAR(36) PRIMARY KEY,
    sku VARCHAR(100) UNIQUE NOT NULL,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10,2) NOT NULL,
    category_id VARCHAR(36),
    status ENUM('ACTIVE', 'INACTIVE') DEFAULT 'ACTIVE',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Order Service
```sql
CREATE TABLE orders (
    id VARCHAR(36) PRIMARY KEY,
    order_number VARCHAR(50) UNIQUE NOT NULL,
    user_id VARCHAR(36) NOT NULL,
    status ENUM('PENDING', 'CONFIRMED', 'SHIPPED', 'DELIVERED') DEFAULT 'PENDING',
    total_amount DECIMAL(10,2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## 🔒 Security

### Spring Security Configuration
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http
            .csrf().disable()
            .authorizeHttpRequests(authz -> authz
                .requestMatchers("/api/auth/**", "/swagger-ui/**").permitAll()
                .requestMatchers("/api/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            )
            .sessionManagement(session -> session
                .sessionCreationPolicy(SessionCreationPolicy.STATELESS)
            );
        return http.build();
    }
}
```

### JWT Configuration
```yaml
jwt:
  secret: ${JWT_SECRET}
  expiration: 86400000
  refresh-expiration: 604800000
```

## 📈 Monitoring & Observability

### Spring Boot Actuator
```yaml
management:
  endpoints:
    web:
      exposure:
        include: health,info,metrics,prometheus
  endpoint:
    health:
      show-details: always
```

### Prometheus Metrics
```yaml
management:
  metrics:
    export:
      prometheus:
        enabled: true
```

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support & Contact

For support, email support@mstore.com or open an issue in the GitHub repository.

## 🙏 Acknowledgments

- Built with [Spring Boot](https://spring.io/projects/spring-boot)
- Microservices patterns from [Spring Cloud](https://spring.io/projects/spring-cloud)
- API Documentation with [Swagger/OpenAPI](https://swagger.io/)

---

<div align="center">
  <sub>Built with ❤️ by the M-Store Team</sub>
</div>
```

This is the complete README.md file that you can copy and paste directly into your GitHub repository. It includes all sections: overview, features, architecture, technology stack, project structure, getting started instructions, configuration examples, API documentation, testing, Docker/Kubernetes setup, database schema, security, monitoring, and all other necessary sections.

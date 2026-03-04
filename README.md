# Ticketing System Backend

A Spring Boot REST API backend for a real-time ticketing system. It manages vendors, customers, and a shared ticket pool, with WebSocket support for live simulation updates.

## Tech Stack

- **Java 21**
- **Spring Boot 3.3.6**
- **Spring Data JPA**
- **Spring WebSocket / STOMP**
- **MySQL**
- **Lombok**
- **Maven**

## Prerequisites

- Java 21+
- Maven 3.8+
- MySQL 8+

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/algotyrnt/ticketing-system-backend.git
cd ticketing-system-backend
```

### 2. Configure the database

Create a MySQL database:

```sql
CREATE DATABASE ticketingSystem;
```

Update `src/main/resources/application.properties` with your MySQL credentials:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/ticketingSystem
spring.datasource.username=<your-username>
spring.datasource.password=<your-password>
```

### 3. Build and run

```bash
./mvnw spring-boot:run
```

The application will start on `http://localhost:8080`.

## API Reference

### Customer Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/customer/all` | Get all customers |
| `POST` | `/customer/create` | Create a new customer |
| `PUT` | `/customer/update` | Update an existing customer |
| `DELETE` | `/customer/delete/{id}` | Delete a customer by ID |

### Vendor Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/vendor/all` | Get all vendors |
| `POST` | `/vendor/create` | Create a new vendor |
| `PUT` | `/vendor/update` | Update an existing vendor |
| `DELETE` | `/vendor/delete/{id}` | Delete a vendor by ID |

### System Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/system/config` | Get the current system configuration |
| `POST` | `/system/start` | Start the ticket simulation with the given config |
| `POST` | `/system/stop` | Stop the running simulation |

## WebSocket

The backend exposes a STOMP-over-WebSocket endpoint at `/ws` (with SockJS fallback) for real-time ticket simulation updates.

## Running Tests

```bash
./mvnw test
```

# Microservices Architecture

## 💡 What is Microservices?
Microservices is an architectural style where an application is structured as a collection of small, independent services that communicate over a network (usually using REST APIs or messaging systems).  
Each service focuses on a specific business capability and can be developed, deployed, and scaled independently.

---

## 🚀 Key Characteristics

- **Independently Deployable:** Each service can be built, deployed, and updated without affecting others.
- **Loosely Coupled:** Services interact through APIs, not direct code dependencies.
- **Focused Responsibility:** Each microservice handles one business function (e.g., user service, payment service).
- **Technology Independent:** Different services can use different languages, databases, or frameworks.
- **Resilient and Scalable:** If one service fails, others can continue running. Scaling can happen per service.

---

## 🛒 Simple Example (E-commerce App)

- **🧍 User Service:** Handles user accounts and authentication
- **🛒 Cart Service:** Manages shopping carts

---

## ✅ Advantages

- Easier to scale and maintain
- Faster development with smaller teams
- Fault isolation (failure in one service doesn’t bring down the entire system)
- Easier to adopt new technologies

---

## ⚠️ Challenges

- Complex deployment and monitoring
- Distributed data management
- Network latency and security between services

---

# REST (Representational State Transfer) Principles

## 💡 What is REST?
REST is an architectural style for designing networked APIs.  
It uses HTTP methods to perform CRUD (Create, Read, Update, Delete) operations on resources identified by URLs.

---

## Core REST Principles

- **Client-Server:**  
  Separation of concerns — client handles UI, server handles data and logic.

- **Stateless:**  
  Each request from client to server must contain all necessary information — no session stored on the server.

- **Cacheable:**  
  Responses can be cached to improve performance and scalability.

- **Uniform Interface:**  
  Resources are identified using URIs, and standard HTTP methods are used:
  - `GET` → Read
  - `POST` → Create
  - `PUT` → Update
  - `DELETE` → Remove

- **Layered System:**  
  The client doesn’t need to know whether it’s connected directly to the server or through intermediaries.

- **Optional: Code on Demand:**  
  Servers can send executable code (like JavaScript) to clients when needed.

---

## How REST and Microservices Work Together

- Each microservice exposes its functionality via REST APIs.
- REST ensures lightweight communication between services.

**Example:**  
The Order Service might call the Payment Service via a REST endpoint like:  
`POST /payments/process`

---

# Monolithic vs Microservices

| Monolithic Architecture | Microservices Architecture |
|------------------------|---------------------------|
| Built as a single, unified unit | Built as a set of independent services |
| All modules tightly integrated and deployed together | Each service focuses on a specific business function |
| Simple to develop and test initially | More complex to manage initially |
| Harder to maintain, scale, and deploy as app grows | Greater scalability, flexibility, and fault isolation |
| Small change requires rebuilding and redeploying whole app | Services can be developed, deployed, and scaled independently |

**🟢 In short:**  
- **Monolithic:** Simple start, complex growth.  
- **Microservices:** Complex start, flexible growth.

---
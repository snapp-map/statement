
# 📄 Project Statement – Snapp

## 🔹 General Description

You are going to design and implement a **large-scale backend application** inspired by modern platforms such as online taxi booking, food ordering, and logistics systems.

The project is named **Snapp** and is divided into **three main independent applications (microservice-based programs)**:

1.  **Snapp** → Taxi booking, parcel delivery, price estimation, and related services.
2.  **Map** → Location, routing, distance, and travel time calculation. 
3.  **Food** → Online food ordering and restaurant management.
    
Each of these applications should follow the **principles of software engineering** such as:

-   **OOP (Object-Oriented Programming)**
-   **SOLID** principles
-   **DRY (Don’t Repeat Yourself)**
-   **Design Patterns** (where applicable)
    

All code should be managed under a **GitHub Organization called [snapp-map](https://github.com/snapp-map)**. Each main program will have a **hub repository** (e.g., [snapp-hub](https://github.com/snapp-map/snapp-hub), [map-hub](https://github.com/snapp-map/map-hub), [food-hub](https://github.com/snapp-map/food-hub)). Inside these hubs, the actual microservices will be developed as **independent repositories** and linked as **submodules**.

### 🔹 Microservice Approach
-   Each microservice should be **independently deployable** and **self-contained**.
-   Services should communicate through **standard protocols** (HTTP REST, gRPC, message brokers, etc.).
-   Each service should have its **own database** (if needed).
-   The entire project must be designed as if it were to be **used in production** (professional level).

### 🔹 Third-party Systems
In addition to the three main applications, a few **smaller supporting programs** will be implemented for simulation purposes, such as:
-   **Bank service** (for payments and transactions)
-   **Email service** (for user notifications)
    

These will act like external systems but will be **locally implemented** in simplified form.

### 🔹 Authentication & Authorization
-   The user should **register only once**.
-   A **third-party authentication service** will handle login, registration, and authorization for all three main programs.
-   Each program (Snapp, Map, Food) should use this authentication service instead of implementing its own.
    

### 🔹 Phases of Development

The project will be divided into **multiple phases**, so that functionality grows step by step.

#### **Phase 1 – Core Snapp (Taxi/Parcel)**
-   Focus only on the **Snapp application**.
-   Users can register, log in, and request a ride or delivery.
-   Map outputs (route, ETA, price) should be mocked with **random but standard outputs**.
-   Microservices for Snapp must be independent and well-structured.
    

#### **Phase 2 – Map Integration**
-   Develop the **Map application**.
-   Replace mocked data in Snapp with real services from Map (distance, ETA, pricing).
-   Ensure Snapp and Map communicate correctly.
    

#### **Phase 3 – Food Service**
-   Develop the **Food application**.
-   Restaurants register and manage menus.
-   Customers order food.
-   Deliveries are handled via Snapp.
    

#### **Phase 4 – Auxiliary Services**
-   Add **banking service simulation** (transaction processing).
-   Add **email service simulation** (notifications, confirmations).
-   Ensure all three programs integrate with these external services.
    

#### **Phase 5 – Final Integration & Optimization**
-   Deploy all services as microservices with **Docker**.
-   Document APIs with **OpenAPI/Swagger**.
-   Ensure CI/CD pipelines for GitHub repositories.
-   Add optional features: analytics, monitoring, logging.


# 📄 Snapp – Project Statement

The **Snapp program** is the first and core component of the project. It is responsible for **ride booking, cargo delivery, driver management, and trip lifecycle operations**.  
This system will be developed as a **microservice-based program** with its own hub repository: **`snapp-hub`**.

Inside `snapp-hub`, each feature should be built as a separate microservice (independent repo + submodule).

----------

## 🎯 Core Roles

-   **Normal User (Passenger)** → Requests taxi or cargo.
    
-   **Driver User** → Registers vehicle, accepts/rejects trips.
    
-   **Support User** → Handles support messages only.
    
-   **Admin** → Manages users, drivers, trips, reports.
    
-   **GOD** → Special account that **creates admins** (cannot be created via API).
    

----------

## 🏗 Phases of Development

### **Phase 1 – Core System (MVP)**

Goal: Deliver the **minimal working product** as fast as possible.

1.  **Authentication & User Management**
    
    -   Register/Login with roles: passenger, driver, support, admin.
        
    -   GOD account is **hardcoded or seeded** in the system.
        
    -   Drivers must provide personal and vehicle info (capacity, type, etc.).
        
2.  **Trip Request (Passenger side)**
    
    -   Passenger submits trip request with origin & destination.
        
    -   System saves request in DB with status `PENDING`.
        
    -   Mock Map service → generate **fake but standard route data** (distance, ETA, price).
        
3.  **Trip Assignment (Driver side)**
    
    -   Request is sent to **nearest available drivers**.
        
    -   Driver can **accept or reject**.
        
    -   If no driver accepts in a fixed time, search area expands (until a maximum).
        
    -   If still unsuccessful → trip request marked as `FAILED`.
        
4.  **Trip Lifecycle**
    
    -   States: `REQUESTED → ACCEPTED → IN_PROGRESS → COMPLETED`.
        
    -   Completed trips update passenger & driver history.
        

✅ At the end of **Phase 1**, you have a functional ride-hailing system.

----------

### **Phase 2 – Pricing & Payment**

Goal: Introduce realistic ride pricing and payment flow.

1.  **Price Calculation**
    
    -   Base price + distance + time (mocked from Map).
        
    -   Peak hours / delayed trips discounts.
        
2.  **Commission Handling**
    
    -   At trip completion, system calculates total fare.
        
    -   Deduct commission (e.g., 20%) → add driver balance.
        
    -   At **end of each day**, driver earnings deposited.
        
3.  **Transaction Service (Bank Simulation)**
    
    -   Integrate with **Bank microservice** (stub for now).
        
    -   Store transaction history for passengers & drivers.
        

----------

### **Phase 3 – Extended Trip Features**

Goal: Add advanced ride types and trip flexibility.

1.  **Delayed Trips**
    
    -   Passenger can mark trip as **delayed** (not urgent).
        
    -   System groups delayed trips with similar routes.
        
    -   Discounted pricing for passengers.
        
2.  **Shared Trips (Non-Closed Trips)**
    
    -   Passenger can opt for **shared trip**.
        
    -   Other passengers can join mid-route.
        
    -   Fare is split between riders.
        

----------

### **Phase 4 – Communication & Feedback**

Goal: Improve user experience with interactions and ratings.

1.  **Messaging Service**
    
    -   In-app chat between passenger ↔ driver.
        
    -   Support messages (support role only).
        
2.  **Rating System**
    
    -   After trip completion, passenger rates driver.
        
    -   Driver can also rate passenger.
        
    -   Ratings affect reputation score.
        

----------

### **Phase 5 – Integration with Map**

Goal: Replace mocked map data with **real Map microservice**.

1.  Request route, ETA, and fuel consumption from **Map program**.
    
2.  Store results in trip details.
    
3.  Adjust pricing logic accordingly.
    

----------

## 📌 Priorities

-   **Phase 1** is **mandatory** and should be completed first (to have a working prototype).
    
-   **Phases 2–5** are **incremental enhancements**. Each team can decide how many advanced features to add, depending on time and skill.


# 📄 MAP – Project Statement

The **MAP program** is responsible for handling **location-based services**, including routing, traffic estimation, energy consumption, and cost calculations. It will be developed under the **`map-hub`** repository, following the same microservice architecture as Snapp.

Its outputs will be used by other programs (Snapp for ride pricing and Food for delivery routes).

----------

## 🎯 Core Responsibilities of MAP

1.  **Shortest Route Calculation** → Given origin and destination, return the best route.
    
2.  **Traffic Modeling** → Estimate traffic conditions dynamically based on usage data (number of active vehicles using Snapp/Food).
    
3.  **Energy Consumption Estimation** → Predict energy/fuel usage considering distance, slope, and traffic.
    
4.  **ETA & Pricing Support** → Provide estimated travel time and support Snapp in fare calculation.
    

----------

## 🏗 Phases of Development

### **Phase 1 – MVP (Minimum Viable Product)**

Goal: Deliver a simple but functional version quickly.

1.  **Basic Routing**
    
    -   Given start & end coordinates, return a simple path.
        
    -   For MVP, use a simplified **graph representation** (nodes = intersections, edges = roads).
        
    -   Return distance and estimated time (using average fixed speed).
        
2.  **Mock Energy Calculation**
    
    -   Assume a fixed consumption rate per km.
        
    -   Return approximate fuel/energy usage.
        
3.  **Basic API Endpoints**
    
    -   `POST /route` → Input: origin, destination → Output: route (list of points), distance, ETA, energy.
        

✅ At the end of **Phase 1**, Snapp can request a route and pricing support with standard but mocked results.

----------

### **Phase 2 – Traffic Simulation**

Goal: Make routing more realistic.

1.  **Traffic Model**
    
    -   Collect the number of **active vehicles from Snapp** (via API or message broker).
        
    -   Define traffic density rules (e.g., >100 vehicles in area = slower speed).
        
2.  **Dynamic ETA**
    
    -   Adjust travel time according to traffic.
        
    -   Update routes with **slow/medium/heavy traffic categories**.
        
3.  **API Update**
    
    -   Return ETA and adjusted route cost based on live traffic.
        

----------

### **Phase 3 – Advanced Energy & Cost Estimation**

Goal: Improve realism of energy/fuel calculation.

1.  **Slope-aware Calculation**
    
    -   Add elevation data to routes (can be mocked for MVP).
        
    -   Energy consumption increases on uphill slopes, decreases on downhill.
        
2.  **Traffic-aware Energy Use**
    
    -   Higher energy consumption in heavy traffic (idling, stop-go).
        
3.  **Vehicle Type Profiles**
    
    -   Different models for car, motorcycle, cargo van.
        
    -   Each has different base consumption rates.
        

----------

### **Phase 4 – Optimized Routing & Algorithms**

Goal: Deliver production-quality map features.

1.  **Shortest vs Fastest Route**
    
    -   Allow user to choose between minimizing distance or time.
        
    -   Implement algorithms like __Dijkstra / A_ Search_*.
        
2.  **Alternative Routes**
    
    -   Provide multiple possible routes with trade-offs (shorter but more traffic, longer but faster).
        
3.  **Scalability**
    
    -   Cache frequently requested routes.
        
    -   Optimize graph storage and queries.
        

----------

### **Phase 5 – Integration & Expansion**

Goal: Complete professional integration with the rest of the ecosystem.

1.  **Integration with Snapp**
    
    -   Provide real-time routes, ETA, and pricing support.
        
    -   Feed Snapp traffic data to improve matching drivers ↔ passengers.
        
2.  **Integration with Food**
    
    -   Provide delivery optimization for multiple stops (restaurant → multiple customers).
        
3.  **Analytics & Reports**
    
    -   Store historical traffic data.
        
    -   Generate insights like busiest areas, peak hours.
        

----------

## 📌 Priorities

-   **Phase 1 (MVP)** must be implemented first → basic route, ETA, and energy.
-   **Phase 2–3** introduce realism (traffic + energy models).
-   **Phase 4–5** add professional-level features for optimization and integration.

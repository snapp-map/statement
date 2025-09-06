
# 📘 Snapp Project – Collaboration Workflow

Welcome to the **Snapp Project** 🎉  
This document defines how all contributors should **develop, collaborate, and maintain** the ecosystem of Snapp, Map, Food, and supporting services.

----------

## 🔹 1. Repository Structure

The project is divided into **hubs**. Each hub is a GitHub repo under the `snapp-map` organization.  
Microservices live as **separate repos** and are added as **submodules** into the hub repo.

```bash
snapp-map/
├── snapp-hub/ # Taxi & parcel platform │   ├── snapp-user-service
│   ├── snapp-driver-service
│   ├── snapp-trip-service
│   └── ...
│
├── map-hub/ # Routing & geolocation platform │   ├── map-routing-service
│   ├── map-traffic-service
│   └── ...
│
├── food-hub/ # Marketplace platform │   ├── food-store-service
│   ├── food-order-service
│   └── ...
│
├── bank-service/ # Banking mini-program ├── email-service/ # Email mini-program └── contracts/ # Shared API specs (OpenAPI, gRPC, schemas)
```
----------

## 🔹 2. Branching Model

We use **GitHub Flow** with clear rules:

-   `main` → Stable production-ready code.
    
-   `dev` → Integration branch for new features.
    
-   `feature/<name>` → Feature work (e.g., `feature/trip-matching`).
    
-   `hotfix/<name>` → Quick fixes for production issues.
    

### ✅ Workflow

1.  Create a branch from `dev`.
    
2.  Commit changes (small, frequent commits preferred).
    
3.  Open a Pull Request (PR) into `dev`.
    
4.  Request review from **at least 1 teammate**.
    
5.  After merge, CI/CD will deploy automatically to staging.
    
6.  Approved PRs to `main` = production deployment.
    

----------

## 🔹 3. Commit Rules

-   Use **conventional commits**:
    
```makefile
feat: add trip request API
fix: correct driver assignment bug
docs: update API usage in README
test: add unit tests for routing service
```
    
-   Keep commits **small and focused**.
    
-   Write descriptive commit messages.
    

----------

## 🔹 4. Code Reviews

-   Every PR must be reviewed by **1–2 members** before merging.
    
-   Use GitHub’s **Review → Comment → Approve** workflow.
    
-   Be respectful & constructive.
    
-   Large PRs should be broken into smaller chunks.
    

----------

## 🔹 5. Development Setup

### Local Development

-   Each service must provide a **Dockerfile**.
    
-   The hub repo must provide a **docker-compose.yml** for local startup.
    
-   Run:
	```bash
	docker-compose up
	```
    
    to spin up all services locally.
    

### Hot Reload

-   **Java (Spring Boot)** → Spring DevTools.
    
-   **Node.js** → Nodemon.
    
-   **Python (FastAPI/Flask)** → uvicorn with reload.
    
-   **Go** → Compile-watch scripts.
    

----------

## 🔹 6. Testing

-   **Unit Tests** → Run per service (`pytest`, `JUnit`, `jest`, `go test`).
    
-   **Integration Tests** → Use docker-compose + `testcontainers`.
    
-   **Contract Tests** → Validate service API contracts against `contracts/`.
    

CI/CD will fail PRs that do not pass tests. ✅

----------

## 🔹 7. CI/CD Pipeline

Each repo must include a `.github/workflows/ci.yml` with stages:

1.  **Lint** → Check formatting & style.
    
2.  **Test** → Run unit & integration tests.
    
3.  **Build** → Build docker image.
    
4.  **Deploy** → Push image to registry, deploy to staging.
    

Optional: require **manual approval** for production deploys.

----------

## 🔹 8. Documentation

-   Every service must include:
    
    -   `README.md` (setup, usage, contributors).
        
    -   API documentation (Swagger/OpenAPI, gRPC `.proto`).
        
-   API definitions should live in the **contracts repo**.
    
-   Services must keep documentation **up to date** with code.
    

----------

## 🔹 9. Communication Between Services

We support two approaches:

1.  **Direct API calls** (REST or gRPC).
    
2.  **Shared libraries (recommended)** → Each hub can publish a small SDK/wrapper library (e.g., `snapp-sdk`, `map-sdk`) for easier integration.
    

Optional: Use **message broker (Kafka/RabbitMQ)** for event-driven communication (`trip_requested`, `order_completed`, `payment_done`).

----------

## 🔹 10. Collaboration Rules

-   Weekly **sync meetings** (short status check).
    
-   Each hub has its **own Slack/Discord channel**.
    
-   Architecture decisions recorded as **ADR files** in Markdown.
    
-   All diagrams & designs stored in a shared **Notion/Confluence space**.
    

----------

## 🔹 11. Optional Features (for advanced teams)

-   **Analytics Dashboards** (Grafana/Metabase).
    
-   **Monitoring & Alerts** (Prometheus, ELK Stack).
    
-   **Professional Logging** (structured logs, log aggregation).
    
-   **AI Features**
    
    -   Demand prediction for Snapp.
        
    -   Route optimization in Map.
        
    -   Product recommendations in Food.
        

These are **not mandatory**, but highly encouraged for teams aiming at extra credit or advanced experience.

----------

## 🔹 12. Quality Standards

-   Follow **SOLID, DRY, KISS** principles.
    
-   Use **linters/formatters**:
    
    -   Java → Checkstyle.
        
    -   Python → Black/Flake8.
        
    -   Node.js → ESLint/Prettier.
        
    -   Go → golangci-lint.
        
-   Each repo should have a `.editorconfig` for consistent style.
    

----------

## 🔹 13. Team Roles

-   Each microservice has **one main owner** + reviewers.
    
-   Cross-hub tasks (CI/CD, contracts, monitoring) are **joint responsibility**.
    
-   Encourage **pair programming** and **knowledge sharing** between language groups.

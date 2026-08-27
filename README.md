# Config Repository - MedPortal

## Student Information
* **Student Name:** Dilini Chamika Silva
* **Student Number:** 241711097
* **GCP Project ID:** project-905bd1ab-9262-4481-a92

## Project Description
The **Config Repository** is the centralized git-based configuration store for the MedPortal Enterprise Cloud Architecture. It holds the externalized property files (`application.yml` or service-specific properties) for all microservices, allowing configuration changes to be managed dynamically without modifying or rebuilding the application source code.

---

## Service-Specific Configurations & Architecture Rationale

### 1. API Gateway (`application.yml`)
* **Port:** `8080`
* **Why we use it:** Acts as the single entry point for all client requests. It handles dynamic routing to downstream microservices using Spring Cloud Gateway and manages global CORS configurations to safely accept requests from the frontend (Vercel & Load Balancer IPs) while integrating with Eureka for service discovery.

### 2. Appointment Service (`appointment-service.properties`)
* **Port:** `8081`
* **Why we use it:** Manages doctors, patients, and appointment scheduling. It connects to a relational database (**Cloud SQL MySQL**) using Spring Data JPA for persistent transactional storage and registers with the Eureka Server for dynamic service lookup.

### 3. Clinical Records Service (`clinical-records.properties`)
* **Port:** `8082`
* **Why we use it:** Handles patient medical records and clinical notes. It utilizes a non-relational document database (**MongoDB Atlas**) to store flexible medical history schemas efficiently, fulfilling the mandatory polyglot persistence requirement.

### 4. Lab Reports Service (`lab-reports.properties`)
* **Port:** `8083`
* **Why we use it:** Manages lab report metadata in a MySQL database while integrating directly with **Google Cloud Storage (GCS Buckets)** (`medportal-lab-reports-bucket`) to securely store and retrieve uploaded report files, fulfilling the mandatory cloud storage requirement.

---

## Setup & Getting Started Instructions

Clone the repository:
   ```bash
   git clone https://github.com/dilinichamikasilva/medportal-config-repo.git
   ```
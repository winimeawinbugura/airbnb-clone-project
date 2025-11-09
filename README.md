🏠 # Airbnb Clone Project

## airbnb-clone-project
This is a project about an Airbnb platform and its associated benefits

Project Overview

The Airbnb Clone Project is a comprehensive, real-world application designed to simulate the development of a booking platform like Airbnb. It focuses on backend development, database design, API creation, and security implementation while mirroring real-world team collaboration.

Project Goals

- Develop a scalable backend architecture.
- Understand team-based software development using GitHub.
- Design and implement a relational database with MySQL.
- Build secure APIs and integrate them with frontend components.
- Apply CI/CD best practices for automated deployment.


Tech Stack

- Backend Framework: Django
- Database: MySQL
- API Development: GraphQL / REST
- Containerization & Deployment: Docker, GitHub Actions
- Version Control: Git & GitHub





 


## Team Roles

This project follows common software development team roles to ensure clear responsibilities and efficient collaboration. The descriptions below combine the roles mentioned in the project overview with standard responsibilities from industry best practices.

### Product Owner
Defines product vision and priorities, collects stakeholder requirements, and approves major deliverables. Acts as the main point of contact for product decisions and feature prioritization.

### Project Manager / Scrum Master
Coordinates schedules, milestones, and team communication. Ensures the team follows agreed processes (e.g., Scrum), removes blockers, and tracks progress against delivery goals.

### Business Analyst (BA)
Gathers and documents business requirements, translates stakeholder needs into detailed functional requirements and user stories, and helps validate solutions against business goals.

### Software Architect
Designs the overall system architecture, defines high-level components and their interactions, selects core technologies and patterns, and ensures scalability, maintainability, and security of the design.

### Backend Developer
Implements server-side logic, builds APIs (REST/GraphQL), enforces business rules, integrates with the database and external services, and writes automated tests for backend functionality.

### Database Administrator (DBA)
Designs and manages the relational database (MySQL), defines schemas and relationships, optimizes queries and indexes, ensures backups, and maintains data integrity and security.

### DevOps / CI-CD Engineer
Configures infrastructure-as-code, containerization (Docker), and CI/CD pipelines (e.g., GitHub Actions). Responsible for automated builds, deployments, environment provisioning, and monitoring.

### QA Engineer / Test Engineer
Designs and runs manual and automated tests to validate functionality, performance, and security. Creates test plans, reports bugs, and verifies fixes to ensure release quality.

### UI/UX Designer (if included)
Designs user flows, wireframes, and visual mocks to ensure the product is usable and accessible. Works closely with frontend and product to translate designs into implementable components.

### Security Engineer (or Security-conscious DevOps)
Defines and enforces API security measures (authentication, authorization, input validation, secure storage of secrets), performs threat modeling, and guides secure coding best practices.







## Technology Stack

The Airbnb Clone Project integrates multiple technologies to simulate the development of a scalable, production-ready booking platform. Each component of the stack contributes to building a reliable, secure, and efficient system.

### 1. Django
A high-level Python web framework used for building robust backend systems. Django simplifies API creation, handles authentication, and manages server-side logic efficiently.

### **2. MySQL**
A powerful open-source relational database management system (RDBMS) used to store structured data such as user profiles, property listings, and booking transactions. MySQL ensures data consistency and supports complex queries.

### **3. GraphQL**
An API query language that enables clients to request exactly the data they need, reducing over-fetching and improving application performance. It enhances communication between the backend and frontend.

### **4. Docker**
A containerization platform that packages applications and dependencies into lightweight, portable containers. Docker ensures consistent deployment across different environments and simplifies development workflows.

### **5. Git & GitHub**
Version control and collaboration tools that enable distributed development. Git tracks code changes, while GitHub facilitates collaboration, code review, and CI/CD integration.

### **6. GitHub Actions (CI/CD)**
A continuous integration and delivery platform that automates testing, builds, and deployment. It ensures each code update is validated before merging into the production branch.

### **7. RESTful APIs**
A standardized architecture style for designing scalable web services. It allows communication between the backend and other systems using HTTP methods and structured responses.

### **8. HTML, CSS, JavaScript**
Frontend technologies (optional extension) used for building and styling the user interface. They help create interactive, responsive components that connect to backend APIs.

### **9. Security Tools**
A combination of authentication, authorization, and encryption mechanisms used to protect user data, manage access control, and ensure secure transactions throughout the system.



**Summary**
This stack ensures that the Airbnb Clone Project achieves modularity, scalability, and maintainability while aligning with real-world industry standards for backend and full-stack applications.




Added Technology Stack section with explanations for each technology

Added initial README.md with project overview and tech stack






## Database Design

The database for the Airbnb Clone Project follows a **relational model** using **MySQL**. It ensures data integrity, supports complex relationships, and maintains scalability for growing data.  

The key entities in the system include **Users**, **Properties**, **Bookings**, **Reviews**, and **Payments**.

---

### **1. Users**
**Description:** Stores information about individuals using the platform (both hosts and guests).  
**Key Fields:**
- `id` (Primary Key) — Unique identifier for each user  
- `name` — Full name of the user  
- `email` — Used for authentication and communication  
- `role` — Defines whether the user is a host or a guest  
- `date_joined` — Timestamp of when the account was created  

---

### **2. Properties**
**Description:** Contains details about each property listed on the platform.  
**Key Fields:**
- `id` (Primary Key) — Unique identifier for each property  
- `user_id` (Foreign Key) — References the user (host) who owns the property  
- `title` — Property name or listing title  
- `location` — City or region where the property is located  
- `price_per_night` — Cost to rent the property per night  

---

### **3. Bookings**
**Description:** Records transactions when a guest books a property.  
**Key Fields:**
- `id` (Primary Key) — Unique booking identifier  
- `user_id` (Foreign Key) — References the guest making the booking  
- `property_id` (Foreign Key) — References the booked property  
- `check_in` — Start date of the booking  
- `check_out` — End date of the booking  

---

### **4. Reviews**
**Description:** Stores feedback left by guests after completing their stay.  
**Key Fields:**
- `id` (Primary Key) — Unique identifier for each review  
- `user_id` (Foreign Key) — References the guest who left the review  
- `property_id` (Foreign Key) — References the reviewed property  
- `rating` — Numeric rating (e.g., 1–5 stars)  
- `comment` — Text feedback from the guest  

---

### **5. Payments**
**Description:** Tracks financial transactions related to bookings.  
**Key Fields:**
- `id` (Primary Key) — Unique identifier for each payment  
- `booking_id` (Foreign Key) — References the booking being paid for  
- `amount` — Total amount paid  
- `payment_method` — e.g., card, PayPal, or mobile money  
- `status` — Payment status (e.g., Pending, Completed, Failed)  

---

### **Entity Relationships**
- A **User** can own multiple **Properties**.  
- A **Property** can have many **Bookings**.  
- A **Booking** belongs to one **User** (guest) and one **Property**.  
- A **Booking** has one related **Payment** record.  
- A **Property** can have multiple **Reviews**, each left by different **Users**.  

---

### **Database Model Summary**
| Entity | Primary Key | Key Relationships |
|:-------|:-------------|:------------------|
| Users | id | 1 → Many Properties, 1 → Many Bookings, 1 → Many Reviews |
| Properties | id | Many → 1 User, 1 → Many Bookings, 1 → Many Reviews |
| Bookings | id | Many → 1 Property, Many → 1 User, 1 → 1 Payment |
| Reviews | id | Many → 1 Property, Many → 1 User |
| Payments | id | 1 → 1 Booking |

---

### 🗺️ Entity Relationship Diagram (ERD)

Below is the visual representation of the database structure used in the Airbnb Clone Project:

![Airbnb Clone ERD](https://github.com/winimeawinbugura/airbnb-clone-project/blob/main/erd-diagram.png)


This database design ensures **referential integrity** and supports **efficient data retrieval** for key operations like searching listings, managing bookings, and processing payments.

Added Database Design section with entities, fields, and relationships



# Project Requirements Document: OneNationRide App

## 1. User Roles and System Actors

### Core User Roles

- Ride Requester (Customer)
- Car Owner (Driver)
- Admin
- External Systems (Payment Gateway, Maps Service, etc.)

## 2. Functional Requirements

### 2.1 User Management and Authentication

| Requirement ID | Category       | User Role | Description               | Expected Behavior/Outcome                     | Backend Implementation                                |
| -------------- | -------------- | --------- | ------------------------- | --------------------------------------------- | ----------------------------------------------------- |
| FR001.1        | Authentication | All Users | Phone number registration | System validates phone number and sends OTP   | Firebase Authentication with SMS verification         |
| FR001.2        | Authentication | All Users | Email verification        | Secondary email verification after phone auth | Custom email verification service with templates      |
| FR001.3        | Authentication | All Users | Session management        | Maintain secure user sessions with JWT        | JWT token generation and validation middleware        |
| FR001.4        | Authentication | Car Owner | Driver verification       | Document upload and verification process      | Cloud Storage for documents, admin verification queue |

### 2.2 Profile and Account Management

| Requirement ID | Category | User Role | Description              | Expected Behavior/Outcome                    | Backend Implementation                             |
| -------------- | -------- | --------- | ------------------------ | -------------------------------------------- | -------------------------------------------------- |
| FR002.1        | Profile  | All Users | Basic profile creation   | Store user details with role-specific fields | Firestore users collection with role-based schemas |
| FR002.2        | Profile  | Car Owner | Vehicle management       | CRUD operations for vehicle information      | Separate vehicles collection with owner references |
| FR002.3        | Profile  | All Users | Profile verification     | Identity verification status tracking        | Background job for verification checks             |
| FR002.4        | Settings | All Users | Notification preferences | Manage push and email notifications          | FCM token management and notification service      |

### 2.3 Ride Management System

| Requirement ID | Category | User Role      | Description              | Expected Behavior/Outcome          | Backend Implementation                               |
| -------------- | -------- | -------------- | ------------------------ | ---------------------------------- | ---------------------------------------------------- |
| FR003.1        | Rides    | Car Owner      | Create ride listing      | Store ride details with validation | Firestore rides collection with geolocation indexing |
| FR003.2        | Rides    | Car Owner      | Ride schedule management | CRUD operations for ride schedules | Scheduled tasks for ride status updates              |
| FR003.3        | Rides    | Ride Requester | Search available rides   | Filter and sort ride listings      | Geospatial queries and search indexing               |
| FR003.4        | Rides    | All Users      | Real-time ride tracking  | Live location updates during ride  | Real-time location updates via Firebase RTDB         |

### 2.4 Booking and Payment System

| Requirement ID | Category | User Role      | Description           | Expected Behavior/Outcome          | Backend Implementation                    |
| -------------- | -------- | -------------- | --------------------- | ---------------------------------- | ----------------------------------------- |
| FR004.1        | Booking  | Ride Requester | Initiate booking      | Create booking with pending status | Transaction-based booking creation        |
| FR004.2        | Booking  | Car Owner      | Booking management    | Accept/reject booking requests     | State machine for booking status          |
| FR004.3        | Payment  | Ride Requester | Process payment       | Secure payment transaction         | Payment gateway integration with webhooks |
| FR004.4        | Payment  | Car Owner      | Earnings distribution | Automatic earnings calculations    | Scheduled payout processing               |

### 2.5 Communication System

| Requirement ID | Category      | User Role | Description        | Expected Behavior/Outcome        | Backend Implementation                      |
| -------------- | ------------- | --------- | ------------------ | -------------------------------- | ------------------------------------------- |
| FR005.1        | Messaging     | All Users | Real-time chat     | Message exchange between parties | Firebase RTDB for chat messages             |
| FR005.2        | Notifications | All Users | Push notifications | Event-based notifications        | FCM integration with notification templates |
| FR005.3        | Support       | All Users | Customer support   | Ticket creation and management   | Support ticket tracking system              |

### 2.6 Safety and Security

| Requirement ID | Category | User Role | Description       | Expected Behavior/Outcome      | Backend Implementation           |
| -------------- | -------- | --------- | ----------------- | ------------------------------ | -------------------------------- |
| FR006.1        | Safety   | All Users | Emergency alert   | SOS signal processing          | High-priority notification queue |
| FR006.2        | Safety   | All Users | Location tracking | Regular location updates       | Geolocation tracking service     |
| FR006.3        | Security | All Users | Fraud detection   | Suspicious activity monitoring | ML-based fraud detection system  |

### 2.7 Rating and Review System

| Requirement ID | Category | User Role | Description      | Expected Behavior/Outcome     | Backend Implementation       |
| -------------- | -------- | --------- | ---------------- | ----------------------------- | ---------------------------- |
| FR007.1        | Feedback | All Users | Post-ride rating | Rating submission and storage | Rating aggregation system    |
| FR007.2        | Feedback | All Users | Written reviews  | Review moderation             | Content moderation service   |
| FR007.3        | Metrics  | All Users | User reputation  | Calculate user trust scores   | Reputation scoring algorithm |

### 2.8 Admin Control Panel

| Requirement ID | Category | User Role | Description         | Expected Behavior/Outcome         | Backend Implementation           |
| -------------- | -------- | --------- | ------------------- | --------------------------------- | -------------------------------- |
| FR008.1        | Admin    | Admin     | User management     | CRUD operations for user accounts | Admin API with role-based access |
| FR008.2        | Admin    | Admin     | Content moderation  | Review and moderate content       | Content moderation queue         |
| FR008.3        | Admin    | Admin     | Analytics dashboard | Real-time system metrics          | Analytics data aggregation       |
| FR008.4        | Admin    | Admin     | Support management  | Handle user support tickets       | Support ticket assignment system |

### 2.9 Data Analytics and Reporting

| Requirement ID | Category  | User Role | Description         | Expected Behavior/Outcome     | Backend Implementation         |
| -------------- | --------- | --------- | ------------------- | ----------------------------- | ------------------------------ |
| FR009.1        | Analytics | Admin     | Usage analytics     | Track system usage metrics    | Analytics event processing     |
| FR009.2        | Analytics | Admin     | Financial reports   | Generate financial statements | Automated report generation    |
| FR009.3        | Analytics | Admin     | Performance metrics | Monitor system performance    | Performance monitoring service |

## 3. External System Integration Requirements

| Requirement ID | System                | Purpose            | Integration Points                                  |
| -------------- | --------------------- | ------------------ | --------------------------------------------------- |
| EX001          | Payment Gateway       | Payment Processing | Payment authorization, settlement, refunds          |
| EX002          | Maps Service          | Location Services  | Route planning, ETA calculation, real-time tracking |
| EX003          | SMS/Email Provider    | Communications     | Notifications, verification codes, alerts           |
| EX004          | Identity Verification | User Verification  | Document verification, background checks            |

## 4. Non-Functional Requirements

| Requirement ID | Category     | Description                                               |
| -------------- | ------------ | --------------------------------------------------------- |
| NFR001         | Performance  | App response time < 3 seconds                             |
| NFR002         | Scalability  | Support for 10,000+ concurrent users                      |
| NFR003         | Security     | End-to-end encryption for sensitive data                  |
| NFR004         | Availability | 99.9% uptime guarantee                                    |
| NFR005         | Compliance   | GDPR and local data protection regulations and compliance |

## 5. Security Requirements

| Requirement ID | Description         | Implementation                    |
| -------------- | ------------------- | --------------------------------- |
| SR001          | User Authentication | Multi-factor authentication       |
| SR002          | Data Protection     | Encryption at rest and in transit |
| SR003          | Payment Security    | PCI DSS compliance                |
| SR004          | Access Control      | Role-based access control (RBAC)  |

## 6. Technical Requirements

| Requirement ID | Component  | Specification               |
| -------------- | ---------- | --------------------------- |
| TR001          | Mobile App | Android (Kotlin)            |
| TR002          | Backend    | Firebase                    |
| TR003          | Database   | Cloud Firestore             |
| TR004          | API        | RESTful APIs with OAuth 2.0 |

---

# Note: the technology stack and TR are not fully decided, after the complete system desgin we will be in a position to decide the technology stack.

system design

**Version:** 2.0 (April 30, 2025)

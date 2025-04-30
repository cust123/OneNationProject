# Software Requirements Specification (SRS) - OneNationRide MVP

## 1. Introduction

This document outlines the essential features and requirements for the Minimum Viable Product (MVP) of the OneNationRide application, targeting completion by August 2025.

## 2. System Overview

OneNationRide MVP is an intercity/intracity ride-sharing application developed for Android using Kotlin and Firebase as the backend infrastructure.

## 🎯 MVP Feature Set

### 🚘 Ride Creation & Discovery (Core)

- Create ride offer: source, destination, date/time, seats, price, preferences.
- Search rides: filter by location, date, available seats, and date.
- Ride details page: driver info, vehicle details, booking button.

### 👥 Booking & Management

- Book/request a ride (real-time seat availability).
- Manage upcoming and past bookings.
- Cancel booking (basic logic).

### 💬 In-App Chat (Post Booking)

- Lightweight chat via Firebase (Firestore or Realtime DB).
- Chat available only after confirmed booking.

### ⭐ Ratings & Reviews

- Rate driver and passenger after the ride (1–5 stars + optional comment).
- Basic rating visible on profile.

## 🔐 Essential Components

- Firebase Authentication (phone-based login).
- User Profiles (passenger & driver roles, car info, profile photo).
- Firebase Firestore (NoSQL DB) + Cloud Functions.
- Google Maps API for location services.

## 3. Core MVP Requirements

### 3.1 Authentication & User Profile Management

| Requirement ID | Category       | User Role | Description                 | Expected Behavior/Outcome                   | Backend Implementation           |
| -------------- | -------------- | --------- | --------------------------- | ------------------------------------------- | -------------------------------- |
| MVP-AUTH-001   | Authentication | All Users | Phone number authentication | Verify user's phone number via Firebase OTP | Firebase Authentication          |
| MVP-AUTH-002   | Profile        | All Users | Basic profile creation      | Store essential user information            | Firestore users collection       |
| MVP-AUTH-003   | Profile        | Driver    | Vehicle information         | Store and validate vehicle details          | Firestore vehicles subcollection |

### 3.2 Ride Management System

| Requirement ID | Category | User Role | Description         | Expected Behavior/Outcome              | Backend Implementation             |
| -------------- | -------- | --------- | ------------------- | -------------------------------------- | ---------------------------------- |
| MVP-RIDE-001   | Rides    | Driver    | Create ride listing | Store ride details with location data  | Firestore rides collection         |
| MVP-RIDE-002   | Search   | Passenger | Search rides        | Filter by location, date, and seats    | Geospatial queries in Firestore    |
| MVP-RIDE-003   | Rides    | All Users | View ride details   | Display comprehensive ride information | Real-time data sync with Firestore |

### 3.3 Booking System

| Requirement ID | Category | User Role | Description          | Expected Behavior/Outcome       | Backend Implementation                 |
| -------------- | -------- | --------- | -------------------- | ------------------------------- | -------------------------------------- |
| MVP-BOOK-001   | Booking  | Passenger | Request booking      | Create pending booking request  | Transaction-based booking creation     |
| MVP-BOOK-002   | Booking  | Driver    | Manage bookings      | Accept/reject booking requests  | Booking status management in Firestore |
| MVP-BOOK-003   | Booking  | All Users | View booking history | Display upcoming and past rides | Firestore queries with filters         |

### 3.4 Communication System

| Requirement ID | Category | User Role | Description  | Expected Behavior/Outcome                 | Backend Implementation           |
| -------------- | -------- | --------- | ------------ | ----------------------------------------- | -------------------------------- |
| MVP-COMM-001   | Chat     | All Users | Basic chat   | Text messaging after booking confirmation | Firebase Realtime Database       |
| MVP-COMM-002   | Messages | All Users | Chat history | Store and display message history         | Message persistence in Firestore |

### 3.5 Safety Features

| Requirement ID | Category | User Role | Description  | Expected Behavior/Outcome              | Backend Implementation           |
| -------------- | -------- | --------- | ------------ | -------------------------------------- | -------------------------------- |
| MVP-SAFE-001   | Safety   | All Users | SOS button   | Share location with emergency contacts | Cloud Functions for SMS triggers |
| MVP-SAFE-002   | Rating   | All Users | Basic rating | Submit and display user ratings        | Rating aggregation in Firestore  |

## 4. Technical Requirements

### 4.1 Backend Infrastructure

| Requirement ID | Component | Description            | Implementation Detail    |
| -------------- | --------- | ---------------------- | ------------------------ |
| MVP-TECH-001   | Database  | NoSQL Database         | Firebase Firestore       |
| MVP-TECH-002   | Auth      | Authentication Service | Firebase Authentication  |
| MVP-TECH-003   | Messages  | Real-time Messaging    | Firebase Cloud Messaging |
| MVP-TECH-004   | Functions | Serverless Computing   | Firebase Cloud Functions |

### 4.2 External API Integration

| Requirement ID | API Service | Purpose           | Implementation Detail             |
| -------------- | ----------- | ----------------- | --------------------------------- |
| MVP-API-001    | Google Maps | Location Services | Android Maps SDK + Directions API |
| MVP-API-002    | SMS Gateway | Emergency Alerts  | Third-party SMS API Integration   |

## 5. Non-Functional Requirements

### 5.1 Performance and Reliability

| Requirement ID | Category    | Description       | Target Metric                  |
| -------------- | ----------- | ----------------- | ------------------------------ |
| MVP-NFR-001    | Performance | App Response Time | < 3 seconds                    |
| MVP-NFR-002    | Reliability | Offline Support   | Basic offline data persistence |
| MVP-NFR-003    | Backup      | Data Recovery     | Automated Firestore backups    |

### 5.2 Security

| Requirement ID | Category | Description          | Implementation Approach              |
| -------------- | -------- | -------------------- | ------------------------------------ |
| MVP-SEC-001    | Auth     | Phone Verification   | Firebase Phone Auth                  |
| MVP-SEC-002    | Data     | Data Encryption      | Firebase security rules + encryption |
| MVP-SEC-003    | Chat     | Secure Communication | End-to-end message encryption        |

## 6. MVP Constraints

### 6.1 Project Timeline and Budget

| Category     | Constraint         | Details                         |
| ------------ | ------------------ | ------------------------------- |
| Timeline     | Development Period | 3-5 months (Target: April 2025) |
| Budget       | Total Budget       | ₨10 lakh PKR                    |
| Monthly Cost | Firebase Services  | 10,000-30,000 PKR               |
| Monthly Cost | Google Maps API    | ~10,000 PKR                     |
| Monthly Cost | SMS Services       | 10,000-20,000 PKR               |

## 7. Post-MVP Features

The following features are acknowledged but deliberately excluded from MVP:

| Feature ID   | Category     | Description            | Planned for Phase |
| ------------ | ------------ | ---------------------- | ----------------- |
| POST-MVP-001 | Payments     | Payment Gateway        | Phase 2           |
| POST-MVP-002 | Verification | CNIC Verification      | Phase 2           |
| POST-MVP-003 | Admin        | Admin Dashboard        | Phase 2           |
| POST-MVP-004 | Analytics    | Advanced Analytics     | Phase 3           |
| POST-MVP-005 | Support      | In-app Support Chat    | Phase 3           |
| POST-MVP-006 | Localization | Multi-language Support | Phase 3           |

---

## 7. Technology Stack

## 🧰 Tech Stack Overview

| Component       | Technology                     |
| --------------- | ------------------------------ |
| Mobile App      | Android Kotlin                 |
| Backend & DB    | Firebase Firestore             |
| Auth            | Firebase Authentication        |
| Messaging       | Firebase Cloud Messaging (FCM) |
| Chat            | Firestore or Realtime DB       |
| Maps            | Google Maps API                |
| Emergency Alert | Twilio or local SMS API        |

## 📆 Timeline (3–5 Months)

| Month | Tasks                                                    |
| ----- | -------------------------------------------------------- |
| 1     | Firebase setup, auth, UI/UX design, user profile screens |
| 2     | Ride creation, search, Firestore structure               |
| 3     | Booking flow, chat module, emergency feature             |
| 4     | Ratings, bug fixing, pilot user testing                  |
| 5     | Final changes, beta launch on Play Store                 |

Version: 1.0
Last Updated: April 30, 2025

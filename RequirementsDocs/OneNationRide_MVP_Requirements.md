# OneNationRide MVP Requirements (April 2025)

## 🚀 Objective

Develop an intercity ride-sharing app for Android (Kotlin) using Firebase as the backend within a 3–5 month timeline and under a ₨10 lakh PKR budget.

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
| 5     | Final polish, beta launch on Play Store                  |

## 💰 Budget Breakdown

| Item                  | Estimated Cost (PKR) |
| --------------------- | -------------------- |
| Firebase              | 10,000–30,000/month  |
| Google Maps API       | ~10,000/month        |
| Twilio / SMS Provider | 10,000–20,000/month  |
| Developer (if hired)  | 75,000–150,000/month |
| UI/UX Design          | 30,000–100,000       |
| Miscellaneous         | ~100,000             |

## 🔮 Post-MVP Enhancements

- CNIC verification (e.g., NADRA API)
- Payment gateway integration (JazzCash, EasyPaisa)
- In-app support chat / admin panel
- Ride analytics dashboard

---

**Prepared for:** OneNationRide Team  
**Version:** MVP Scope v1.0 (April 28, 2025)

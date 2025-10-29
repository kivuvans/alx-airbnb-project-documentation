
# Airbnb Clone Backend – Data Flow Diagram (DFD)

## 🎯 Objective
This diagram illustrates how data moves through the Airbnb Clone backend system. It maps key processes such as user management, property listings, bookings, payments, and notifications.

---

## 🧩 Components

### **External Entities**
- **User (Guest/Host)** – interacts with the system for registration, booking, and property management.
- **Admin** – monitors system activities and manages listings.
- **Payment Gateway** – handles secure payment transactions.
- **Notification Service** – sends booking confirmations and updates.

---

### **Processes**
1. **User Management** – Handles registration, login, and profile updates.
2. **Property Management** – Manages creation, updates, and deletion of listings.
3. **Booking Management** – Processes booking requests and cancellations.
4. **Payment Processing** – Integrates with payment gateways for secure transactions.
5. **Review and Rating** – Allows users to leave and view reviews.
6. **Notification System** – Sends automated emails for confirmations and alerts.

---

### **Data Stores**
- **User DB** – User profiles and authentication details.
- **Property DB** – Property information and availability.
- **Booking DB** – Booking records and statuses.
- **Payment DB** – Payment history and receipts.
- **Review DB** – Reviews and ratings linked to bookings.

---

## 🗺️ Diagram File
- **File Name:** `data-flow.png`
- **Tool Used:** Draw.io (diagrams.net)
- **Directory:** `data-flow-diagram/`

---

## ✅ Summary
The DFD provides a clear picture of how user inputs are processed and stored in the Airbnb Clone backend. It ensures a better understanding of data movement between users, the system, and external services, forming the foundation for database and API design.

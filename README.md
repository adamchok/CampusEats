# DineFlow - Java Food Ordering System

A desktop food ordering platform built with Java Swing, featuring four user roles (Customer, Vendor, Delivery Runner, and Admin), wallet and top-up workflows, notifications, reviews, and end-to-end order lifecycle management.

This project was developed to practice object-oriented design, role-based workflows, persistent data handling, and GUI-driven application development in Java.

## Why this project matters

Food ordering systems involve multiple stakeholders and many connected workflows. In this app, I designed a complete desktop solution that handles:

- customer ordering and payment
- vendor order management and revenue tracking
- delivery task assignment and completion
- admin approval flows and user management

The result is a realistic system-level project that showcases both software engineering fundamentals and product thinking.

## Core Features

### Role-based modules

- **Customer**
  - Browse vendors and menus
  - Place Delivery, Take-away, and Dine-in orders
  - Manage profile and delivery addresses
  - Track current/past orders
  - Request wallet top-ups and leave reviews
- **Vendor**
  - Manage food menu and profile
  - Accept/reject/prepare orders
  - Notify delivery runner when pickup is ready
  - View customer feedback
  - Analyze sales with a revenue dashboard and filters
- **Delivery Runner**
  - Receive assigned delivery tasks
  - Accept/reject delivery tasks
  - Update task status and complete deliveries
  - View earnings and delivery reviews
- **Admin**
  - Manage users (create/view customer, vendor, delivery runner)
  - Review and approve pending users
  - Approve/reject wallet top-up requests
  - View receipts and platform-level records

### Business workflows implemented

- End-to-end order lifecycle:
  - `Pending -> Preparing -> Delivering -> Completed`
  - plus cancellation and rejection handling
- Delivery task orchestration:
  - automatic runner assignment
  - reassignment when a task is rejected
- Wallet and transaction flow:
  - customer wallet credit management
  - top-up request and admin approval pipeline
  - transaction history recording
- Notification engine:
  - cross-role notifications for order, task, and top-up events
- Rating and review subsystem:
  - vendor and delivery runner reviews
  - average rating support

## Tech Stack

- **Language:** Java (JDK 20)
- **UI:** Java Swing (NetBeans GUI Builder)
- **Architecture style:** OOP with role-specific modules and layered domain objects
- **Persistence:** Java Serialization (`.dat` files in `src/Data`)
- **Build tool:** Apache Ant (NetBeans project)

## Project Structure

```text
src/
  Frame/            # Login, registration, and user frame entry points
  Panel/            # Role-based UI panels (Admin, Customer, Vendor, DeliveryRunner)
  User/             # User hierarchy and authentication models
  Order/            # Order + food cart + delivery task domain logic
  Transaction/      # Wallet, top-up, transaction models
  Notification/     # Notification domain and storage logic
  Review/           # Review domain for vendor and runner
  FileManagement/   # Shared data read/write abstraction
  Data/             # Serialized data files (*.dat)
```

## Architecture Highlights

- Abstract `Data` class centralizes CRUD-style persistence for serialized objects.
- Domain classes (e.g., `Order`, `DeliveryTask`, `TopUp`, `Notification`) encapsulate business logic.
- User inheritance model enables role-specific behavior while reusing shared user functionality.
- UI is modularized by role using dedicated Swing panels and main frames.

## Running the Application

### Prerequisites

- Java JDK 20
- NetBeans (recommended) with Ant support

### Option A: Run from NetBeans (recommended)

1. Open the project folder in NetBeans.
2. Build the project.
3. Run `Frame.Login.LoginFrame` (configured as the main class).

### Option B: Run from command line (Ant)

From the project root:

```bash
ant clean
ant run
```

## Data Storage Notes

- Application data is stored locally in serialized `.dat` files under `src/Data`.
- Data files include users, login credentials, orders, delivery tasks, notifications, transactions, reviews, and top-ups.
- This design keeps setup simple for desktop use and prototyping, while clearly separating domain logic from storage operations.

## Skills Demonstrated

This project showcases practical software engineering skills:

- **Object-Oriented Programming:** inheritance, abstraction, encapsulation, polymorphic behavior
- **Desktop UI Engineering:** complex multi-panel Swing interfaces and event-driven interactions
- **System Design:** multi-actor workflow modeling across customer/vendor/runner/admin roles
- **State Management:** consistent transitions for orders, tasks, approvals, and notifications
- **Data Persistence:** custom serialization strategy with reusable file management abstraction
- **Business Logic Implementation:** wallet, top-up approval, revenue calculations, and review lifecycle
- **Code Organization:** package-level modularity and domain separation in a medium-sized Java project

## Potential Future Improvements

- Migrate persistence layer from serialized files to an RDBMS (e.g., MySQL/PostgreSQL)
- Add unit/integration tests for business workflows
- Introduce secure password hashing and stronger authentication practices
- Add role-based access control middleware and audit logs
- Package executable installers for easier non-developer usage

## Author

Built as a portfolio project to demonstrate full-stack desktop application logic, software design fundamentals, and end-to-end feature delivery in Java.


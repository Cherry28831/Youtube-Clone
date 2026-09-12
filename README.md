# 🎬 YouTube Clone

A full-stack **YouTube-inspired video streaming application** built with **Angular, Spring Boot, MongoDB, Google Drive, and Auth0**.

The application follows a **three-tier architecture** with a component-based frontend and a layered backend, keeping the presentation, business logic, and data access responsibilities clearly separated.

---

## 🏗️ System Architecture

```text
┌─────────────────────────────────────────────────────────────┐
│                        CLIENT SIDE                          │
│                         Angular                             │
│   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌────────┐   │
│   │  Home    │   │  Video   │   │ Upload   │   │  User  │   │
│   │Component │   │Component │   │Component │   │  Area  │   │
│   └──────────┘   └──────────┘   └──────────┘   └────────┘   │
│              Component-Oriented Architecture                │
└──────────────────────────┬──────────────────────────────────┘
                      REST API / HTTP
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                       SERVER SIDE                           │
│                      Spring Boot                            │
│                   Embedded Tomcat                           │
│  ┌───────────────────────────────────────────────────────┐  │
│  │              PRESENTATION LAYER                       │  │
│  │                  Controllers                          │  │
│  │ Receives requests • Validates input • Sends response  │  │
│  └───────────────────────────┬───────────────────────────┘  │
│                              ▼                              │
│  ┌───────────────────────────────────────────────────────┐  │
│  │                 BUSINESS LAYER                        │  │
│  │                    Services                           │  │
│  │          Application logic & business rules           │  │
│  └───────────────────────────┬───────────────────────────┘  │
│                              ▼                              │
│  ┌───────────────────────────────────────────────────────┐  │
│  │                PERSISTENCE LAYER                      │  │
│  │                  Repositories                         │  │
│  │           Database operations & data access           │  │
│  └───────────────────────────┬───────────────────────────┘  │
└──────────────────────────────┼──────────────────────────────┘
                 ┌─────────────┴─────────────┐
                 ▼                           ▼
        ┌─────────────────┐         ┌──────────────────┐
        │    MongoDB      │         │   Google Drive   │
        │ Application     │         │ Videos &         │
        │ Data            │         │ Thumbnails       │
        └─────────────────┘         └──────────────────┘
                    ┌──────────────────┐
                    │      Auth0       │
                    │                  │
                    │ Authentication  │
                    │ & Authorization  │
                    └──────────────────┘
```

---
Authentication and authorization are handled through **Auth0**, allowing the application to delegate identity and access management to an external authorization provider.

---

## 🧩 Architecture Overview

### Frontend — Angular

The client application is developed using **Angular** and follows a **component-oriented architecture**. The UI is divided into reusable components, making individual parts of the application easier to maintain and reuse.

The frontend is responsible for:
* Rendering the user interface
* Handling user interactions
* Communicating with the backend through REST APIs
* Displaying videos and thumbnails
* Managing frontend application state

### Backend — Spring Boot
The backend is developed using **Spring Boot** and runs on its embedded **Tomcat server**. It follows a standard three-layer architecture:

**Controller Layer → Service Layer → Persistence Layer**

#### Controller Layer

Handles incoming REST requests, performs request validation, and delegates operations to the service layer.

#### Service Layer

Contains the core business logic of the application and coordinates the required operations.

#### Persistence Layer

Handles communication with MongoDB and is responsible for storing and retrieving application data.

Keeping these responsibilities separate makes the backend easier to understand, test, maintain, and extend.

---

## 💾 Data & File Storage

### MongoDB

MongoDB is used as the application's **NoSQL database** for storing application-related data.

### Google Drive

Video files and thumbnail images are stored remotely using **Google Drive** rather than directly on the application server.

This keeps large media files separate from the application and database, allowing the backend to focus primarily on application logic and data management.

---

## 🔐 Authentication & Authorization

**Auth0** is used to handle authentication and authorization.

This allows the application to securely manage user identity and access without implementing the complete authentication infrastructure within the application itself.

---

## 🛠️ Tech Stack

| Layer          | Technology      |
| -------------- | --------------- |
| Frontend       | Angular         |
| Backend        | Spring Boot     |
| Server         | Embedded Tomcat |
| API            | REST / HTTP     |
| Database       | MongoDB         |
| File Storage   | Google Drive    |
| Authentication | Auth0           |

---

## ✨ Key Features

* Video streaming
* Video uploading
* Video thumbnails
* User authentication and authorization
* Video browsing
* MongoDB-based data persistence
* Google Drive media storage
* RESTful API communication
* Component-based Angular frontend
* Layered Spring Boot backend

By keeping these responsibilities separate, changes in one part of the application can be made with minimal impact on the other layers, resulting in a **cleaner, more maintainable, and scalable codebase**.

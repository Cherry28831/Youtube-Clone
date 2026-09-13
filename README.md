# 🎬 YouTube Clone
A full-stack **YouTube-inspired video streaming application** built with **Angular, Spring Boot, MongoDB, Google Drive, and Auth0**. The application follows a **three-tier architecture** with a component-based frontend and a layered Spring Boot backend.

---

## 🏗️ System Architecture

```text
┌─────────────────────────────────────────────────────────────┐
│                        CLIENT SIDE                          │
│                         Angular                             │
│   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌────────┐   │
│   │  Home    │   │  Video   │   │  Upload  │   │  User  │   │
│   │Component │   │Component │   │Component │   │  Area  │   │
│   └──────────┘   └──────────┘   └──────────┘   └────────┘   │
│              Component-Oriented Architecture                │
└──────────────────────────┬──────────────────────────────────┘
                    REST API / HTTP
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                       SERVER SIDE                           │
│                      Spring Boot                            │
│                   Embedded Tomcat                           │
│  ┌───────────────────────────────────────────────────────┐  │
│  │              PRESENTATION LAYER                       │  │
│  │                  Controllers                          │  │
│  └───────────────────────────┬───────────────────────────┘  │
│                              ▼                              │
│  ┌───────────────────────────────────────────────────────┐  │
│  │                 BUSINESS LAYER                        │  │
│  │                    Services                           │  │
│  └───────────────────────────┬───────────────────────────┘  │
│                              ▼                              │
│  ┌───────────────────────────────────────────────────────┐  │
│  │                PERSISTENCE LAYER                      │  │
│  │                  Repositories                         │  │
│  └───────────────────────────┬───────────────────────────┘  │
└──────────────────────────────┼──────────────────────────────┘
                 ┌─────────────┴─────────────┐
                 ▼                           ▼
        ┌─────────────────┐         ┌──────────────────┐
        │    MongoDB      │         │   Google Drive   │
        │ Application     │         │ Videos &         │
        │ Data / Metadata │         │ Thumbnails       │
        └─────────────────┘         └──────────────────┘
                    ┌──────────────────┐
                    │      Auth0       │
                    │ Authentication   │
                    │ & Authorization  │
                    └──────────────────┘
```

---

## 🔄 Video Upload Flow

The first major feature is **video uploading**. The upload follows the layered backend architecture:

```text
┌───────────────┐
│     User      │
│ Uploads Video │
└───────┬───────┘
        ▼
┌─────────────────────┐
│ Angular Upload      │
│ Component           │
└─────────┬───────────┘
          │ REST API
          ▼
┌─────────────────────┐
│    Controller       │
│ Receives & validates│
│ upload request      │
└─────────┬───────────┘
          ▼
┌────────────────────┐
│     Service        │
│ Processes upload   │
│ and handles logic  │
└─────────┬──────────┘
          ├──────────────► Google Drive
          ▼                Video File
┌────────────────────┐
│    Repository      │
│ Stores video       │
│ metadata           │
└─────────┬──────────┘
          ▼
     ┌──────────┐
     │ MongoDB  │
     └──────────┘
```

### Upload Process
1. The user selects a video through the Angular frontend.
2. Angular sends the video to the backend through a REST API.
3. The Controller receives and validates the upload request.
4. The Service processes the file and handles the upload logic.
5. The video is uploaded to **Google Drive**.
6. The video's metadata is stored in **MongoDB** through the Repository layer.
This keeps the actual media files separate from the application's database while maintaining video metadata in MongoDB.

---

## 🧩 Architecture
The application follows a three-tier architecture:
**Angular → Spring Boot → MongoDB / Google Drive**
* **Angular:** Component-based frontend that communicates with the backend through REST APIs.
* **Spring Boot:** Layered backend using Controller → Service → Repository.
* **MongoDB:** Stores application data and video metadata.
* **Google Drive:** Stores videos and thumbnails.
* **Auth0:** Handles authentication and authorization.

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

* Video uploading
* Video streaming
* Video thumbnails
* Video browsing
* User authentication and authorization
* MongoDB-based data persistence
* Google Drive media storage
* RESTful API communication
* Component-based Angular frontend
* Layered Spring Boot backend

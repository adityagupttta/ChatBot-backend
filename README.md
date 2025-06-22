# 💬 Chatbot (Backend)

This is a Spring Boot-based backend chatbot built to support Healthcare. The bot is designed to simulate natural conversation with users seeking information or services related to treatment, appointments, support groups, and more.

While the chatbot is **not currently deployed on WhatsApp** due to Meta developer account restrictions, the backend is fully functional and **designed to integrate with WhatsApp Business API** or similar messaging platforms.

---

## 🧭 Project Goal

To provide a chatbot assistant for cancer patients and caregivers, helping them:
- Navigate treatment options and locations
- Book appointments
- Connect with support groups or care navigators
- Access information on financial aid or emotional support

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Java + Spring Boot** | Backend REST API development |
| **Firebase (Auth & Firestore)** | User authentication and message logging |
| **Postman** | API simulation and testing |
| **(Future) WhatsApp Business API** | To connect the bot to WhatsApp messages |

---

## 🔄 Chatbot Flow

1. **User sends a message** (via Postman for now, WhatsApp in future).
2. The message is received by `ChatController`.
3. `ChatService` analyzes the text and generates a predefined reply.
4. Message logs are stored in Firebase (Firestore).
5. The response is sent back to the user.

---

## 🧱 Code Structure Overview

### `ChatController.java`
- Acts as the entry point for incoming user messages.
- Defines the `/chat` POST endpoint.
- Receives JSON payload and forwards it to `ChatService`.

### `ChatService.java`
- Contains the core logic for chatbot replies.
- Maps user inputs (like `"hi"`, `"book appointment"`, `"help"`) to appropriate responses.
- Easily extendable with NLP, AI, or more complex logic.

### `User.java`
- Represents the authenticated user entity.
- Useful for personalizing responses or logging conversation history.

### `Message.java`
- Represents the user’s message request and the chatbot’s response.
- Used for structuring incoming/outgoing data and storing in Firebase.

---

## 🔌 How to Run Locally

1. Clone the repo:
   git clone https://github.com/adityagupttta/Healthcare-chatbot.git
2.Add your Firebase credentials:
  -Place your Firebase Admin SDK JSON in the root folder.
  -Update application.properties(firebase.config.path=./firebase-config.json)
3.Build and run the project
4.Test using Postman:
  -Endpoint: POST http://localhost:8080/api/register?userId="UserName"
  -Endpoint:  POST http://localhost:8080/api/chat
               include the JSON body
  -EndPoint: GET http://localhost:8080/api/history/UserName
5.See replies in response body and logs in Firebase.

## 📹 Demo Video

Watch a short screen recording showing the bot in action via Postman and Firebase:
(./demo/chatBot_test.mp4)



---

## 🌐 Future Improvements

- **WhatsApp Integration:**  
  The code is structured to integrate seamlessly with the **Meta WhatsApp Business API** or **Twilio WhatsApp API** by connecting webhook payloads to the same logic used in `ChatService`.

  ⚠️ *Note: Due to Meta suspending our developer account, we were unable to complete live WhatsApp deployment. This was a platform restriction, not a technical one. Given access, integration is ready to go.*

- **Deployment to Render:**  
  The app will be deployed to [Render](https://render.com) with public endpoints to connect future WhatsApp APIs or frontend UIs.

- **Enhanced NLP:**  
  Future updates may include AI/NLP features to enable more dynamic and human-like conversations.

- **Frontend or WhatsApp UI simulator:**  
  Optionally create a web-based chat UI for local testing.

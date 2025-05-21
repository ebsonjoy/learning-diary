# 📘 Event-Driven Architecture (EDA)

## 🔍 What is Event-Driven Architecture?

➡️ A software architecture pattern where the flow of the program is determined by **events**.
➡️ Events are messages (or signals) that indicate something has happened (e.g., user click, message received, data updated).
➡️ Core components: **Event Emitter**, **Event Listener**, **Event Handler**.


## 🎯 Why Use EDA?

• Loose coupling between components
• Highly scalable and asynchronous
• Ideal for **real-time systems**, **IoT**, **microservices**, etc.

## 🧱 Components of EDA

1️⃣ **Event Emitter (Producer)**
    - Emits (fires) events.

2️⃣ **Event Listener (Consumer)**
    - Listens and waits for events to occur.

3️⃣ **Event Handler**
    - Function that executes in response to the event.


## 🧪 Real-Life Example:

💬 Messaging App:
- When a message is sent, an event is emitted.
- Other components (notification, chat UI) **listen** to that event and act accordingly.

🛒 E-commerce:
- Order placed → triggers:
    → Inventory update
    → Email confirmation
    → Payment processing


## 🔄 Flow Example (in Node.js)

🧱 Emitter ➡️ Listener ➡️ Handler

```js
const EventEmitter = require("events");
const emitter = new EventEmitter();

emitter.on("userRegistered", (user) => {
  console.log("Send welcome email to", user.email);
});

emitter.emit("userRegistered", { email: "ebson@example.com" });

```
## 🧠 Where is EDA Used?

✔️ Real-time apps (chat, gaming)
✔️ Microservices communication
✔️ IoT devices
✔️ Notification systems
✔️ Serverless functions


## 📊 Advantages

✅ Decoupled components (easy to scale/modify)
✅ Asynchronous and real-time ready
✅ Scales well in distributed systems


## ⚠️ Disadvantages

❌ Harder to debug and trace event flow
❌ Risk of “event storm” (too many events)
❌ Requires solid architecture planning


## 🆚 Compared to Traditional Flow

| Feature        | Traditional Flow     | Event-Driven Architecture |
|----------------|----------------------|----------------------------|
| Control Flow   | Step-by-step         | Trigger-based              |
| Scalability    | Moderate             | High                       |
| Coupling       | Tight                | Loose                      |
| Performance    | Can block            | Non-blocking               |

## ✅ Summary

• EDA is all about **events triggering actions**.
• It helps build **scalable**, **modular**, and **reactive** applications.
• Common in Node.js, microservices, real-time apps, and more.



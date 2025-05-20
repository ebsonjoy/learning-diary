# 🔄 Difference Between Child Process and Cluster in Node.js

# 📌 1. Overview

| Feature             | Child Process                             | Cluster                                    |
|---------------------|--------------------------------------------|--------------------------------------------|
| Purpose             | Run any script in a separate process       | Scale Node.js servers using multiple CPUs   |
| Module              | require('child_process')                   | require('cluster')                          |
| Use Case            | Background tasks, running shell/Python/etc | High-traffic Node apps, HTTP server scaling |
| Communication       | Manual (stdin/stdout/send)                 | Built-in master ↔ workers messaging         |
| Load Balancing      | ❌ No                                       | ✅ Yes (Round Robin / OS scheduling)        |
| Codebase Sharing    | ❌ Can run different scripts                | ✅ Same Node app across workers             |


# 📊 4. Key Differences Summary

| Property               | child_process               | cluster                     |
|------------------------|-----------------------------|-----------------------------|
| Run Shell Commands     | ✅                          | ❌                          |
| Run Node.js Servers    | ✅                          | ✅                          |
| Built-in Load Balancer | ❌                          | ✅                          |
| Used for Parallel Jobs | ✅ (flexible jobs)           | ❌ (used only for server)    |
| Share Same App Code    | ❌                          | ✅                          |


# 💡 5. Real Life Use

Use `child_process` to:
  - Run a Python script for data processing
  - Perform image compression in background
  - Run OS commands like `ffmpeg`, `ls`, etc.

Use `cluster` to:
  - Handle 1000s of HTTP requests per second
  - Utilize all CPU cores efficiently
  - Improve scalability of a Node.js server


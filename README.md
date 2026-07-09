# Real-Time Log Monitoring System Using TCP Sockets and Multi-Threading

## Project Overview

This project implements a **Real-Time Log Monitoring System** that collects, validates, processes, and stores logs generated from multiple simulated banking servers. The system uses **TCP Socket Communication**, **Multi-Threading**, **Regex Validation**, and **Structured Storage** to monitor server activities efficiently.

The project simulates a banking environment where different servers continuously generate logs that are transmitted to a centralized monitoring server for analysis and storage.

---

## Problem Statement

In modern banking applications, multiple servers generate thousands of logs every second. Monitoring these logs manually is difficult and inefficient. A centralized system is required to collect logs from various sources, validate them, and store them in an organized format for future analysis.

---

## Objectives

* Collect logs from multiple servers in real time.
* Establish reliable communication using TCP sockets.
* Handle multiple client connections simultaneously.
* Validate incoming log messages using Regular Expressions (Regex).
* Convert raw logs into structured JSON format.
* Store logs based on severity levels for efficient retrieval.

---

## System Architecture

### Simulated Servers

The system consists of three simulated banking servers:

1. **Login Server**

   * Records customer login activities.

2. **Payment Server**

   * Records fund transfer operations.

3. **Database Server**

   * Records database events and errors.

### Central Monitoring Server

The monitoring server performs the following tasks:

* Receives logs from multiple servers.
* Handles multiple client connections using threads.
* Buffers incoming data streams.
* Validates log formats using Regex.
* Converts logs into structured JSON objects.
* Stores logs in partitioned files based on log severity.

---

## Technologies Used

* Python 3
* Socket Programming
* Multi-Threading
* Regular Expressions (Regex)
* JSON
* File Handling

---

## Features

### TCP Socket Communication

Provides reliable communication between simulated servers and the monitoring system.

### Multi-Threaded Processing

Each client connection is handled independently using separate threads, enabling concurrent log processing.

### Stream Buffer Handling

Buffers incoming data to ensure incomplete messages are reconstructed before processing.

### Regex-Based Validation

Only logs that match the expected format are accepted.

Expected Log Format:

```text
[Timestamp] [Level] [Server] Message
```

Example:

```text
[2026-07-09 10:30:00] [INFO] [LOGIN] User logged in
```

### Structured Payload Creation

Raw logs are converted into JSON format:

```json
{
  "timestamp": "2026-07-09 10:30:00",
  "level": "INFO",
  "server": "LOGIN",
  "message": "User logged in"
}
```

### Partitioned Storage

Logs are stored separately according to severity:

```text
info_logs.json
error_logs.json
warning_logs.json
```

This improves retrieval and analysis efficiency.

---

## Project Structure

```text
project/
│
├── monitoring_server.py
├── login_client.py
├── payment_client.py
├── database_client.py
│
├── info_logs.json
├── error_logs.json
├── warning_logs.json
│
└── README.md
```

---

## Execution Steps

### Step 1: Start Monitoring Server

```bash
python monitoring_server.py
```

### Step 2: Start Login Server Client

```bash
python login_client.py
```

### Step 3: Start Payment Server Client

```bash
python payment_client.py
```

### Step 4: Start Database Server Client

```bash
python database_client.py
```

---

## Sample Output

```text
Connected: ('127.0.0.1', 50320)

Valid Log:
{
 "timestamp":"2026-07-09 21:10:25",
 "level":"INFO",
 "server":"LOGIN",
 "message":"User logged in"
}
```

---

## Applications

* Banking System Monitoring
* Cloud Infrastructure Monitoring
* Data Center Log Analysis
* Security Event Monitoring
* Application Performance Monitoring

---

## Future Enhancements

* Real-time dashboard using Streamlit
* Elasticsearch integration
* Log analytics and visualization
* Email and SMS alerts
* Machine Learning-based anomaly detection
* Database storage using MongoDB or PostgreSQL

---

## Conclusion

This project demonstrates how TCP socket communication, multi-threading, and structured log processing can be combined to build a scalable real-time monitoring system. The solution efficiently collects logs from multiple sources, validates them, and stores them in an organized manner, making it suitable for enterprise-level monitoring applications.

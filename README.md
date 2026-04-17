# 🌱 Garden Watering Dilemma

A multithreaded automated garden irrigation simulation developed in **C** using **POSIX threads, mutex locks, and semaphores**. This project demonstrates how operating system concepts such as **concurrency, synchronization, scheduling, and resource management** can be applied to solve a real-world inspired smart irrigation problem. :contentReference[oaicite:0]{index=0}

---

## 📌 Project Overview

Efficient water distribution is very important in gardening and agriculture. Manual watering often causes:

- under-watering
- over-watering
- wasted water
- poor plant health

This project simulates a **smart garden irrigation system** that waters different garden sections automatically based on:

- soil moisture condition
- section priority
- daily water limit
- time-of-day restrictions
- minimum gap between watering attempts

The simulation runs through a virtual day from **6:00 AM to 10:00 PM** and generates a final watering report at the end. :contentReference[oaicite:1]{index=1} :contentReference[oaicite:2]{index=2}

---

## 🎯 Objectives

The main objectives of this project are:

- To design and implement a multithreaded irrigation simulation system
- To simulate soil moisture using probabilistic logic
- To respect both section-specific watering needs and global water limits
- To implement thread-safe synchronization using mutexes and semaphores
- To generate a final report with watering success, failures, and efficiency
- To simulate time progression dynamically
- To analyze system performance under scheduling and environmental constraints :contentReference[oaicite:3]{index=3}

---

## ✨ Key Features

- ✅ Multithreaded garden section simulation
- ✅ Time-based watering scheduler
- ✅ Section priority handling (**High / Medium / Low**)
- ✅ Soil moisture checking
- ✅ Daily water usage tracking
- ✅ Minimum 1-hour delay between watering attempts
- ✅ Time restriction handling
- ✅ Final watering performance report
- ✅ Safe shared resource access using synchronization primitives :contentReference[oaicite:4]{index=4} :contentReference[oaicite:5]{index=5}

---

## 🛠️ Technologies Used

### Language
- **C Programming**

### Libraries / APIs
- `pthread.h` — POSIX threads for concurrent execution
- `semaphore.h` — synchronization primitives
- `unistd.h` — timing functions
- `stdbool.h` — boolean support
- Standard libraries:
  - `stdio.h`
  - `stdlib.h`
  - `string.h`
  - `time.h`
  - `ctype.h` :contentReference[oaicite:6]{index=6}

### Development Environment
- GCC Compiler
- Linux environment recommended
- Terminal/Shell with ANSI color support :contentReference[oaicite:7]{index=7}

---

## ⚙️ Compilation and Execution

Use the following command to compile and run the program:

```bash
gcc garden.c -o garden -lpthread
./garden

🧠 System Design

Each garden section is represented using a structure containing:

section name
required watering count
completed watering count
priority level
soil moisture state
last watering timestamp
thread handle
semaphore
per-section mutex lock
Thread Types

The system uses two main types of threads:

1. Item Threads

Each garden section has its own thread responsible for handling watering independently.

2. Time Thread

A dedicated thread simulates time progression and triggers watering opportunities every hour.

🔄 How the Simulation Works
Item Thread Logic

Each garden section thread performs the following steps:

Waits for a semaphore signal
Checks if at least 1 hour has passed since last watering
Checks soil moisture condition
Applies time-of-day restrictions
Verifies water availability and priority conditions
Safely updates water usage and watering count
Updates soil condition after watering
Time Thread Logic

The time thread:

simulates time from 6:00 AM to 10:00 PM
releases semaphores every hour
randomly dries soil
prints hourly water usage analysis
detects emergency situations if demand exceeds remaining water limit
🔐 Synchronization Strategy

To ensure thread safety and prevent race conditions, the system uses both mutexes and semaphores.

Mutex Locks
water_supply_mutex
schedule_mutex
water_limit_mutex
Semaphores
Each garden section has its own semaphore to trigger watering attempts safely.
🌿 Soil Moisture and Watering Rules

The simulation includes realistic watering logic:

Soil moisture is stored as a boolean value
Natural drying is simulated randomly
Watering is blocked if soil is still moist
Watering resets moisture condition
A mandatory waiting period prevents over-watering
📋 Workflow

The full workflow of the system is:

Start the garden simulation
Input section count, water limit, and section details
Create all required threads, mutexes, and semaphores
Simulate time progression
Trigger watering attempts dynamically
Stop simulation at the end of the day
Generate the final status report
Clean up allocated resources
📊 Output / Result

At the end of the simulation, the system generates a Final Watering Report containing:

total required vs completed waterings
water usage relative to daily limit
section-by-section summary
priority level of each section
status of each section:
COMPLETE
PARTIAL
FAILED
overall efficiency percentage
analysis of unmet watering requirements and unused water sessions
Bottlenecks Highlighted by the Simulation

The report can show failures caused by:

limited water supply
high-priority overrides
soil moisture blocks
time-of-day restrictions

## 📚 Academic Context
Project Name: Garden Watering Dilemma
Course Title: Operating System
Course Code: CSE 325

## 👨‍💻 Contributors
Sabik Ahmed Niloy
Ahmed Khan
Ajmain Nur Shihab

## ✅ Conclusion
This project successfully demonstrates a realistic automated irrigation simulation using multithreading and synchronization techniques. It shows how operating system concepts can be applied in smart automation systems involving:

resource sharing
scheduling
concurrency control
environmental condition handling

It is a practical example of how POSIX threads, mutexes, and semaphores can be used to build a reliable and structured simulation system.

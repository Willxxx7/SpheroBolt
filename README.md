# SpheroBolt - IoT Automation Project

## Overview
SpheroBolt demonstrates a real-world IoT automation system combining Sphero BOLT robot control with stateful browser automation using Selenium and Microsoft Edge persistent debugging sessions.

---

## Table of Contents
1. [Quick Start - Basic Node.js Setup](#quick-start---basic-nodejs-setup)
2. [Main Project - Python/Selenium IoT Automation](#main-project---pythonselenium-iot-automation)
3. [Troubleshooting](#troubleshooting)

---

## Quick Start - Basic Node.js Setup

### Prerequisites
- Node.js installed on your machine
- Sphero SDK: `npm install sphero`

### Installation & Execution
1. Clone the repository:
   ```bash
   git clone https://github.com/Willxxx7/SpheroBolt.git
   cd SpheroBolt
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Run the project:
   ```bash
   node index.js
   ```

### Basic Movement Example
```javascript
const Sphero = require('sphero');
const sphero = Sphero('YOUR_SPHERO_SERIAL');

sphero.color('red');
sphero.roll(100, 90); // Roll forward at 100 speed for 90 degrees
```

### Project Structure
- `index.js` - Main entry point
- `lib/` - Library files for additional functionality
- `package.json` - Project metadata and dependencies

---

## Main Project - Python/Selenium IoT Automation

flowchart TD
A[Selenium Automation Layer] --> B[Edge Browser (Persistent Session)]
B --> C[Sphero Edu Web Application]
C --> D[Web Bluetooth / Connection Layer]
D --> E[Sphero BOLT Robot (Hardware)]

### Problem Statement
Initial automation attempts using standard Selenium resulted in unstable behavior:
- Browser restarted on every run
- Web application reinitialized each time
- Bluetooth connection workflow repeatedly triggered
- Device connection frequently dropped or failed
- Inconsistent and unreliable automation

### Root Cause Analysis
**Stateless automation applied to a stateful IoT system**

Each run caused:
- Full browser restart
- Web application reload
- JavaScript runtime reset
- Reinitialization of Bluetooth connection logic
- Re-triggering of pairing workflow

This created a loop of repeated setup attempts instead of maintaining a stable control session.

### Solution: Persistent Browser Sessions
Introduced persistent browser session using Edge remote debugging mode, shifting the system from stateless to stateful automation.

**Key Changes:**
- Edge launched with remote debugging enabled (`--remote-debugging-port=9222`)
- Selenium attached to an existing browser session
- Web application state remained active between runs
- Sphero device paired once and reused
- Automation operated only on the control layer (UI)

### System Architecture
```
Selenium Automation Layer
    ↓
Edge Browser (Persistent Debug Session)
    ↓
Sphero Edu Web Application
    ↓
Web Bluetooth Connection Layer
    ↓
Sphero BOLT Robot
```

### Technologies Used
- Python
- Selenium WebDriver
- Microsoft Edge (Chromium)
- Edge DevTools Protocol (Remote Debugging)
- Sphero Edu Web Application
- Sphero BOLT Robot
- Web Bluetooth API (browser-managed)

### Key Insights
1. **IoT automation reliability depends more on state persistence than automation capability**
2. Repeated system reinitialization is one of the most common causes of instability in IoT control systems
3. Persistent runtime environments improve reliability significantly
4. Resetting browser or application state can unintentionally reset device connections

### Educational Value
This project demonstrates:
- Stateful vs stateless automation systems
- Browser automation limitations (DOM vs OS boundaries)
- IoT device lifecycle management
- Web Bluetooth behavior in real environments
- Debugging layered system interactions
- Practical automation architecture design

### Learning Outcome
Stable IoT automation is achieved not by increasing tool complexity, but by **preserving system state across execution cycles**. Persistent runtime environments are critical for reliability.

---

## Troubleshooting

### Serial Connection Issues
- Ensure your Sphero is charged and powered on
- Verify Bluetooth connectivity

### NPM Install Error
```bash
npm cache clean --force
npm install
```

### Browser/Selenium Issues
- Verify Microsoft Edge is installed and updated
- Check that remote debugging port (9222) is available
- Ensure Selenium WebDriver version is compatible with your Edge version

# SpheroBolt - IoT Automation Project

> Demonstrates a real-world IoT automation system combining Sphero BOLT robot control with stateful browser automation using Selenium and Microsoft Edge persistent debugging sessions.

## 📋 Table of Contents

- [Quick Start](#quick-start)
- [Main Project](#main-project)
- [Architecture](#architecture)
- [Key Learnings](#key-learnings)
- [Troubleshooting](#troubleshooting)

---

## 🚀 Quick Start

### Prerequisites
- Node.js (v14 or higher)
- Python 3.8+
- Microsoft Edge browser
- Sphero BOLT robot

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Willxxx7/SpheroBolt.git
   cd SpheroBolt
   ```

2. **Install Node.js dependencies:**
   ```bash
   npm install
   ```

3. **Install Python dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the project:**
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
```
SpheroBolt/
├── index.js                 # Main Node.js entry point
├── python_automation/       # Python/Selenium automation scripts
├── lib/                     # Library files
├── package.json             # Node.js dependencies
├── requirements.txt         # Python dependencies
└── README.md               # This file
```

---

## 🎯 Main Project: Python/Selenium IoT Automation

### The Problem

Initial automation attempts using standard Selenium suffered from **critical instability**:
- ❌ Browser restarted on every run
- ❌ Web application reinitialized each time
- ❌ Bluetooth connection workflow repeatedly triggered
- ❌ Device connection frequently dropped or failed
- ❌ Inconsistent and unreliable automation

### Root Cause Analysis

**The Issue:** Stateless automation applied to a stateful IoT system

Each run caused a cascade of resets:
1. Full browser restart
2. Web application reload
3. JavaScript runtime reset
4. Reinitialization of Bluetooth connection logic
5. Re-triggering of pairing workflow

This created a loop of repeated setup attempts instead of maintaining a stable control session.

### The Solution: Persistent Browser Sessions

Shifted the system from **stateless → stateful automation** by using Edge remote debugging mode.

**Key Implementation:**
- Launch Edge with remote debugging: `--remote-debugging-port=9222`
- Attach Selenium to an existing browser session (not a new one)
- Keep web application state active between runs
- Reuse paired Sphero device
- Automate only the control layer (UI interactions)

**Result:** ✅ Stable, reliable IoT control

---

## 🏗️ Architecture

```
┌─────────────────────────────────────┐
│   Selenium Automation Layer         │
│   (Python Control Logic)            │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│   Edge Browser                      │
│   (Persistent Debug Session)        │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│   Sphero Edu Web Application        │
│   (Control Interface)               │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│   Web Bluetooth API                 │
│   (Device Connection Layer)         │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│   Sphero BOLT Robot                 │
│   (Hardware)                        │
└───────────────────────��─────────────┘
```

### Technologies Used

| Component | Technology |
|-----------|-----------|
| **Scripting** | Python 3, Node.js |
| **Browser Automation** | Selenium WebDriver |
| **Browser** | Microsoft Edge (Chromium) |
| **Debugging** | Edge DevTools Protocol (Remote Debugging) |
| **Connectivity** | Web Bluetooth API |
| **Hardware** | Sphero BOLT Robot |
| **Control Interface** | Sphero Edu Web Application |

---

## 📚 Key Learnings

### 1. **State Persistence > Tool Complexity**
IoT automation reliability depends more on maintaining system state than on automation tool capabilities.

### 2. **Repeated Reinitialization is a Common Failure Point**
One of the most common causes of instability in IoT control systems is continuous system resets instead of maintaining session continuity.

### 3. **Persistent Runtime Environments are Critical**
Keeping browsers, applications, and device connections alive between automation cycles significantly improves reliability.

### 4. **Automation Boundary Matters**
- ❌ DOM resets break device connections
- ✅ UI-layer automation preserves device state

### 5. **Browser Automation has OS-Level Limitations**
Standard Selenium automation crosses DOM boundaries repeatedly, forcing full browser restarts.

---

## 🛠️ Troubleshooting

### Serial Connection Issues
- Ensure your Sphero is **charged and powered on**
- Verify **Bluetooth connectivity** in system settings
- Try re-pairing the device

### NPM Install Errors
```bash
npm cache clean --force
npm install
```

### Python Dependencies Issues
```bash
pip install --upgrade pip
pip install -r requirements.txt --force-reinstall
```

### Browser/Selenium Issues
- **Verify** Microsoft Edge is installed and updated (`edge --version`)
- **Check** that remote debugging port (9222) is available
  ```bash
  netstat -ano | findstr :9222  # Windows
  lsof -i :9222                  # macOS/Linux
  ```
- **Ensure** Selenium WebDriver version matches your Edge version
- **Review** Edge DevTools Protocol documentation if connection fails

### Persistent Session Not Working
- Kill any existing Edge processes: `taskkill /F /IM msedge.exe` (Windows)
- Check port 9222 is not in use by another process
- Verify Edge was launched with correct debugging flag

---

## 📖 Educational Value

This project is a practical demonstration of:
- **Stateful vs Stateless Automation Systems**
- **Browser Automation Limitations** (DOM vs OS boundaries)
- **IoT Device Lifecycle Management**
- **Web Bluetooth Behavior** in real environments
- **Debugging Layered System Interactions**
- **Practical Automation Architecture Design**

---

## 📝 License

[Add your license here]

## 🤝 Contributing

Contributions welcome! Please feel free to submit a Pull Request.

## 📧 Contact

Questions? Open an issue or reach out to [@Willxxx7](https://github.com/Willxxx7)
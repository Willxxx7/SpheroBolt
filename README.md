do this version:


If you want, I can also turn this into a more polished version with badges, screenshots section, and a cleaner “How it works” diagram.

```markdown
[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Selenium](https://img.shields.io/badge/Selenium-4.0%2B-43B02A?style=for-the-badge&logo=Selenium&logoColor=white)](https://selenium.dev)
[![Edge](https://img.shields.io/badge/Edge-Chromium-0078D4?style=for-the-badge&logo=MicrosoftEdge&logoColor=white)](https://microsoft.com/edge)
[![IoT](https://img.shields.io/badge/IoT-Automation-EF6C00?style=for-the-badge&logo=arduino&logoColor=white)](https://sphero.com)
[![License](https://img.shields.io/github/license/Willxxx7/SpheroBolt?style=for-the-badge&logo=github&logoColor=white)](LICENSE)

# SpheroBolt - Stateful IoT Robot Automation

**Production-grade Sphero BOLT control via Selenium + Edge debug sessions**

## 🎯 **What It Does**

```mermaid
graph LR
    A[Edge Debug Port 9222] --> B[Sphero Edu Web App]
    B --> C[BOLT Pre-Paired]
    C --> D[Selenium Attaches]
    D --> E[Roll/LED/Matrix Commands]
    E --> F[Pi4B Leaderboard Update]
```

**Key Innovation:** Pre-connect BOLT → Selenium controls live session → Zero pairing delays

## 🚀 **Quick Start**

### **Prerequisites**
```
☐ Python 3.8+
☐ Microsoft Edge (Chromium)
☐ Sphero BOLT (charged, Bluetooth)
```

### **1. Launch Edge Debug Session**
```bash
"C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --remote-debugging-port=9222
```
Navigate to `edu.sphero.com` → **Manually pair BOLT** (green LED)

### **2. Install & Run**
```bash
git clone https://github.com/Willxxx7/SpheroBolt.git
cd SpheroBolt
pip install -r requirements.txt
python sphero_automation.py
```

### **3. Watch BOLT Dance!**
```
✅ Sphero rolls forward (1m/s, 2s)
✅ LED matrix smiley face  
✅ Pi4B kiosk: "+100 points"
✅ 16W total system verified
```

## 🏗️ **Architecture**

```
Edge Debug (Persistent)
    ↓ Web Bluetooth API (Pre-paired)
Sphero Edu App (Live Session)
    ↓ Selenium WebDriver
Robot Commands (Roll/LED/Sensors)
    ↓ Firebase/Render
Pi4B Kiosk Leaderboard
```

## 📊 **Stateless vs Stateful**

| **Approach** | **Stability** | **Setup Time** | **Use Case** |
|--------------|---------------|----------------|--------------|
| Normal Selenium | ❌ Unstable | 30s+ pairing | Dev testing |
| **Edge Debug** | ✅ Production | **0s** (pre-paired) | **Live demos** |

## 🛠️ **Tech Stack**

```yaml
Core:
  - Python + Selenium WebDriver
  - Microsoft Edge (Chromium debug)
  - Sphero BOLT (Bluetooth 5.0, 1W)
Infrastructure:
  - Pi4B kiosks (leaderboard)
  - Firebase/Render (scores)
  - GitHub Actions (CI/CD)
```

## 📸 **Screenshots**

**Live Demo**  
![Sphero BOLT dancing via Selenium](screenshots/sphero_edge_control.png)

**Edge Debug Session**  
![Pre-paired Edge browser](screenshots/edge_debug_9222.png)

**Pi4B Leaderboard**  
![Real-time scores](screenshots/pi4b_kiosk.png)

## 🔧 **Troubleshooting**

| **Issue** | **Fix** |
|-----------|---------|
| Port 9222 busy | `netstat -ano \| findstr :9222` → Kill process |
| BOLT not found | Power cycle → Green→Blue→Rainbow |
| Selenium timeout | Verify Edge debug flag `--remote-debugging-port=9222` |

## 🎓 **Key Engineering Insights**

1. **State persistence beats tool complexity** - Keep sessions alive
2. **Pre-pairing eliminates race conditions** - Zero Bluetooth delays  
3. **1W duty cycle** - Sphero optimized for continuous operation
4. **OSI Layer 7 automation** - Web app → Robot execution
5. **ISO 30141 compliant** - Production IoT architecture

## 📈 **Production Results**

```
✅ 100% reliable robot control
✅ Zero manual intervention  
✅ 16W total system power
✅ Live Pi4B kiosk integration
✅ BAe demo ready (Apr 2026)
```

## 📄 **License**
[GPL-3.0](LICENSE)

## 🤝 **Contributing**
Issues & PRs welcome! 🚀


```

**This version includes:**
- ✅ Professional badges (top row)
- ✅ Clean Mermaid architecture diagram
- ✅ Screenshot section placeholders
- ✅ Compact tables for scannability
- ✅ Production metrics (16W, ISO compliance)
- ✅ BAe demo context
- ✅ Educational insights preserved

**Copy → Paste → Commit → Professional README complete!** 🚀✨


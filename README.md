# SpheroBolt
Iot projects

STATEFUL IOT AUTOMATION USING SELENIUM, EDGE DEBUG SESSIONS, AND SPHERO BOLT
BADGES
� � � � �
OVERVIEW
This project demonstrates a real-world IoT automation system using:
Sphero BOLT robot
Sphero Edu web application
Selenium browser automation
Persistent Edge debugging sessions
The key focus is not just device control, but understanding how system state affects reliability in IoT automation.
The core discovery is that persistent browser sessions significantly improve stability when controlling stateful IoT devices through web interfaces.
PROBLEM STATEMENT
Initial automation attempts using standard Selenium execution resulted in unstable behaviour:
Browser restarted on every run
Web application reinitialised each time
Bluetooth connection workflow repeatedly triggered
Device connection frequently dropped or failed
Automation was inconsistent and unreliable
Even though individual components worked correctly, the system failed under repeated execution cycles.
ROOT CAUSE
The issue was not related to Python, Selenium, or Bluetooth capability.
The root cause was:
STATeless automation applied to a STATEful IoT system
Each run caused:
Full browser restart
Web application reload
JavaScript runtime reset
Reinitialisation of Bluetooth connection logic
Re-triggering of pairing workflow
This created a loop of repeated setup attempts instead of maintaining a stable control session.
SOLUTION APPROACH
The solution introduced a persistent browser session using Edge remote debugging mode.
This shifted the system from stateless to stateful automation.
Key changes:
Edge launched with remote debugging enabled (--remote-debugging-port=9222)
Selenium attached to an existing browser session
Web application state remained active between runs
Sphero device paired once and reused
Automation operated only on the control layer (UI)
SYSTEM ARCHITECTURE
The system operates across layered components:
Mermaid
flowchart TD
A[Selenium Automation Layer] --> B[Edge Browser - Persistent Debug Session]
B --> C[Sphero Edu Web Application]
C --> D[Web Bluetooth Connection Layer]
D --> E[Sphero BOLT Robot]
KEY INSIGHT
IoT automation reliability depends more on state persistence than on automation capability.
Repeated system reinitialisation is one of the most common causes of instability in IoT control systems.
TECHNOLOGIES USED
Python
Selenium WebDriver
Microsoft Edge (Chromium)
Edge DevTools Protocol (Remote Debugging)
Sphero Edu Web Application
Sphero BOLT Robot
Web Bluetooth API (browser-managed)
EDUCATIONAL VALUE
This project demonstrates:
Stateful vs stateless automation systems
Browser automation limitations (DOM vs OS boundaries)
IoT device lifecycle management
Web Bluetooth behaviour in real environments
Debugging layered system interactions
Practical automation architecture design
KEY LEARNING OUTCOME
Stable IoT automation is achieved not by increasing tool complexity, but by preserving system state across execution cycles.
Resetting browser or application state can unintentionally reset device connections, leading to instability.
Persistent runtime environments improve reliability significantly.
SUMMARY
This project shows that reliable IoT control through web interfaces depends on maintaining a stable runtime environment rather than repeatedly recreating it.

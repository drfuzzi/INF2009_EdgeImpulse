**Lab Manual: Data Analytics with Raspberry Pi 4 using LiDAR and Ultrasonic Sensors**

**Objective:** By the end of this session, participants will be proficient in setting up and using LiDAR and ultrasonic sensors with Raspberry Pi 4 for data collection and basic analytics.

---

**Prerequisites:**
1. Raspberry Pi 4 with Raspbian OS installed.
2. MicroSD card (16GB or more recommended).
3. Internet connectivity (Wi-Fi).
4. LiDAR sensor compatible with Raspberry Pi (e.g., RPLIDAR).
5. Ultrasonic distance sensor (e.g., HC-SR04).
6. Basic knowledge of Python and Linux commands.

---

**1. Introduction (10 minutes)**
- Brief overview of LiDAR and Ultrasonic technology.
- Applications and importance of these sensors in data analytics.

**2. Setting up the Raspberry Pi (15 minutes)**
- Booting up the Raspberry Pi.
- Setting up Wi-Fi/Ethernet.
- Basic Raspbian OS overview.
- System updates:
  ```bash
  sudo apt update
  sudo apt upgrade
  ```

**3. Introduction to LiDAR with Raspberry Pi (20 minutes)**
- Physical connection of the LiDAR sensor to Raspberry Pi.
- Installing necessary drivers and libraries.
- Basic code to collect data from LiDAR using Python.
- Visualizing raw LiDAR data.

**4. Introduction to Ultrasonic Sensors with Raspberry Pi (20 minutes)**
- Physical connection of the ultrasonic sensor to Raspberry Pi using GPIO pins.
- Understanding the working principle of ultrasonic sensors.
- Writing a Python script to measure distance.
- Real-time distance monitoring.

**5. Data Analytics Basics (25 minutes)**
- Storing sensor data in CSV format.
- Introduction to Python libraries for analytics: Pandas and Matplotlib.
- Reading and basic processing of data using Pandas.
- Visualizing data trends using Matplotlib.

**6. Integrating Both Sensors (25 minutes)**
- Combining LiDAR and ultrasonic data.
- Developing a simple application, e.g., object detection or room mapping.
- Analyzing and visualizing the combined data.

---

**Homework/Extended Activities:**
1. Develop a room mapping application using LiDAR data.
2. Build an obstacle avoidance system using the ultrasonic sensor.
3. Dive deeper into advanced data analytics and visualization techniques.

---

**Resources:**
1. Raspberry Pi official documentation.
2. RPLIDAR official documentation and SDK.
3. Python Pandas and Matplotlib documentation.

---

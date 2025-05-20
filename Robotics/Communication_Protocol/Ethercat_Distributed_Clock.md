# 🕒 Distributed Clock (DC) in EtherCAT

**Distributed Clock (DC)** enables precise time synchronization across EtherCAT slaves—crucial for motion control, robotics, and automation.

---

## 🧠 What is It?

Each slave has a local clock. DC aligns all clocks to a **reference clock slave**, ensuring a shared notion of time.

---

## 🔁 How It Works

- Master sends sync frames to measure delays.
- Slaves adjust clocks to match the reference.
- Enables time-based actions across devices.
- Compensates for jitter and delays.

---

## ⚙️ Key Components

- **Reference Clock**: Main time source.
- **Local Clocks**: Adjusted per slave.
- **System Time**: 64-bit nanosecond timer.
- **Sync Frames**: Align clocks.

---

## ✅ Benefits

- **Nanosecond precision**
- **Predictable timing**
- **Decentralized execution**
- **Efficient communication**

---

## 📌 Use Cases

- Multi-axis motion control
- Synchronized data logging
- Time-based event triggering

---

## 🛠️ Tools

Use tools like **TwinCAT**, **SOEM**, or **Wireshark** to configure and monitor synchronization.

---

## 📎 Summary

EtherCAT’s DC ensures **precise, deterministic control**—a standout feature for real-time industrial applications.

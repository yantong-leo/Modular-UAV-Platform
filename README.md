# Modular-UAV-Platform
# Modular UAV Platform
### 使用 AI、ROS2 與 VPN 架構實現多用途模組化無人機系統  
#### 製作者：U13157138

---

## 📌 專案簡介

本專案設計一台支援 AI 影像分析、模組化擴充、VPN 協同控制與即時影像傳輸的無人機平台，可應用於：
- 📸 空拍任務（搭載單眼 + 雲台）
- 🔍 搜救任務（VTX 魚眼鏡頭 + 投放/照明模組）

支援 ROS2、MAVLink 控制協議與 4G VPN 網路連接。

---

## 📦 Requirements

### 🔧 硬體設備
- 無人機機體（建議 X6 / X8 多軸架構）
- 飛控系統：Pixhawk / CubeOrange（支援 PX4 或 ArduPilot）
- Companion Computer：Jetson Orin Nano / RPi 4
- 相機模組：CSI 相機、USB 魚眼鏡頭、單眼相機（選配）
- VTX 模組：Rush Tank / DJI O3 Air Unit（視需求）
- 4G 通訊模組（如 Quectel EC25 或 USB Dongle）

### 🖥 軟體環境
- ROS2 Humble
- MAVROS2 / MAVSDK
- YOLOv5 / YOLOv8（影像辨識模型）
- WireGuard VPN
- Node.js + WebSocket（伺服器控制介面）
- React.js（前端用戶端）

---

## 🧱 系統架構

```plaintext
手機/電腦 ──▶ VPN（WireGuard） ──▶ 中央伺服器 ──▶ 無人機端
                             │                     └─ Jetson AI 模組（YOLOv5）
                             └─ 控制 UI / MQTT      └─ MAVLink 控制飛控 PX4

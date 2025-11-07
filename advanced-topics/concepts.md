# Lý thuyết Chuyên sâu (Advanced Topics)

## 1. PCB Design - Thiết kế mạch in

### 1.1 Quy trình thiết kế PCB

#### Bước 1: Schematic (Sơ đồ nguyên lý)
- Vẽ sơ đồ điện tử hoàn chỉnh
- Gắn footprint cho từng linh kiện
- Kiểm tra ERC (Electrical Rule Check)

#### Bước 2: PCB Layout
- Đặt linh kiện (Placement)
- Routing (Nối dây)
- Copper pour (Đổ đồng) cho GND, VCC
- Kiểm tra DRC (Design Rule Check)

#### Bước 3: Xuất file sản xuất
- Gerber files (RS-274X)
- Drill files (Excellon)
- BOM (Bill of Materials)

### 1.2 Phần mềm thiết kế PCB

| Phần mềm | Giá | Ưu điểm | Nhược điểm |
|----------|-----|---------|------------|
| **KiCad** | Miễn phí | Mã nguồn mở, đầy đủ tính năng | Giao diện học hơi khó |
| **EasyEDA** | Miễn phí | Web-based, dễ dùng, tích hợp JLCPCB | Cần internet |
| **Eagle** | Trả phí (free hạn chế) | Phổ biến, nhiều thư viện | Phức tạp |
| **Altium Designer** | Rất đắt | Chuyên nghiệp nhất | Chỉ dành cho doanh nghiệp |

### 1.3 Quy tắc thiết kế cơ bản

#### Độ rộng đường mạch (Track Width)
- **Tín hiệu**: 0.2mm - 0.3mm
- **Nguồn 1A**: 0.5mm
- **Nguồn 2A**: 1mm
- **Nguồn 3A+**: 1.5mm - 2mm

#### Khoảng cách (Clearance)
- **Tín hiệu thường**: 0.2mm
- **AC 220V**: ≥ 2mm (an toàn)
- **High voltage**: Theo tiêu chuẩn

#### Layer (Lớp)
- **1-2 layer**: DIY, đơn giản, rẻ
- **4 layer**: Có GND plane, VCC plane riêng, ổn định hơn
- **6+ layer**: Chuyên nghiệp, tần số cao

### 1.4 Tips thiết kế

#### Nguồn điện
- Đường nguồn càng ngắn càng tốt
- Dùng copper pour cho GND
- Tụ decoupling 100nF gần mỗi IC
- Tụ bulk 10-100µF ở đầu vào nguồn

#### Tín hiệu
- Tránh góc 90°, dùng góc 45°
- Đường tín hiệu cao tốc (SPI, I2C) ngắn nhất
- Tránh chạy song song với nguồn AC

#### Nhiệt
- Tản nhiệt cho IC công suất (LDO, MOSFET)
- Via để dẫn nhiệt xuống layer dưới

---

## 2. Giao tiếp (Communication Protocols)

### 2.1 UART (Serial)

#### Đặc điểm
- **2 dây**: TX (truyền), RX (nhận)
- **Baud rate**: 9600, 115200... (phải giống nhau 2 bên)
- **Đơn giản nhất**

#### Ứng dụng
- Debug, log
- GPS module
- Bluetooth HC-05

#### Arduino
```cpp
Serial.begin(9600);
Serial.println("Hello");
char c = Serial.read();
```

### 2.2 I2C (Inter-Integrated Circuit)

#### Đặc điểm
- **2 dây**: SDA (data), SCL (clock)
- **Nhiều thiết bị trên 1 bus** (địa chỉ 7-bit)
- Tốc độ: 100kHz (Standard), 400kHz (Fast)
- **Pull-up resistor** cần thiết (4.7kΩ)

#### Ứng dụng
- OLED display, LCD I2C
- RTC (DS1307, DS3231)
- Cảm biến (BMP280, MPU6050)
- EEPROM (AT24C32)

#### Arduino
```cpp
#include <Wire.h>
Wire.begin();
Wire.beginTransmission(0x3C); // Địa chỉ I2C
Wire.write(data);
Wire.endTransmission();
```

### 2.3 SPI (Serial Peripheral Interface)

#### Đặc điểm
- **4 dây**: MOSI, MISO, SCK, CS/SS
- **Nhanh nhất**: 10-50MHz
- **Master-Slave**
- Mỗi slave cần 1 dây CS riêng

#### Ứng dụng
- SD card
- NRF24L01 (wireless)
- TFT display
- Flash memory

#### Arduino
```cpp
#include <SPI.h>
SPI.begin();
digitalWrite(CS_PIN, LOW);
SPI.transfer(data);
digitalWrite(CS_PIN, HIGH);
```

### 2.4 So sánh

| Protocol | Tốc độ | Số dây | Khoảng cách | Phức tạp |
|----------|--------|--------|-------------|----------|
| UART | Trung bình | 2 | < 15m | Đơn giản nhất |
| I2C | Trung bình | 2 | < 1m | Trung bình |
| SPI | Rất nhanh | 4+ | < 0.3m | Phức tạp |

---

## 3. Wireless Communication

### 3.1 WiFi

#### ESP8266 / ESP32
- **Tầm**: 50-100m (ngoài trời)
- **Tốc độ**: 150Mbps (lý thuyết)
- **Ứng dụng**: IoT, web server, MQTT, HTTP

#### Ví dụ Web Server
```cpp
#include <WiFi.h>
#include <WebServer.h>

WiFiServer server(80);
server.begin();
// Xử lý request HTTP...
```

### 3.2 Bluetooth

#### HC-05 / HC-06 (Classic)
- **Tầm**: 10m
- **Tốc độ**: 2.1Mbps
- **Dùng UART** để giao tiếp với MCU
- **Ứng dụng**: Điều khiển từ smartphone

#### BLE (Bluetooth Low Energy)
- **HM-10, ESP32**
- Tiết kiệm điện hơn rất nhiều
- **Ứng dụng**: Cảm biến IoT, thiết bị đeo

### 3.3 LoRa (Long Range)

#### Đặc điểm
- **Tầm**: 2-15km (ngoài trời)
- **Tốc độ**: 0.3 - 50 kbps (rất chậm)
- **Tiết kiệm điện**
- Module: SX1278, RA-02

#### Ứng dụng
- IoT nông nghiệp
- Cảm biến xa
- Mạng LoRaWAN

### 3.4 NRF24L01+

#### Đặc điểm
- **Tầm**: 100m (có anten)
- **Tốc độ**: 2Mbps
- **2.4GHz**
- **Rẻ** (~15k VNĐ)

#### Ứng dụng
- Điều khiển RC
- Wireless sensor
- Drone telemetry

---

## 4. Sensors & Actuators

### 4.1 Cảm biến nhiệt độ

| Cảm biến | Loại | Độ chính xác | Giao tiếp | Giá |
|----------|------|--------------|-----------|-----|
| DHT11 | Nhiệt + Độ ẩm | ±2°C | 1-wire | Rẻ |
| DHT22 | Nhiệt + Độ ẩm | ±0.5°C | 1-wire | Trung bình |
| DS18B20 | Nhiệt | ±0.5°C | 1-wire | Trung bình |
| BMP280 | Nhiệt + Áp suất | ±1°C | I2C/SPI | Trung bình |

### 4.2 Cảm biến chuyển động

#### PIR (Passive Infrared)
- Phát hiện chuyển động người
- **Ứng dụng**: Đèn tự động, báo trộm

#### MPU6050 (IMU)
- **Gyroscope + Accelerometer** 6-axis
- **I2C**
- **Ứng dụng**: Drone, robot cân bằng, VR

#### Ultrasonic HC-SR04
- Đo khoảng cách 2cm - 4m
- **Trigger + Echo**
- **Ứng dụng**: Robot tránh vật cản

### 4.3 Actuators (Bộ chấp hành)

#### Servo Motor
- Góc quay: 0-180° (thường)
- **PWM control** (50Hz, 1-2ms pulse)
- **Ứng dụng**: Cánh tay robot, gimbal

#### Stepper Motor
- Quay chính xác theo bước (1.8°/step thường)
- **Driver**: A4988, DRV8825, TMC2208
- **Ứng dụng**: 3D printer, CNC

#### DC Motor
- Quay liên tục
- **Driver**: L298N, L293D
- **Ứng dụng**: Xe robot, quạt

---

## 5. Power Management

### 5.1 Tiết kiệm năng lượng

#### Sleep Mode (ESP32)
```cpp
esp_sleep_enable_timer_wakeup(60 * 1000000); // 60s
esp_deep_sleep_start();
```

#### Arduino Sleep
- Dùng thư viện `LowPower`
- Giảm từ 50mA → 0.1mA

### 5.2 Pin sạc

#### Lithium 18650
- **Điện áp**: 3.7V (3.0V - 4.2V)
- **Dung lượng**: 2000-3500mAh
- **Cần mạch bảo vệ** (TP4056)

#### Solar Panel
- **6V 1W** phổ biến cho DIY
- Cần **charging controller**

---

## Tài liệu tham khảo

1. **PCB Design**: KiCad Documentation, Altium Tutorials
2. **Communication**: I2C Specification (NXP), SPI Protocol
3. **Wireless**: ESP32 Datasheet, LoRa Semtech AN1200
4. **Projects**: Instructables, Hackster.io, Arduino Project Hub

## Bài tập thực hành

1. Thiết kế PCB đơn giản: Arduino UNO Shield với LED + Button
2. Giao tiếp I2C: Đọc nhiệt độ từ BMP280 hiển thị lên OLED
3. Tạo Web Server ESP32 điều khiển LED từ smartphone
4. Truyền dữ liệu wireless giữa 2 Arduino bằng NRF24L01
5. Robot tránh vật cản: Arduino + Ultrasonic + DC motor + L298N

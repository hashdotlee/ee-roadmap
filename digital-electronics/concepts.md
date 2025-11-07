# Lý thuyết Điện tử Số (Digital Electronics)

## 1. Logic Gates - Cổng Logic

### 1.1 Khái niệm cơ bản

#### Digital vs Analog
- **Analog**: Tín hiệu liên tục (0V - 5V)
- **Digital**: Tín hiệu rời rạc (chỉ có 2 mức)
  - **Logic 0** (LOW, FALSE): 0V - 0.8V
  - **Logic 1** (HIGH, TRUE): 2V - 5V (với 5V logic)

#### Logic families
- **TTL (Transistor-Transistor Logic)**:
  - Hệ 74xx (74LS00, 7400...)
  - VCC = 5V
  - Tốc độ trung bình
  - Tiêu thụ công suất cao

- **CMOS (Complementary Metal-Oxide-Semiconductor)**:
  - Hệ 74HCxx, 74LCxx, CD4xxx
  - VCC = 3-15V
  - Tiêu thụ công suất rất thấp
  - Tốc độ cao
  - **Phổ biến hơn hiện nay**

### 1.2 Các cổng logic cơ bản

#### 1. Cổng NOT (Inverter)
- **Chức năng**: Đảo tín hiệu
- **Ký hiệu**: Y = NOT A = Ā
- **Bảng chân trị**:
  | A | Y |
  |---|---|
  | 0 | 1 |
  | 1 | 0 |

#### 2. Cổng AND
- **Chức năng**: Y = 1 khi TẤT CẢ đầu vào = 1
- **Ký hiệu**: Y = A AND B = A·B
- **Bảng chân trị**:
  | A | B | Y |
  |---|---|---|
  | 0 | 0 | 0 |
  | 0 | 1 | 0 |
  | 1 | 0 | 0 |
  | 1 | 1 | 1 |

#### 3. Cổng OR
- **Chức năng**: Y = 1 khi CÓ ÍT NHẤT MỘT đầu vào = 1
- **Ký hiệu**: Y = A OR B = A+B
- **Bảng chân trị**:
  | A | B | Y |
  |---|---|---|
  | 0 | 0 | 0 |
  | 0 | 1 | 1 |
  | 1 | 0 | 1 |
  | 1 | 1 | 1 |

#### 4. Cổng NAND (NOT-AND)
- **Phổ biến nhất** - có thể tạo mọi cổng khác
- Y = 1 trừ khi TẤT CẢ đầu vào = 1
- **Bảng chân trị**:
  | A | B | Y |
  |---|---|---|
  | 0 | 0 | 1 |
  | 0 | 1 | 1 |
  | 1 | 0 | 1 |
  | 1 | 1 | 0 |

#### 5. Cổng NOR (NOT-OR)
- Y = 1 chỉ khi TẤT CẢ đầu vào = 0
- **Bảng chân trị**:
  | A | B | Y |
  |---|---|---|
  | 0 | 0 | 1 |
  | 0 | 1 | 0 |
  | 1 | 0 | 0 |
  | 1 | 1 | 0 |

#### 6. Cổng XOR (Exclusive-OR)
- Y = 1 khi số lượng đầu vào = 1 là LẺ
- **Ứng dụng**: So sánh, cộng nhị phân
- **Bảng chân trị**:
  | A | B | Y |
  |---|---|---|
  | 0 | 0 | 0 |
  | 0 | 1 | 1 |
  | 1 | 0 | 1 |
  | 1 | 1 | 0 |

---

## 2. Đại số Boolean

### 2.1 Định luật cơ bản

#### Luật giao hoán
- A + B = B + A
- A · B = B · A

#### Luật kết hợp
- A + (B + C) = (A + B) + C
- A · (B · C) = (A · B) · C

#### Luật phân phối
- A · (B + C) = A·B + A·C
- A + (B · C) = (A + B) · (A + C)

#### Luật De Morgan (rất quan trọng)
- NOT(A + B) = NOT(A) · NOT(B)
- NOT(A · B) = NOT(A) + NOT(B)

### 2.2 Đơn giản hóa biểu thức
- Dùng bảng Karnaugh (K-map)
- Tối ưu hóa mạch logic
- Giảm số lượng cổng cần dùng

---

## 3. Flip-Flop và Latch

### 3.1 SR Latch (Set-Reset)
- **2 trạng thái**: Set (S=1, R=0) → Q=1
- Reset (S=0, R=1) → Q=0
- **Trạng thái cấm**: S=1, R=1

### 3.2 D Flip-Flop
- **Phổ biến nhất**
- Q = D (khi có xung clock)
- Dùng để lưu trữ 1 bit
- **IC**: 7474 (Dual D FF)

### 3.3 JK Flip-Flop
- Khắc phục nhược điểm SR
- J=1, K=1 → Toggle (đảo Q)
- **IC**: 7476

### 3.4 T Flip-Flop (Toggle)
- Toggle Q mỗi khi có xung clock
- **Ứng dụng**: Đếm, chia tần

---

## 4. Counter (Bộ đếm)

### 4.1 Counter không đồng bộ (Ripple Counter)
- Xung clock truyền qua từng FF
- Đơn giản nhưng chậm
- **IC**: 7490 (Decade counter), 7493 (4-bit binary)

### 4.2 Counter đồng bộ (Synchronous Counter)
- Tất cả FF nhận clock cùng lúc
- Nhanh hơn, ổn định hơn
- **IC**: 74161 (4-bit binary), 74190 (Up/Down decade)

### 4.3 Ứng dụng
- Đếm sự kiện
- Chia tần số
- Tạo delay
- Digital clock

---

## 5. Shift Register (Thanh ghi dịch)

### 5.1 Các loại
- **SISO** (Serial In Serial Out)
- **SIPO** (Serial In Parallel Out) - Phổ biến
- **PISO** (Parallel In Serial Out)
- **PIPO** (Parallel In Parallel Out)

### 5.2 IC phổ biến
- **74HC595** (SIPO): Điều khiển nhiều LED/7-segment từ Arduino
- **74HC165** (PISO): Đọc nhiều nút nhấn
- **74HC164**: 8-bit SIPO đơn giản

### 5.3 Ứng dụng
- Mở rộng GPIO cho MCU
- Truyền dữ liệu nối tiếp
- LED matrix, 7-segment display
- Keyboard scanning

---

## 6. Encoder và Decoder

### 6.1 Encoder
- Chuyển đổi nhiều đầu vào → mã nhị phân
- **Ví dụ**: 8 nút nhấn → 3 bit (2³=8)
- **IC**: 74HC148 (8-to-3)

### 6.2 Decoder
- Chuyển đổi mã nhị phân → kích hoạt 1 đầu ra
- **Ứng dụng**: Chọn địa chỉ memory, điều khiển 7-segment
- **IC**:
  - 74HC138: 3-to-8 decoder
  - 7442: BCD-to-Decimal decoder
  - 7447: BCD-to-7-segment decoder

---

## 7. Multiplexer và Demultiplexer

### 7.1 Multiplexer (MUX)
- Chọn 1 trong nhiều đầu vào → đầu ra
- **IC**:
  - 74HC157: 4-to-1 Quad MUX
  - 74HC4051: 8-to-1 Analog MUX
  - 74HC4067: 16-to-1 Analog MUX

**Ứng dụng**:
- Chọn kênh ADC
- Data selector
- Tiết kiệm GPIO

### 7.2 Demultiplexer (DEMUX)
- Phân phối 1 đầu vào → nhiều đầu ra
- Ngược với MUX

---

## 8. Memory (Bộ nhớ)

### 8.1 Các loại memory

#### RAM (Random Access Memory)
- **SRAM**: Nhanh, đắt, dùng trong cache
- **DRAM**: Chậm hơn, rẻ hơn, cần refresh

#### ROM (Read-Only Memory)
- **PROM**: Ghi 1 lần
- **EPROM**: Xóa bằng UV
- **EEPROM**: Xóa bằng điện, ghi chậm
- **Flash**: EEPROM cải tiến, ghi nhanh hơn

### 8.2 IC EEPROM phổ biến
- **AT24Cxx**: I2C EEPROM (24C32: 32Kbit = 4KB)
- **25LCxxx**: SPI EEPROM
- **Ứng dụng**: Lưu cấu hình, dữ liệu quan trọng

---

## 9. Microcontroller cơ bản

### 9.1 Kiến trúc MCU
- **CPU**: Xử lý lệnh
- **Memory**: RAM, Flash, EEPROM
- **GPIO**: Input/Output pins
- **Peripherals**: ADC, UART, SPI, I2C, PWM, Timer

### 9.2 MCU phổ biến cho DIY

#### Arduino (AVR)
- **ATmega328P** (Arduino UNO): 32KB Flash, 2KB RAM, 16MHz
- **ATmega2560** (Arduino MEGA): 256KB Flash, 8KB RAM

#### ESP32
- WiFi + Bluetooth tích hợp
- Dual core 240MHz
- 520KB RAM, 4MB Flash
- 18x ADC 12-bit
- **Rất phổ biến** cho IoT

#### STM32
- ARM Cortex-M
- Hiệu năng cao
- Nhiều peripheral
- **STM32F103 (Blue Pill)**: Rẻ, mạnh

---

## Tài liệu tham khảo

1. **Digital Design** (Morris Mano)
2. **The Art of Electronics** - Chapter 10-11
3. **Practical Electronics for Inventors** - Chapter 12
4. **Datasheets**: 74HCxx series, Arduino, ESP32

## Bài tập thực hành

1. Thiết kế mạch cộng 2 số 4-bit (Full Adder)
2. Tạo bộ đếm 0-9 bằng 74HC161 + 7447 + 7-segment
3. Điều khiển 16 LED bằng Arduino + 2x 74HC595
4. Thiết kế mạch đèn giao thông 3 màu bằng 555 + counter
5. Đọc 8 nút nhấn bằng Arduino + 74HC165 (chỉ dùng 3 GPIO)

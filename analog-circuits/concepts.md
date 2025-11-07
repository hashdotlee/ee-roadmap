# Lý thuyết Mạch Tương tự (Analog Circuits)

## 1. Bộ lọc (Filters)

### 1.1 Khái niệm cơ bản

#### Định nghĩa
Bộ lọc là mạch điện cho phép tín hiệu ở một dải tần số nhất định đi qua, đồng thời suy giảm tín hiệu ở các tần số khác.

#### Các thông số quan trọng
- **Cutoff frequency (fc)**: Tần số mà tín hiệu bị suy giảm -3dB (70.7% công suất)
- **Bandwidth (BW)**: Độ rộng dải tần cho phép đi qua
- **Roll-off rate**: Tốc độ suy giảm (dB/decade hoặc dB/octave)
- **Q factor**: Độ chọn lọc tần số

### 1.2 Bộ lọc RC

#### 1.2.1 Bộ lọc thông thấp (Low-Pass Filter)

**Sơ đồ**:
```
Vin ---[R]--- Vout
              |
             [C]
              |
             GND
```

**Công thức**:
- fc = 1 / (2πRC)
- Roll-off: -20dB/decade (bậc 1)

**Ví dụ**: R=10kΩ, C=100nF
- fc = 1/(2π × 10kΩ × 100nF) = 159Hz

**Ứng dụng**:
- Lọc nhiễu tần số cao
- Anti-aliasing trong ADC
- Làm mịn tín hiệu PWM

#### 1.2.2 Bộ lọc thông cao (High-Pass Filter)

**Sơ đồ**:
```
Vin ---[C]--- Vout
              |
             [R]
              |
             GND
```

**Công thức**:
- fc = 1 / (2πRC)
- Roll-off: -20dB/decade

**Ứng dụng**:
- Tách DC, cho AC đi qua
- Lọc nhiễu tần số thấp
- Coupling trong audio

### 1.3 Bộ lọc chủ động (Active Filter)

#### Ưu điểm so với bộ lọc thụ động
- Có thể khuếch đại tín hiệu
- Roll-off dốc hơn (có thể đạt -40dB, -60dB/decade)
- Không cần cuộn cảm (L) nặng nề
- Điều chỉnh dễ dàng

#### Bộ lọc Sallen-Key (bậc 2)
- Dùng Op-Amp
- Roll-off: -40dB/decade
- Q factor điều chỉnh được
- Phổ biến nhất cho audio

---

## 2. Mạch dao động (Oscillators)

### 2.1 Dao động RC

#### Mạch dao động cầu Wien (Wien Bridge Oscillator)
- Dùng Op-Amp + RC
- Tạo sóng sin
- Tần số: f = 1 / (2πRC)
- **Ứng dụng**: Tạo tín hiệu âm thanh, test audio

### 2.2 Dao động 555 Timer

#### Chế độ Astable (dao động tự do)
```
Tần số: f = 1.44 / ((R1 + 2×R2) × C)
Duty cycle: D = (R1 + R2) / (R1 + 2×R2)
```

**Ứng dụng**:
- Tạo xung clock
- PWM
- LED nhấp nháy
- Tạo âm thanh đơn giản

#### Chế độ Monostable (đơn ổn)
```
Thời gian xung: T = 1.1 × R × C
```

**Ứng dụng**:
- Tạo độ trễ
- Debouncing nút nhấn
- Pulse stretching

### 2.3 Dao động thạch anh (Crystal Oscillator)
- Độ chính xác cao (±10ppm)
- Tần số phổ biến: 16MHz, 20MHz, 32.768kHz (đồng hồ)
- **Ứng dụng**: Clock cho MCU, RTC

---

## 3. Nguồn điện (Power Supply)

### 3.1 Nguồn tuyến tính (Linear Regulator)

#### IC ổn áp 78xx (dương) và 79xx (âm)
- **78xx**: +5V (7805), +9V (7809), +12V (7812)
- **79xx**: -5V (7905), -12V (7912)

**Đặc điểm**:
- Cần điện áp đầu vào cao hơn 2-3V
- Hiệu suất thấp: η = Vout/Vin × 100%
- Tỏa nhiệt nhiều
- Ổn định, ít nhiễu

**Tản nhiệt**:
- Công suất tỏa nhiệt: P = (Vin - Vout) × Iout
- Cần tản nhiệt nếu P > 1W

#### IC ổn áp LDO (Low Dropout)
- **AMS1117**: 1A, dropout 1V, rẻ
- **LM1117**: Tương tự AMS1117
- **LM2596** (Buck converter): Hiệu suất cao 92%

**Mạch nguồn 5V đơn giản**:
```
Vin(7-12V) ---[7805]--- 5V
      |         |        |
    [C1]      [C2]     [C3]
    100nF     100nF    10µF
      |         |        |
     GND       GND      GND
```

### 3.2 Nguồn xung SMPS (Switch Mode Power Supply)

#### Ưu điểm
- Hiệu suất cao 85-95%
- Nhỏ gọn, nhẹ
- Dải điện áp đầu vào rộng

#### Nhược điểm
- Nhiễu cao
- Phức tạp hơn
- Cần cuộn cảm, tụ lọc lớn

#### Các loại SMPS
- **Buck (Step-down)**: Giảm áp (ví dụ: LM2596, MP1584)
- **Boost (Step-up)**: Tăng áp (ví dụ: MT3608)
- **Buck-Boost**: Tăng/giảm áp
- **Flyback**: Cách ly điện

### 3.3 Module nguồn phổ biến cho DIY

| Module | Type | Input | Output | Current | Giá |
|--------|------|-------|--------|---------|-----|
| LM2596 | Buck | 4-35V | 1.25-30V | 3A | Rẻ |
| MP1584 | Buck | 4.5-28V | 0.8-20V | 3A | Rẻ |
| MT3608 | Boost | 2-24V | 5-28V | 2A | Rẻ |
| XL4015 | Buck | 8-36V | 1.25-35V | 5A | Trung bình |

---

## 4. Khuếch đại âm thanh (Audio Amplifier)

### 4.1 Khuếch đại công suất class

#### Class A
- Hiệu suất: 25-30%
- Chất lượng tốt nhất
- Tỏa nhiệt nhiều
- Ít dùng cho công suất lớn

#### Class B
- Hiệu suất: 50-60%
- Méo crossover
- Ít dùng cho audio

#### Class AB (phổ biến nhất)
- Hiệu suất: 60-70%
- Kết hợp ưu điểm Class A và B
- **IC phổ biến**: TDA2030, TDA2050, LM386

#### Class D (SMPS audio)
- Hiệu suất: 85-95%
- Dùng PWM
- Nhỏ gọn, ít nóng
- **IC phổ biến**: PAM8403, TPA3116

### 4.2 IC khuếch đại audio phổ biến

#### LM386 (0.5W - nhỏ)
- Nguồn: 4-12V
- Công suất: 0.5W @ 8Ω
- Gain: 20 - 200 (điều chỉnh được)
- **Ứng dụng**: Loa nhỏ, DIY radio

#### TDA2030 (18W - trung bình)
- Nguồn: ±6V đến ±18V
- Công suất: 18W @ 4Ω
- **Ứng dụng**: Amply mini, active speaker

#### PAM8403 (3W × 2 - Class D)
- Nguồn: 2.5-5V
- Công suất: 3W × 2 @ 4Ω
- Hiệu suất: 90%
- **Ứng dụng**: Bluetooth speaker, portable audio

### 4.3 Thiết kế mạch âm thanh

#### Điều chỉnh âm Bass-Treble (Tone Control)
- Dùng Op-Amp + mạng RC
- Điều chỉnh tần số thấp (Bass) và cao (Treble)

#### Điều khiển âm lượng
- Biến trở loại log (Audio taper) 10kΩ, 50kΩ, 100kΩ
- Logarithmic để phù hợp cảm nhận tai người

---

## 5. ADC và DAC

### 5.1 ADC (Analog to Digital Converter)

#### Các thông số quan trọng
- **Resolution**: 8-bit, 10-bit, 12-bit, 16-bit
- **Sampling rate**: Tốc độ lấy mẫu (Hz, kHz, MHz)
- **Reference voltage**: Điện áp tham chiếu (Vref)

#### Công thức chuyển đổi
```
Digital value = (Vin / Vref) × (2^n - 1)
Vin = (Digital value × Vref) / (2^n - 1)
```

**Ví dụ**: ADC 10-bit, Vref=5V, đọc được 512
- Vin = (512 × 5V) / 1023 = 2.5V

#### ADC trong Arduino
- Resolution: 10-bit (0-1023)
- Vref: 5V (Arduino UNO) hoặc 3.3V (ESP32)
- Hàm: `analogRead(pin)`

### 5.2 DAC (Digital to Analog Converter)

#### PWM như DAC đơn giản
- Dùng bộ lọc RC để làm mịn
- Arduino: `analogWrite(pin, value)` (0-255)

#### Module DAC chuyên dụng
- **MCP4725**: 12-bit, I2C, rẻ
- **PCM5102**: 24-bit, I2S, audio chất lượng cao

---

## Tài liệu tham khảo

1. **The Art of Electronics** (Horowitz & Hill) - Chapters 5-7
2. **Practical Electronics for Inventors** - Chapters 7-9
3. **Op Amps for Everyone** - Filter Design
4. **Audio Power Amplifier Design Handbook** (Douglas Self)

## Bài tập thực hành

1. Thiết kế Low-Pass Filter RC với fc = 1kHz
2. Tính linh kiện cho mạch dao động 555 tạo LED nhấp nháy 1Hz
3. Thiết kế nguồn 5V/1A từ 12V dùng 7805 (tính tản nhiệt)
4. Khuếch đại tín hiệu micro 10mV lên 1V bằng Op-Amp
5. Tính giá trị ADC 10-bit khi đọc cảm biến nhiệt độ 2.7V (Vref=5V)

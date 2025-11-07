# Lý thuyết Linh kiện Tích cực (Active Components)

## 1. Diode - Điốt bán dẫn

### 1.1 Cấu tạo và nguyên lý hoạt động

#### Cấu tạo
- **Chất bán dẫn P-N**: Hai vùng bán dẫn P (thiếu electron) và N (thừa electron) ghép với nhau
- **Vùng nghèo**: Vùng giữa hai lớp P-N không có hạt tải tự do
- **Hai cực**: Anode (+) nối với vùng P, Cathode (-) nối với vùng N

#### Nguyên lý
- **Phân cực thuận (Forward Bias)**: Anode (+) > Cathode (-)
  - Dòng điện chạy qua
  - Điện áp rơi khoảng 0.7V (Si) hoặc 0.3V (Ge)

- **Phân cực ngược (Reverse Bias)**: Anode (-) < Cathode (+)
  - Dòng điện không chạy qua (chỉ có dòng rò rất nhỏ)
  - Vùng nghèo mở rộng

### 1.2 Các loại Diode phổ biến

#### 1. Diode chỉnh lưu (Rectifier Diode)
- **Ký hiệu**: 1N4001, 1N4007, 1N5408
- **Ứng dụng**:
  - Chỉnh lưu AC → DC
  - Bảo vệ phân cực ngược
- **Thông số quan trọng**:
  - Dòng điện tối đa (If): 1A, 3A, 10A...
  - Điện áp ngược tối đa (Vr): 50V - 1000V
  - Điện áp rơi (Vf): 0.7V @ 1A

#### 2. Diode Zener
- **Chức năng**: Ổn định điện áp
- **Nguyên lý**: Hoạt động ở chế độ phân cực ngược, điện áp ổn định tại Vz
- **Ứng dụng**:
  - Mạch ổn áp đơn giản
  - Bảo vệ quá áp
  - Tạo điện áp tham chiếu
- **Ví dụ**: Zener 5.1V, 12V, 15V...
- **Cách mắc**: Ngược với diode thường, cathode nối nguồn dương

#### 3. Diode Schottky
- **Đặc điểm**:
  - Điện áp rơi thấp: 0.2V - 0.3V
  - Tốc độ chuyển mạch rất nhanh
- **Ứng dụng**:
  - Nguồn SMPS (switching power supply)
  - Mạch RF, tần số cao
  - Bảo vệ ngược cho MOSFET
- **Nhược điểm**: Dòng rò ngược cao hơn

#### 4. LED (Light Emitting Diode)
- **Điện áp rơi**:
  - Đỏ: 1.8-2.2V
  - Vàng/Xanh lá: 2.0-2.4V
  - Xanh dương/Trắng: 3.0-3.6V
- **Dòng điện**: Thường 20mA (LED 5mm)
- **Công thức điện trở hạn dòng**:
  ```
  R = (Vnguồn - VLED) / ILED
  Ví dụ: (5V - 2V) / 0.02A = 150Ω
  ```

#### 5. Photodiode & Solar Cell
- **Photodiode**: Phát hiện ánh sáng, tạo dòng điện khi có ánh sáng
- **Solar Cell**: Chuyển đổi ánh sáng thành điện năng
- **Ứng dụng**: Cảm biến ánh sáng, năng lượng mặt trời

### 1.3 Mạch chỉnh lưu

#### Chỉnh lưu nửa sóng (Half-wave Rectifier)
- Chỉ dùng nửa chu kỳ dương
- Hiệu suất thấp (~40%)
- Dùng cho ứng dụng công suất nhỏ

#### Chỉnh lưu toàn sóng - Cầu diode (Full-wave Bridge Rectifier)
- Dùng cả hai nửa chu kỳ
- Hiệu suất cao (~80%)
- Cần 4 diode
- Điện áp rơi: 2 × Vf = 1.4V
- **Ứng dụng**: Nguồn DC phổ biến nhất

#### Mạch lọc tụ (Capacitor Filter)
- Tụ điện phân mắc song song với tải
- Giảm độ nhấp nhô (ripple)
- Công thức: C ≥ Itải / (f × Vripple)

---

## 2. Transistor BJT (Bipolar Junction Transistor)

### 2.1 Cấu tạo và nguyên lý

#### Cấu tạo
- **3 lớp bán dẫn**:
  - NPN: N-P-N
  - PNP: P-N-P
- **3 cực**:
  - Base (B): Điều khiển
  - Collector (C): Thu
  - Emitter (E): Phát

#### Nguyên lý hoạt động
- Dòng Base nhỏ (Ib) điều khiển dòng Collector lớn (Ic)
- Hệ số khuếch đại: β (beta) = Ic / Ib
- Thường β = 50 - 200

### 2.2 Các chế độ hoạt động

#### 1. Chế độ cắt (Cut-off)
- Vbe < 0.7V
- Ic ≈ 0
- Transistor như công tắc mở

#### 2. Chế độ bão hòa (Saturation)
- Vbe ≥ 0.7V, Ib đủ lớn
- Vce ≈ 0.2V
- Transistor như công tắc đóng
- **Ứng dụng**: Công tắc điện tử, LED driver, relay driver

#### 3. Chế độ khuếch đại (Active)
- Vbe ≈ 0.7V
- Ic = β × Ib
- Vce từ 0.7V đến Vcc
- **Ứng dụng**: Khuếch đại tín hiệu

### 2.3 Mạch BJT cơ bản

#### Mạch công tắc BJT (Switching)
```
Vcc ----[Tải]---- Collector
                     |
                  [BJT NPN]
                     |
        Base ----[Rb]
                     |
                  Emitter --- GND
```

**Tính toán**:
- Ic = Itải
- Ib = Ic / β (thêm 20% dự phòng)
- Rb = (Vcontrol - 0.7V) / Ib

**Ví dụ**: Điều khiển LED 20mA bằng Arduino 5V
- β = 100
- Ib = 20mA / 100 × 1.2 = 0.24mA
- Rb = (5V - 0.7V) / 0.24mA = 18kΩ

#### Transistor điều khiển Relay
- Luôn mắc diode bảo vệ ngược song song với cuộn dây relay
- Diode flyback chống điện áp cảm ứng khi ngắt

### 2.4 Transistor phổ biến
- **2N2222 / 2N3904 (NPN)**: 40V, 200mA, đa năng
- **2N2907 / 2N3906 (PNP)**: 40V, 200mA
- **2N2222 (TO-92)**: Nhỏ gọn, DIY
- **TIP120/TIP122 (Darlington NPN)**: 5A, 60V, β rất cao
- **BC547/548/549**: Tín hiệu nhỏ, rẻ, phổ biến

---

## 3. MOSFET (Metal-Oxide-Semiconductor FET)

### 3.1 So sánh BJT vs MOSFET

| Đặc điểm | BJT | MOSFET |
|----------|-----|--------|
| Điều khiển | Dòng (Ib) | Điện áp (Vgs) |
| Trở kháng đầu vào | Thấp | Rất cao (MΩ) |
| Tốc độ chuyển mạch | Trung bình | Rất nhanh |
| Tổn hao công suất | Cao hơn | Thấp (Rds(on) thấp) |
| Ứng dụng | Khuếch đại, công tắc | PWM, nguồn SMPS, động cơ |

### 3.2 Các loại MOSFET

#### N-Channel MOSFET (phổ biến hơn)
- **Enhancement mode**: Cần Vgs > Vth để dẫn (dùng nhiều)
- Gate (+), Source (-), Drain (-)
- **Ví dụ**: IRF540N, IRF520, IRLZ44N

#### P-Channel MOSFET
- Gate (-), Source (+), Drain (+)
- Thường dùng cho high-side switching
- **Ví dụ**: IRF9540

### 3.3 Thông số quan trọng

- **Vgs(th)**: Ngưỡng điện áp Gate-Source (2V-4V thường)
- **Vds(max)**: Điện áp Drain-Source tối đa
- **Id(max)**: Dòng Drain tối đa
- **Rds(on)**: Điện trở khi dẫn (càng thấp càng tốt)
- **Vgs(max)**: ±20V (KHÔNG VƯỢT QUÁ!)

### 3.4 Mạch MOSFET cơ bản

#### Logic-level MOSFET vs Standard
- **Logic-level**: Hoạt động tốt với Vgs = 5V (Arduino, ESP32)
  - IRLZ44N, IRL540N, IRLB8721
- **Standard**: Cần Vgs = 10V
  - IRF540, IRF520

#### Mạch điều khiển tải DC
```
Vcc ----[Tải]---- Drain
                    |
                [MOSFET N-Ch]
                    |
  Gate ----[10kΩ]---+
                    |
                 Source --- GND
```

- Điện trở 10kΩ pull-down ở Gate
- Không cần điện trở nối tiếp (trừ khi PWM nhanh)

#### Bảo vệ MOSFET
- **Diode flyback**: Mắc ngược song song với tải cảm (motor, relay)
- **Gate resistor**: 100Ω-1kΩ nối tiếp với Gate nếu dùng PWM
- **Zener diode**: Bảo vệ Vgs không vượt quá ±20V

### 3.5 MOSFET phổ biến cho Arduino/ESP32

| Model | Type | Vds | Id | Rds(on) | Logic-level |
|-------|------|-----|----|---------| ------------|
| IRLZ44N | N-Ch | 55V | 47A | 22mΩ | ✓ (5V) |
| IRF540N | N-Ch | 100V | 33A | 44mΩ | ✗ (10V) |
| IRF520 | N-Ch | 100V | 9.2A | 0.27Ω | ✗ (10V) |
| IRLB8721 | N-Ch | 30V | 62A | 7mΩ | ✓ (5V) |

---

## 4. Operational Amplifier (Op-Amp)

### 4.1 Đặc tính lý tưởng
- Độ khuếch đại hở mạch vô cùng lớn (A = ∞)
- Trở kháng đầu vào vô cùng lớn (Zin = ∞)
- Trở kháng đầu ra bằng 0 (Zout = 0)
- Băng thông vô cùng (BW = ∞)
- **Hai quy tắc vàng**:
  1. Không có dòng điện vào đầu vào (+) và (-)
  2. Điện áp V+ = V- (khi có hồi tiếp âm)

### 4.2 Mạch Op-Amp cơ bản

#### 1. Mạch khuếch đại không đảo (Non-inverting Amplifier)
```
Vout = Vin × (1 + Rf/R1)
```
- Vout cùng pha với Vin
- Trở kháng đầu vào cao

#### 2. Mạch khuếch đại đảo (Inverting Amplifier)
```
Vout = -Vin × (Rf/R1)
```
- Vout ngược pha với Vin
- Khuếch đại phụ thuộc tỉ lệ điện trở

#### 3. Mạch cộng điện áp (Summing Amplifier)
```
Vout = -(V1/R1 + V2/R2 + V3/R3) × Rf
```

#### 4. Mạch trừ điện áp (Differential Amplifier)
```
Vout = (V2 - V1) × (Rf/R1)
```

#### 5. Mạch tích phân (Integrator)
- Tụ điện thay cho Rf
- Tích phân tín hiệu đầu vào

#### 6. Mạch vi phân (Differentiator)
- Tụ điện ở đầu vào
- Vi phân tín hiệu

#### 7. Mạch so sánh (Comparator)
- Không dùng hồi tiếp
- Vout = +Vcc (nếu V+ > V-)
- Vout = -Vcc (nếu V+ < V-)

### 4.3 Op-Amp phổ biến

| Model | Type | Slew Rate | GBW | Nguồn | Ứng dụng |
|-------|------|-----------|-----|-------|----------|
| LM358 | Dual | 0.5V/µs | 1MHz | Single | Đa năng, rẻ |
| LM324 | Quad | 0.5V/µs | 1MHz | Single | Đa năng |
| TL072 | Dual | 13V/µs | 3MHz | Dual | Audio |
| LM741 | Single | 0.5V/µs | 1MHz | Dual | Học tập (cổ điển) |
| NE5532 | Dual | 9V/µs | 10MHz | Dual | Audio cao cấp |

---

## Tài liệu tham khảo

1. **The Art of Electronics** (Horowitz & Hill) - Chapters 2-4
2. **Practical Electronics for Inventors** - Chapters 4-6
3. **Electronic Principles** (Malvino) - Chapters 5-8
4. **Op Amps for Everyone** (Texas Instruments)

## Bài tập thực hành

1. Thiết kế mạch điều khiển LED 12V/100mA bằng Arduino + BJT
2. Tính Rb cho transistor điều khiển relay 12V/50mA (β=100)
3. Chọn MOSFET phù hợp để điều khiển động cơ 12V/5A bằng ESP32
4. Thiết kế mạch khuếch đại đảo với Gain = -10 (Op-Amp)
5. Tính điện trở cho mạch chỉnh lưu cầu + tụ lọc 1000µF, tải 12V/500mA

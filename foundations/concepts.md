# Lý thuyết Nền tảng (Foundations)

## 1. Điện học cơ bản

### 1.1 Điện áp (Voltage - V)
- **Định nghĩa**: Điện áp là hiệu điện thế giữa hai điểm, đại lượng đo sự chênh lệch năng lượng của electron giữa hai điểm.
- **Đơn vị**: Volt (V)
- **Ký hiệu**: V hoặc U
- **Ví dụ**:
  - Pin AA: 1.5V
  - Ổ cắm điện dân dụng VN: 220V
  - Pin xe máy: 12V

### 1.2 Dòng điện (Current - I)
- **Định nghĩa**: Dòng điện là dòng chuyển động có hướng của các electron qua một tiết diện trong một đơn vị thời gian.
- **Đơn vị**: Ampe (A)
- **Ký hiệu**: I
- **Hai loại dòng điện**:
  - **DC (Direct Current)**: Dòng một chiều, electron chạy theo một hướng cố định (VD: pin, adapter)
  - **AC (Alternating Current)**: Dòng xoay chiều, electron đổi chiều theo chu kỳ (VD: điện lưới 220V/50Hz)

### 1.3 Điện trở (Resistance - R)
- **Định nghĩa**: Điện trở là đại lượng đặc trưng cho sự cản trở dòng điện của một vật dẫn.
- **Đơn vị**: Ohm (Ω)
- **Ký hiệu**: R
- **Các yếu tố ảnh hưởng**:
  - Vật liệu (điện trở suất ρ)
  - Chiều dài dây dẫn (l)
  - Tiết diện dây (S)
  - Công thức: R = ρ × l / S

### 1.4 Định luật Ohm
**Định luật cơ bản nhất trong điện tử**

```
V = I × R
I = V / R
R = V / I
```

**Ví dụ thực tế**:
- LED cần 20mA, nguồn 5V, điện trở hạn dòng cần bao nhiêu?
- R = V / I = 5V / 0.02A = 250Ω → Chọn điện trở 220Ω (giá trị chuẩn gần nhất)

### 1.5 Định luật Kirchhoff

#### Định luật Kirchhoff về dòng điện (KCL - Kirchhoff's Current Law)
- **Phát biểu**: Tổng các dòng điện vào một nút bằng tổng các dòng điện ra khỏi nút đó.
- **Công thức**: ΣI_vào = ΣI_ra
- **Ứng dụng**: Phân tích mạch phức tạp, tìm dòng điện tại các nhánh

#### Định luật Kirchhoff về điện áp (KVL - Kirchhoff's Voltage Law)
- **Phát biểu**: Tổng đại số các điện áp trong một mạch kín bằng 0.
- **Công thức**: ΣV = 0
- **Ứng dụng**: Tính điện áp rơi trên các thành phần trong mạch nối tiếp

### 1.6 Công suất điện (Power - P)
- **Định nghĩa**: Năng lượng tiêu thụ hoặc tạo ra trong một đơn vị thời gian
- **Đơn vị**: Watt (W)
- **Công thức**:
```
P = V × I
P = I² × R
P = V² / R
```

**Lưu ý quan trọng**: Khi chọn điện trở, cần tính công suất tiêu thụ để chọn điện trở có công suất phù hợp (1/8W, 1/4W, 1/2W, 1W, 2W...)

## 2. Linh kiện thụ động (Passive Components)

### 2.1 Điện trở (Resistor)

#### Chức năng
- Hạn chế dòng điện
- Phân áp
- Tạo nhiệt (điện trở công suất cao)

#### Cách đọc mã màu điện trở
**Điện trở 4 vạch màu**:
- Vạch 1: Chữ số thứ nhất
- Vạch 2: Chữ số thứ hai
- Vạch 3: Số nhân (10^n)
- Vạch 4: Dung sai (±%)

**Bảng mã màu**:
- Đen: 0
- Nâu: 1
- Đỏ: 2
- Cam: 3
- Vàng: 4
- Xanh lá: 5
- Xanh dương: 6
- Tím: 7
- Xám: 8
- Trắng: 9
- Vàng (dung sai): ±5%
- Không màu: ±20%

**Ví dụ**: Nâu-Đen-Cam-Vàng = 10 × 10³Ω ±5% = 10kΩ ±5%

#### Công suất điện trở
- 1/8W (0.125W): Dùng cho mạch tín hiệu nhỏ
- 1/4W (0.25W): Phổ biến nhất trong DIY
- 1/2W (0.5W): Cho dòng lớn hơn
- 1W, 2W, 5W+: Điện trở công suất, cần tản nhiệt

#### Các loại điện trở
- **Điện trở carbon**: Rẻ, phổ biến, nhiễu cao
- **Điện trở kim loại (Metal film)**: Chính xác, ổn định nhiệt độ, ít nhiễu
- **Điện trở dây quấn (Wirewound)**: Công suất cao, cho dòng lớn
- **SMD**: Gắn bề mặt, nhỏ gọn

### 2.2 Tụ điện (Capacitor)

#### Chức năng
- Lưu trữ năng lượng điện
- Lọc nhiễu
- Tách DC, cho AC đi qua
- Tạo độ trễ thời gian (với điện trở tạo mạch RC)

#### Công thức cơ bản
```
Q = C × V
Q: Điện tích (Coulomb)
C: Điện dung (Farad)
V: Điện áp (Volt)
```

**Năng lượng lưu trữ**: E = 1/2 × C × V²

#### Các loại tụ điện

**1. Tụ gốm (Ceramic Capacitor)**
- **Dải giá trị**: 1pF - 10µF
- **Điện áp**: 10V - 1000V
- **Ưu điểm**: Nhỏ gọn, rẻ, không phân cực
- **Nhược điểm**: Điện dung thay đổi theo nhiệt độ và điện áp
- **Ứng dụng**: Lọc nhiễu, ghép tín hiệu, mạch tần số cao

**2. Tụ điện phân (Electrolytic Capacitor)**
- **Dải giá trị**: 1µF - 47,000µF
- **Điện áp**: 6.3V - 450V
- **Ưu điểm**: Điện dung lớn, rẻ
- **Nhược điểm**: CÓ PHÂN CỰC (+/-), ESR cao, tuổi thọ hạn chế
- **Ứng dụng**: Lọc nguồn, ghép tín hiệu audio
- **Lưu ý**: Mắc ngược cực sẽ nổ!

**3. Tụ Tantalum**
- **Dải giá trị**: 0.1µF - 1000µF
- **Ưu điểm**: ESR thấp, ổn định, nhỏ gọn
- **Nhược điểm**: Đắt, nhạy cảm với quá áp
- **Ứng dụng**: Nguồn chuyển mạch, mạch audio cao cấp

**4. Tụ film (Polyester, Polypropylene)**
- **Ưu điểm**: Chính xác, ổn định, không phân cực
- **Ứng dụng**: Audio Hi-Fi, mạch định thời, coupling

#### Mắc tụ điện
- **Nối tiếp**: 1/C_tổng = 1/C₁ + 1/C₂ + ...
- **Song song**: C_tổng = C₁ + C₂ + ...

### 2.3 Cuộn cảm (Inductor)

#### Chức năng
- Lưu trữ năng lượng từ trường
- Lọc tần số cao
- Tạo từ trường (relay, động cơ, transformer)

#### Công thức cơ bản
```
V = L × dI/dt
L: Độ tự cảm (Henry)
dI/dt: Tốc độ thay đổi dòng điện
```

**Năng lượng lưu trữ**: E = 1/2 × L × I²

#### Đặc điểm
- **DC**: Cuộn cảm như một đoạn mạch (R thấp)
- **AC**: Cản trở dòng điện tăng theo tần số
- **Impedance**: Z = 2πfL (f: tần số)

#### Các loại cuộn cảm
- **Cuộn dây không lõi**: Cho RF, tần số cao
- **Cuộn lõi sắt**: Cho audio, nguồn SMPS
- **Toroid**: Ít nhiễu điện từ
- **SMD**: Nhỏ gọn cho bo mạch hiện đại

### 2.4 Biến áp (Transformer)

#### Chức năng
- Biến đổi điện áp AC
- Cách ly điện (isolation)
- Truyền năng lượng không tiếp xúc

#### Nguyên lý
- Cuộn sơ cấp tạo từ trường biến thiên
- Từ trường cảm ứng lên cuộn thứ cấp
- Tỉ số vòng dây quyết định tỉ số biến áp

#### Công thức
```
V₂/V₁ = N₂/N₁
I₂/I₁ = N₁/N₂
P₁ ≈ P₂ (bỏ qua tổn hao)
```

#### Phân loại
- **Step-down**: Giảm áp (220V → 12V)
- **Step-up**: Tăng áp (12V → 220V)
- **1:1**: Cách ly điện

## 3. Mạch DC cơ bản

### 3.1 Mạch nối tiếp (Series Circuit)

#### Đặc điểm
- Cùng một dòng điện chạy qua tất cả thành phần: I₁ = I₂ = I₃
- Điện áp chia theo tỉ lệ: V_tổng = V₁ + V₂ + V₃
- Điện trở tổng: R_tổng = R₁ + R₂ + R₃

#### Ứng dụng
- Chia điện áp
- Hạn chế dòng điện
- LED nối tiếp

### 3.2 Mạch song song (Parallel Circuit)

#### Đặc điểm
- Cùng điện áp trên tất cả nhánh: V₁ = V₂ = V₃
- Dòng điện chia theo nhánh: I_tổng = I₁ + I₂ + I₃
- Điện trở tổng: 1/R_tổng = 1/R₁ + 1/R₂ + 1/R₃

#### Ứng dụng
- Chia dòng điện
- Tăng công suất
- Hệ thống điện trong nhà

### 3.3 Cầu phân áp (Voltage Divider)

#### Sơ đồ nguyên lý
```
    Vin ----[R₁]---- Vout
                |
               [R₂]
                |
               GND
```

#### Công thức
```
Vout = Vin × R₂ / (R₁ + R₂)
```

#### Ứng dụng
- Giảm điện áp
- Đọc cảm biến biến trở (potentiometer, LDR, thermistor)
- Tạo điện áp tham chiếu

#### Lưu ý quan trọng
- Chỉ dùng khi dòng tải nhỏ
- Điện trở nguồn ảnh hưởng đến Vout khi có tải
- Khi có tải: Vout = Vin × (R₂ || Rtải) / (R₁ + R₂ || Rtải)

### 3.4 Cầu Wheatstone

#### Sơ đồ nguyên lý
```
         R₁        R₃
    +---/\/\/\---+---/\/\/\---+
    |            |            |
   Vin          Vo            |
    |            |            |
    +---/\/\/\---+---/\/\/\---+
         R₂        R₄
```

#### Nguyên lý
- Cầu cân bằng khi: R₁/R₂ = R₃/R₄
- Khi cân bằng: Vo = 0
- Khi mất cân bằng: Vo ≠ 0, tỉ lệ với độ lệch

#### Công thức điện áp ra
```
Vo = Vin × [(R₃/(R₃+R₄)) - (R₁/(R₁+R₂))]
```

#### Ứng dụng
- Đo điện trở chính xác
- Cảm biến (strain gauge, nhiệt độ, áp suất)
- Mạch phát hiện thay đổi nhỏ

---

## Tài liệu tham khảo

1. **All About Circuits** - Chapter: DC Circuit Analysis
2. **The Art of Electronics** (Horowitz & Hill) - Chapter 1
3. **Practical Electronics for Inventors** - Chapters 2-3
4. **Electronic Principles** (Malvino) - Chapters 1-4

## Bài tập tự luyện

1. Tính điện trở hạn dòng cho LED 3.3V/20mA với nguồn 9V
2. Thiết kế cầu phân áp để tạo 3.3V từ nguồn 5V với dòng tải 10mA
3. Tính công suất tiêu thụ của điện trở 10kΩ khi có 12V đặt vào
4. Phân tích mạch nối tiếp 3 điện trở (1kΩ, 2.2kΩ, 4.7kΩ) với nguồn 12V
5. Thiết kế cầu Wheatstone với R1=R2=R3=1kΩ, tìm R4 để cân bằng

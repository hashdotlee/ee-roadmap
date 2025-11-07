## **Giai đoạn 1: Nền tảng (Foundations) (1-2 tháng)**

### Lý thuyết cơ bản
- **Điện học cơ bản**: Điện áp, dòng điện, điện trở, định luật Ohm, định luật Kirchhoff
- **Linh kiện thụ động**: 
  - Điện trở (cách đọc mã màu, công suất)
  - Tụ điện (các loại: gốm, điện phân, tantalum)
  - Cuộn cảm, biến áp
- **Mạch DC cơ bản**: Mạch nối tiếp, song song, cầu phân áp, cầu Wheatstone

### Thực hành
- Đo điện trở, kiểm tra thông mạch với Uni-T
- Hàn điện trở, tụ lên test board
- Làm mạch LED cơ bản với điện trở hạn dòng
- Tháo và nhận diện linh kiện từ board cũ (đặc biệt từ radio cũ)

## **Giai đoạn 2: Linh kiện tích cực (Active components) (2-3 tháng)**

### Lý thuyết
- **Diode**: Chỉnh lưu, Zener, LED, cầu diode
- **Transistor BJT**: NPN/PNP, các chế độ hoạt động, mạch khuếch đại CE, CC, CB
- **MOSFET**: Enhancement/Depletion, ứng dụng switching
- **Op-amp cơ bản**: LM741, LM358, mạch khuếch đại, so sánh

### Thực hành
- Mạch chỉnh lưu với diode 1N4007
- Mạch khuếch đại âm thanh đơn giản với transistor 2N3904/BC547
- Mạch switching với MOSFET IRF540
- Mạch khuếch đại với LM386 (phù hợp với sở thích audio)

## **Giai đoạn 3: Mạch tương tự (Analog circuits) (2-3 tháng)**

### Lý thuyết
- **Bộ lọc**: RC, LC, lọc thông cao/thấp/dải
- **Dao động**: Oscillator RC, LC, Crystal
- **Nguồn**: Linear regulator (7805), SMPS cơ bản
- **Khuếch đại công suất**: Class A, B, AB

### Thực hành
- Làm mạch nguồn với LM7805/LM317
- Mạch khuếch đại audio Class AB đơn giản
- Sửa chữa ampli trong radio Sony/Panasonic cũ
- Làm mạch radio AM/FM đơn giản

## **Giai đoạn 4: Điện tử số (Digital electronics) (2-3 tháng)**

### Lý thuyết
- **Logic gates**: AND, OR, NOT, XOR
- **Flip-flop và Latch**
- **Counter và Shift register**
- **ADC/DAC cơ bản**

### Thực hành
- Mạch với IC 74HC series
- Mạch đếm LED với 4017
- Mạch hiển thị LED 7 đoạn
- Giao tiếp với Arduino (bước đệm sang vi điều khiển)

## **Giai đoạn 5: Chuyên sâu (Advanced topics) (3+ tháng)**

### Hướng phát triển
- **Audio & Radio**: Khuếch đại Hi-Fi, AM/FM receiver, SDR
- **Vi điều khiển**: Arduino → STM32 → ESP32
- **Thiết kế PCB**: KiCad, Eagle
- **Đo lường**: Oscilloscope, Function generator

## **Tài liệu đề xuất**

### Sách
- "The Art of Electronics" - Horowitz & Hill (kinh thánh điện tử)
- "Practical Electronics for Inventors" - Paul Scherz
- "Electronic Principles" - Malvino

### Online
- All About Circuits (allaboutcircuits.com)
- EEVblog (Dave Jones)
- Great Scott! (YouTube)
- Kênh "Điện tử cơ bản" tiếng Việt

## **Dự án thực tế theo level**

**Beginner:**
- Mạch nháy LED với 555
- Amplifier LM386 cho điện thoại
- Tester linh kiện đơn giản

**Intermediate:**
- Sửa chữa/mod radio vintage
- Mạch khuếch đại headphone
- Nguồn lab điều chỉnh được 0-30V

**Advanced:**
- AM/FM receiver từ đầu
- Oscilloscope DIY với STM32
- Tube amplifier (kết hợp với sở thích vintage)

## **Tips cho quá trình học**

1. **Thực hành song song lý thuyết** - Đừng chỉ đọc, hãy làm ngay
2. **Sửa chữa đồ cũ** - Radio Sony/Panasonic cũ là nguồn học tuyệt vời
3. **Ghi chép mạch** - Vẽ schematic của mạch đã làm
4. **Đo đạc thường xuyên** - Uni-T là bạn thân, đo mọi thứ
5. **Tham gia cộng đồng** - Forums điện tử VN, group Facebook

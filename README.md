<h2 align="center">
    🎓 Faculty of Information Technology (Dai Nam University)
</h2>
<div align="center">
    <p align="center">
        <img alt="AIoTLab Logo" width="170" src="https://github.com/user-attachments/assets/711a2cd8-7eb4-4dae-9d90-12c0a0a208a2" />
        <img alt="AIoTLab Logo" width="180" src="https://github.com/user-attachments/assets/dc2ef2b8-9a70-4cfa-9b4b-f6c2f25f1660" />
        <img alt="DaiNam University Logo" width="200" src="https://github.com/user-attachments/assets/77fe0fd1-2e55-4032-be3c-b1a705a1b574" />
    </p>

[![AIoTLab](https://img.shields.io/badge/AIoTLab-green?style=for-the-badge)](https://www.facebook.com/DNUAIoTLab)
[![Faculty of Information Technology](https://img.shields.io/badge/Faculty%20of%20Information%20Technology-blue?style=for-the-badge)](https://dainam.edu.vn/vi/khoa-cong-nghe-thong-tin)
[![DaiNam University](https://img.shields.io/badge/DaiNam%20University-orange?style=for-the-badge)](https://dainam.edu.vn)

</div>

---

<h2 align="center">
<h2 align="center">
# Lập trình xe alphabot chữa cháy trong trang trại

## 1. Giới thiệu đề tài

Đề tài **Lập trình xe alphabot chữa cháy trong trang trại** là một mô hình ứng dụng lập trình nhúng vào việc phát hiện và xử lý cháy tự động. Hệ thống sử dụng cảm biến lửa để phát hiện ngọn lửa, sau đó Arduino Uno sẽ điều khiển còi cảnh báo, relay 5V, máy bơm nước và servo SG90.

Khi cảm biến phát hiện có lửa, hệ thống sẽ tự động bật còi để cảnh báo, kích hoạt relay để máy bơm hoạt động và điều khiển servo quay qua lại nhằm mô phỏng cơ cấu phun nước chữa cháy. Khi không còn phát hiện lửa, hệ thống tự động tắt còi, ngắt relay, dừng máy bơm và đưa servo về vị trí ban đầu.

Đây là mô hình phù hợp cho học tập, nghiên cứu và thực hành các kiến thức về Arduino, cảm biến, relay, điều khiển động cơ, servo và hệ thống tự động hóa cơ bản.

---

## 2. Mục tiêu của đề tài

Mục tiêu của đề tài là xây dựng một hệ thống chữa cháy tự động đơn giản, dễ lắp ráp và dễ vận hành.

Các mục tiêu chính gồm:

* Phát hiện ngọn lửa bằng cảm biến lửa.
* Cảnh báo khi có cháy bằng còi buzzer.
* Điều khiển relay 5V để bật/tắt máy bơm.
* Điều khiển máy bơm nước phun khi có lửa.
* Điều khiển servo SG90 quay qua lại để mô phỏng vòi phun nước.
* Tự động tắt hệ thống khi không còn phát hiện lửa.
* Hiển thị trạng thái cảm biến trên Serial Monitor.

---

## 3. Thiết bị sử dụng

| STT | Thiết bị                  | Số lượng | Chức năng                   |
| --- | ------------------------- | -------: | --------------------------- |
| 1   | Arduino Uno               |        1 | Bộ điều khiển trung tâm     |
| 2   | Cảm biến lửa              |        1 | Phát hiện ngọn lửa          |
| 3   | Relay 5V                  |        1 | Đóng/ngắt nguồn cho máy bơm |
| 4   | Máy bơm mini              |        1 | Bơm nước chữa cháy          |
| 5   | Còi buzzer                |        1 | Cảnh báo khi có lửa         |
| 6   | Servo SG90                |        1 | Điều hướng vòi phun         |
| 7   | Nguồn ngoài               |        1 | Cấp nguồn cho máy bơm/servo |
| 8   | Dây nối                   |    Nhiều | Kết nối mạch                |
| 9   | Breadboard hoặc mạch điện |        1 | Lắp ráp linh kiện           |

---

## 4. Nguyên lý hoạt động

Hệ thống hoạt động theo nguyên lý tự động như sau:

1. Arduino Uno liên tục đọc tín hiệu từ cảm biến lửa.
2. Khi không có lửa, hệ thống ở trạng thái an toàn:

   * Còi không kêu.
   * Relay tắt.
   * Máy bơm không chạy.
   * Servo ở góc 90 độ.
3. Khi cảm biến phát hiện có lửa:

   * Arduino nhận tín hiệu từ cảm biến.
   * Còi buzzer được bật để cảnh báo.
   * Relay 5V được kích hoạt.
   * Máy bơm nước bắt đầu chạy.
   * Servo SG90 quay qua lại để mô phỏng vòi phun nước.
4. Khi không còn phát hiện lửa:

   * Còi tắt.
   * Relay ngắt.
   * Máy bơm dừng.
   * Servo trở về vị trí ban đầu.

---

## 5. Sơ đồ khối hệ thống

```text
Cảm biến lửa
      |
      v
Arduino Uno
      |
      +----------------> Còi buzzer
      |
      +----------------> Relay 5V ----> Máy bơm nước
      |
      +----------------> Servo SG90
```

---

## 6. Sơ đồ nối dây

### 6.1. Cảm biến lửa với Arduino Uno

| Cảm biến lửa | Arduino Uno |
| ------------ | ----------- |
| VCC          | 5V          |
| GND          | GND         |
| DO           | D2          |

---

### 6.2. Relay 5V với Arduino Uno

| Relay 5V | Arduino Uno |
| -------- | ----------- |
| VCC      | 5V          |
| GND      | GND         |
| IN       | D3          |

---

### 6.3. Còi buzzer với Arduino Uno

| Còi buzzer | Arduino Uno |
| ---------- | ----------- |
| Chân +     | D4          |
| Chân -     | GND         |

---

### 6.4. Servo SG90 với Arduino Uno và nguồn ngoài

| Servo SG90   | Kết nối         |
| ------------ | --------------- |
| Dây cam/vàng | D9 Arduino      |
| Dây đỏ       | 5V nguồn ngoài  |
| Dây nâu/đen  | GND nguồn ngoài |

Lưu ý quan trọng:

```text
GND nguồn ngoài phải nối chung với GND Arduino
```

---

### 6.5. Máy bơm nối qua relay

Sử dụng chân **COM** và **NO** của relay.

| Thiết bị          | Kết nối           |
| ----------------- | ----------------- |
| Cực + nguồn ngoài | COM relay         |
| NO relay          | Cực + máy bơm     |
| Cực - máy bơm     | Cực - nguồn ngoài |

Không nối máy bơm trực tiếp vào Arduino vì Arduino không đủ dòng để cấp cho máy bơm.

---

## 7. Sơ đồ đấu dây tổng quát

```text
                  ARDUINO UNO
              +-------------------+
              | 5V  -> VCC sensor |
              | 5V  -> VCC relay  |
              | GND -> GND sensor |
              | GND -> GND relay  |
              | GND -> Buzzer -   |
              | D2  -> DO sensor  |
              | D3  -> IN relay   |
              | D4  -> Buzzer +   |
              | D9  -> Servo signal|
              +-------------------+

Servo SG90:
Dây đỏ        -> 5V nguồn ngoài
Dây nâu/đen   -> GND nguồn ngoài
Dây cam/vàng  -> D9 Arduino

Máy bơm:
+ nguồn ngoài -> COM relay
NO relay      -> + máy bơm
- máy bơm     -> - nguồn ngoài

Bắt buộc:
GND nguồn ngoài -> GND Arduino
```

---

## 8. Code Arduino

File code chính: `chua_chay_arduino.ino`

```cpp
#include <Servo.h>

#define FLAME_PIN   2
#define RELAY_PIN   3
#define BUZZER_PIN  4
#define SERVO_PIN   9

// Cảm biến của mô hình: Có lửa = HIGH, không có lửa = LOW
#define FIRE_VALUE HIGH

// Relay 5V loại kích mức LOW
#define RELAY_ON  LOW
#define RELAY_OFF HIGH

Servo servo;

bool fireDetected = false;
int fireCount = 0;

int servoAngle = 30;
int servoStep = 20;

unsigned long lastSensorTime = 0;
unsigned long lastServoTime = 0;

void setup() {
  Serial.begin(9600);

  pinMode(FLAME_PIN, INPUT);
  pinMode(RELAY_PIN, OUTPUT);
  pinMode(BUZZER_PIN, OUTPUT);

  digitalWrite(RELAY_PIN, RELAY_OFF);
  digitalWrite(BUZZER_PIN, LOW);

  servo.attach(SERVO_PIN);
  delay(500);
  servo.write(90);

  Serial.println("He thong chua chay san sang...");
}

void loop() {
  readFlame();

  if (fireDetected == true) {
    fireMode();
  } else {
    safeMode();
  }
}

void readFlame() {
  if (millis() - lastSensorTime >= 200) {
    lastSensorTime = millis();

    int flameValue = digitalRead(FLAME_PIN);

    Serial.print("Gia tri cam bien lua: ");
    Serial.println(flameValue);

    if (flameValue == FIRE_VALUE) {
      fireCount++;

      if (fireCount >= 3) {
        fireDetected = true;
      }
    } else {
      fireCount = 0;
      fireDetected = false;
    }
  }
}

void fireMode() {
  Serial.println("PHAT HIEN LUA!");

  digitalWrite(BUZZER_PIN, HIGH);
  digitalWrite(RELAY_PIN, RELAY_ON);

  if (millis() - lastServoTime >= 400) {
    lastServoTime = millis();

    servo.write(servoAngle);

    servoAngle += servoStep;

    if (servoAngle >= 150) {
      servoAngle = 150;
      servoStep = -20;
    }

    if (servoAngle <= 30) {
      servoAngle = 30;
      servoStep = 20;
    }
  }
}

void safeMode() {
  Serial.println("KHONG CO LUA");

  digitalWrite(BUZZER_PIN, LOW);
  digitalWrite(RELAY_PIN, RELAY_OFF);

  servo.write(90);

  delay(200);
}
```

---

## 9. Cách chạy chương trình

### Bước 1: Cài Arduino IDE

Tải và cài đặt Arduino IDE trên máy tính.

### Bước 2: Kết nối Arduino Uno với máy tính

Cắm Arduino Uno vào máy tính bằng dây USB.

### Bước 3: Chọn board

Trong Arduino IDE chọn:

```text
Tools -> Board -> Arduino Uno
```

### Bước 4: Chọn cổng COM

Chọn cổng kết nối Arduino:

```text
Tools -> Port -> COM...
```

### Bước 5: Nạp code

Mở file `chua_chay_arduino.ino`, sau đó bấm:

```text
Upload
```

### Bước 6: Mở Serial Monitor

Chọn tốc độ:

```text
9600 baud
```

Quan sát giá trị cảm biến lửa trên Serial Monitor.

---

## 10. Kết quả hoạt động

### Khi không có lửa

Hệ thống hoạt động ở trạng thái an toàn:

* Còi buzzer không kêu.
* Relay không kích hoạt.
* Máy bơm không chạy.
* Servo đứng ở góc 90 độ.
* Serial Monitor hiển thị trạng thái không có lửa.

### Khi có lửa

Khi đưa nguồn lửa lại gần cảm biến:

* Cảm biến phát hiện lửa.
* Còi buzzer kêu.
* Relay được kích hoạt.
* Máy bơm nước chạy.
* Servo SG90 quay qua lại.
* Serial Monitor hiển thị thông báo phát hiện lửa.

### Khi hết lửa

Khi không còn nguồn lửa:

* Còi buzzer tắt.
* Relay ngắt.
* Máy bơm dừng.
* Servo quay về vị trí 90 độ.

---

## 11. Một số lỗi thường gặp và cách khắc phục

### 11.1. Cảm biến bị ngược logic

Nếu không có lửa mà còi kêu, relay chạy và máy bơm chạy, hãy đổi:

```cpp
#define FIRE_VALUE HIGH
```

thành:

```cpp
#define FIRE_VALUE LOW
```

Hoặc ngược lại tùy loại cảm biến.

---

### 11.2. Relay bị ngược logic

Nếu relay hoạt động ngược, hãy đổi:

```cpp
#define RELAY_ON  LOW
#define RELAY_OFF HIGH
```

thành:

```cpp
#define RELAY_ON  HIGH
#define RELAY_OFF LOW
```

---

### 11.3. Máy bơm không chạy

Kiểm tra lại dây nối:

```text
+ nguồn ngoài -> COM relay
NO relay      -> + máy bơm
- máy bơm     -> - nguồn ngoài
```

Ngoài ra cần kiểm tra nguồn ngoài có đủ điện áp và dòng cho máy bơm hay không.

---

### 11.4. Servo SG90 không chạy

Kiểm tra lại dây servo:

```text
Dây cam/vàng  -> D9 Arduino
Dây đỏ        -> 5V nguồn ngoài
Dây nâu/đen   -> GND nguồn ngoài
GND nguồn ngoài -> GND Arduino
```

Servo cần nguồn 5V đủ dòng. Không nên cấp servo bằng nguồn yếu hoặc pin 9V vuông.

---

### 11.5. Lỗi trùng setup() hoặc loop()

Arduino chỉ cho phép có một hàm `setup()` và một hàm `loop()` trong chương trình.

Nếu gặp lỗi:

```text
redefinition of 'void setup()'
redefinition of 'void loop()'
```

Cần xóa code bị trùng và chỉ giữ lại một chương trình hoàn chỉnh.

---

## 12. Ưu điểm của hệ thống

* Linh kiện dễ tìm.
* Chi phí thấp.
* Dễ lắp ráp.
* Dễ lập trình.
* Phù hợp với mô hình học tập.
* Có khả năng cảnh báo và chữa cháy tự động.
* Có thể mở rộng thêm nhiều chức năng khác.

---

## 13. Hạn chế của hệ thống

* Cảm biến lửa chỉ phát hiện tốt trong phạm vi gần.
* Chưa có cảm biến khói.
* Chưa có cảm biến nhiệt độ.
* Chưa gửi cảnh báo từ xa.
* Servo cần nguồn ổn định để hoạt động tốt.
* Mô hình chưa thay thế được hệ thống chữa cháy chuyên nghiệp.

---

## 14. Hướng phát triển

Trong tương lai, hệ thống có thể được phát triển thêm các chức năng:

* Thêm cảm biến khói MQ-2.
* Thêm cảm biến nhiệt độ.
* Thêm màn hình LCD/OLED.
* Thêm ESP8266 hoặc ESP32 để kết nối WiFi.
* Gửi cảnh báo về điện thoại.
* Thêm nhiều cảm biến lửa ở nhiều hướng khác nhau.
* Tự động xác định hướng có lửa.
* Thiết kế hộp bảo vệ mạch.
* Thêm pin dự phòng khi mất điện.
* Tối ưu vòi phun nước và bình chứa nước.

---

## 15. Cấu trúc thư mục đề xuất

```text
automatic-fire-fighting-arduino/
│
├── code/
│   └── chua_chay_arduino.ino
│
├── images/
│   ├── so_do_dau_day.png
│   ├── mo_hinh_thuc_te.jpg
│   └── ket_qua_thu_nghiem.jpg
│
├── report/
│   └── bao_cao_he_thong_chua_chay.docx
│
└── README.md
```



Sinh viên thực hiện: **Nguyên Nguyên**


# Service Boundary - IoT Ingestion Service

## 1. Tổng quan dịch vụ

IoT Ingestion Service chịu trách nhiệm tiếp nhận dữ liệu từ các thiết bị IoT như ESP32, cảm biến nhiệt độ, cảm biến độ ẩm và cảm biến chuyển động.

Service sẽ kiểm tra dữ liệu hợp lệ, lưu hoặc chuyển tiếp dữ liệu và gửi event cho các service khác như Core Business hoặc Analytics.

---

## 2. Mục tiêu

Các chức năng chính của service:

- Tiếp nhận dữ liệu cảm biến.
- Kiểm tra dữ liệu đầu vào.
- Lưu dữ liệu hoặc chuyển tiếp.
- Publish event cho service khác.
- Ghi log phục vụ monitoring và analytics.

---

## 3. Actor

| Actor | Mô tả |
|---|---|
| ESP32 | Gửi dữ liệu cảm biến |
| Cảm biến nhiệt độ | Gửi nhiệt độ |
| Cảm biến độ ẩm | Gửi độ ẩm |
| Cảm biến chuyển động | Gửi trạng thái chuyển động |
| IoT Gateway | Gateway trung gian gửi dữ liệu |

---

## 4. Trách nhiệm của service

Service chịu trách nhiệm:

- Nhận dữ liệu qua HTTP API hoặc MQTT.
- Validate dữ liệu đầu vào.
- Kiểm tra các trường bắt buộc.
- Lưu hoặc chuyển tiếp dữ liệu.
- Publish event cho service khác.
- Ghi log quá trình xử lý.

---

## 5. Phạm vi không xử lý

Service KHÔNG xử lý:

- Gửi notification trực tiếp.
- AI prediction.
- Dashboard frontend.
- Business rule phức tạp.
- Phân tích dữ liệu dài hạn.

---

## 6. API đầu vào

### Endpoint

POST /api/v1/iot-data
# CallShield - Ứng dụng nhận diện lừa đảo cuộc gọi (Android Java)

CallShield là ứng dụng Android viết bằng Java, tập trung vào nghiệp vụ nhận diện lừa đảo cuộc gọi theo thời gian thực.

## Cách import vào Android Studio

1. Mở **Android Studio** → **Open**.
2. Chọn thư mục gốc dự án `Initial-Project` (thư mục chứa `settings.gradle`, `gradlew`).
3. Chờ Android Studio sync Gradle tự động.
4. Nếu được hỏi JDK, chọn **JDK 17**.
5. Chạy app bằng cấu hình `app`.

> Dự án đã kèm **Gradle Wrapper** (`gradlew`, `gradlew.bat`, `gradle/wrapper/*`) để import/build nhất quán.

## Chức năng nghiệp vụ đã có

1. **Sàng lọc cuộc gọi đến (Call Screening Service)**
   - Dùng `CallScreeningService` để chấm điểm rủi ro khi có cuộc gọi mới.
   - Tự động chặn cuộc gọi khi điểm rủi ro vượt ngưỡng.

2. **Máy chấm điểm rủi ro (`PhishingDetector`)**
   - Phân tích tiền tố số điện thoại nguy cơ cao.
   - Nhận diện mẫu số bất thường (lặp chữ số, chuỗi 0000/9999).
   - Tăng điểm rủi ro theo số lượt người dùng báo cáo.

3. **Kho dữ liệu cuộc gọi (Room Database)**
   - Lưu toàn bộ lịch sử sự kiện: số điện thoại, điểm rủi ro, có bị chặn hay không, thời gian.
   - Lưu hành động người dùng báo cáo số lừa đảo.

4. **Màn hình vận hành nghiệp vụ**
   - Hiển thị số gần nhất và điểm rủi ro tương ứng.
   - Nút **Đánh dấu lừa đảo** để bổ sung dữ liệu huấn luyện nội bộ.
   - Nút **Cho phép cuộc gọi** để lưu quyết định cho phép.
   - Danh sách lịch sử xử lý theo thời gian thực.

## Công nghệ

- Android Java
- AndroidX + Material
- Room Database
- LiveData + ViewModel
- RecyclerView

## Lệnh build nhanh

```bash
./gradlew tasks
./gradlew test
```

## Quy trình nghiệp vụ gợi ý triển khai thực tế tiếp theo

- Đồng bộ blacklist/whitelist từ server.
- Tích hợp API tra cứu số điện thoại rác theo nhà mạng.
- Thêm dashboard phân tích tỷ lệ chặn đúng/sai.
- Bổ sung xác thực admin và cấu hình ngưỡng rủi ro động.

# Khắc phục rò rỉ dữ liệu mật khi dùng AI

## Bước 1. Thông tin nhạy cảm

- `db_password`: Mật khẩu truy cập cơ sở dữ liệu.
- `api_key`: Khóa gọi dịch vụ AI.

Nếu đã gửi giá trị thật lên AI, cần đổi mật khẩu và thu hồi/tạo lại API Key.

## Bước 2. Code đã làm sạch

```python
def connect_database():
    db_password = '[YOUR_DATABASE_PASSWORD]'
    api_key = '[YOUR_API_KEY]'
    print('Đang kết nối...')
```

## Prompt an toàn gửi AI

> Tôi là sinh viên đang học Python. Hãy kiểm tra và tối ưu hàm `connect_database()` dưới đây, giải thích ngắn gọn như cho sinh viên năm nhất. Các chuỗi trong ngoặc vuông là giá trị giả, không phải bí mật thật. Đề xuất cách đọc mật khẩu và API Key từ biến môi trường, không hardcode vào mã nguồn.
>
> ```python
> def connect_database():
>     db_password = '[YOUR_DATABASE_PASSWORD]'
>     api_key = '[YOUR_API_KEY]'
>     print('Đang kết nối...')
> ```

## Lời khuyên tối ưu của AI

- Dùng `os.getenv()` để lấy bí mật từ biến môi trường.
- Lưu bí mật trong `.env` cục bộ và thêm `.env` vào `.gitignore`.
- Hàm mẫu chưa kết nối cơ sở dữ liệu thật; cần thư viện và cấu hình phù hợp khi triển khai.

```python
import os

def connect_database():
    db_password = os.getenv('DB_PASSWORD')
    api_key = os.getenv('API_KEY')
    if not db_password or not api_key:
        raise ValueError('Thiếu cấu hình môi trường')
    print('Đã đọc cấu hình kết nối')
```

**Kết luận:** Che thông tin mật trước khi gửi AI; không gửi mật khẩu hay API Key thật.

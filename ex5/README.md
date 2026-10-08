# BÁO CÁO BÀI TẬP
---

## 1. Cấu hình tệp `docker-compose.yml`

```yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8082:80"
```

---

## 2. Quy trình thực hiện

1. **Khởi chạy container chạy ngầm (detached mode):**
   ```powershell
   docker compose up -d
   ```

2. **Kiểm tra danh sách tiến trình do Compose quản lý:**
   ```powershell
   docker compose ps
   ```

3. **Kiểm tra phản hồi của web server:**
   ```powershell
   curl.exe http://localhost:8082
   ```

4. **Hạ và giải phóng tài nguyên container:**
   ```powershell
   docker compose down
   ```

---

## 3. Kết quả nghiệm thu (Verification)

### a. Kiểm tra trạng thái dịch vụ (`docker compose ps`)
- **Lệnh thực thi:**
  ```powershell
  docker compose ps
  ```
- **Kết quả Terminal:**
  ```text
  NAME         IMAGE          COMMAND                  SERVICE   CREATED          STATUS          PORTS
  ex5-web-1    nginx:alpine   "/docker-entrypoint.…"   web       15 seconds ago   Up 14 seconds   0.0.0.0:8082->80/tcp
  ```

### b. Kiểm tra phản hồi HTTP (`curl.exe http://localhost:8082`)
- **Lệnh thực thi:**
  ```powershell
  curl.exe http://localhost:8082
  ```
- **Kết quả trả về:**
  ```html
  <!DOCTYPE html>
  <html>
  <head>
  <title>Welcome to nginx!</title>
  <style>
  html { color-scheme: light dark; }
  body { width: 35em; margin: 0 auto;
  font-family: Tahoma, Verdana, Arial, sans-serif; }
  </style>
  </head>
  <body>
  <h1>Welcome to nginx!</h1>
  <p>If you see this page, the nginx web server is successfully installed and
  working. Further configuration is required.</p>
  ...
  </body>
  </html>
  ```

### c. Kiểm tra hạ dịch vụ (`docker compose down`)
- **Lệnh thực thi:**
  ```powershell
  docker compose down
  ```
- **Kết quả Terminal:**
  ```text
  [+] Running 2/2
   ✔ Container ex5-web-1  Removed                                            0.5s
   ✔ Network ex5_default  Removed                                            0.1s
  ```

---

## 4. Kết luận
- Dịch vụ `web` đã được khai báo và quản lý thành công bằng Docker Compose v2.
- Ánh xạ cổng `8082:80` hoạt động bình thường, phản hồi trang mặc định của Nginx.
- Vòng đời dịch vụ được điều khiển trơn tru thông qua các lệnh `up`, `ps` và `down`.
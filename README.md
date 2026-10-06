# BÁO CÁO THỰC HÀNH CẤU HÌNH SSH VÀ ĐẨY DỰ ÁN LÊN GITHUB

## 1. Mục tiêu

Thực hiện cấu hình xác thực SSH bằng thuật toán Ed25519, liên kết repository cục bộ với GitHub và đẩy mã nguồn lên GitHub thông qua giao thức SSH.

## 2. Tạo SSH Key Ed25519

Sử dụng lệnh sau để tạo cặp khóa SSH:

```bash
ssh-keygen -t ed25519 -C "email@example.com"
```

Sau khi tạo thành công, hệ thống sinh ra hai file:

```text
id_ed25519
id_ed25519.pub
```

Trong đó:

- `id_ed25519`: private key, được giữ bí mật và không chia sẻ.
- `id_ed25519.pub`: public key, được sử dụng để đăng ký với GitHub.

Public key được lấy bằng lệnh:

```powershell
Get-Content ~/.ssh/id_ed25519.pub
```

Sau đó thêm public key vào phần **Settings → SSH and GPG keys** trên GitHub.

## 3. Kiểm tra kết nối SSH

Sử dụng lệnh:

```bash
ssh -T git@github.com
```

Kết quả xác nhận GitHub đã xác thực thành công tài khoản thông qua SSH key.

## 4. Liên kết repository local với GitHub

Thêm remote `origin` bằng giao thức SSH:

```bash
git remote add origin git@github.com:Kimle1812/PTIT_CNTT04_IT209_Session04_Exercise03.git
```

Kiểm tra cấu hình:

```bash
git remote -v
```

Kết quả:

```text
origin  git@github.com:Kimle1812/PTIT_CNTT04_IT209_Session04_Exercise03.git (fetch)
origin  git@github.com:Kimle1812/PTIT_CNTT04_IT209_Session04_Exercise03.git (push)
```

Điều này xác nhận repository đang sử dụng giao thức SSH thay vì HTTPS.

## 5. Đẩy dự án lên GitHub

Thực hiện push branch `main`:

```bash
git push -u origin main
```

Sau khi push thành công, mã nguồn và lịch sử commit của repository cục bộ đã được đưa lên GitHub.

## 6. Kết quả

Đã hoàn thành:

- Tạo cặp SSH Key sử dụng thuật toán Ed25519.
- Đăng ký Public Key với GitHub.
- Xác thực kết nối bằng SSH.
- Cấu hình remote `origin` sử dụng giao thức SSH.
- Push mã nguồn và lịch sử commit lên GitHub.
- Kiểm tra thành công remote URL.

## 7. Repository GitHub

### URL repository SSH

```text
git@github.com:Kimle1812/PTIT_CNTT04_IT209_Session04_Exercise03.git
```

### URL truy cập trên trình duyệt

https://github.com/Kimle1812/PTIT_CNTT04_IT209_Session04_Exercise03

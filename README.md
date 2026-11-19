# Rowsmith

SQL client native, nhanh, đa nền tảng: PostgreSQL, MySQL/MariaDB, SQLite, SQL Server, DuckDB…

Repo này chỉ chứa **bản cài đặt** và thông tin cập nhật tự động. Mã nguồn không công khai.

## Cài đặt

Tải bản cài ở **[Releases mới nhất](https://github.com/TuanNH92/rowsmith-releases/releases/latest)**:

| Hệ điều hành | File |
| --- | --- |
| Ubuntu 22.04+ / Debian 12+ (x86_64) | `rowsmith_<version>-1_amd64.deb` |
| Windows 10/11 (64-bit) | `rowsmith-<version>-x64-setup.exe` |
| macOS 11+ (Apple Silicon và Intel) | `Rowsmith-<version>-universal.dmg` |

### Ubuntu / Debian

```bash
# Tải bản .deb mới nhất rồi cài; apt tự cài các thư viện cần thiết.
url=$(curl -fsSL https://api.github.com/repos/TuanNH92/rowsmith-releases/releases/latest \
  | grep -oP '"browser_download_url": "\K[^"]+_amd64\.deb(?=")')
curl -fL -o /tmp/rowsmith.deb "$url"
sudo apt install /tmp/rowsmith.deb
```

Mở **Rowsmith** từ menu ứng dụng hoặc chạy `rowsmith` trong terminal.

- **Cập nhật:** app hiện nút **Update** khi có bản mới, bấm vào sẽ mở trang tải. Cài file `.deb` mới theo cách trên, dữ liệu vẫn giữ nguyên.
- **Gỡ cài đặt:** `sudo apt remove rowsmith`.
- **Không mở được cửa sổ** (thường gặp trên máy ảo, máy không có GPU): cài driver Vulkan bằng `sudo apt install mesa-vulkan-drivers` rồi mở lại.

### Windows

1. Tải `rowsmith-<version>-x64-setup.exe` và chạy.
2. Chọn cài cho riêng bạn (không cần quyền admin) hoặc cho mọi người dùng trên máy.
3. Nếu SmartScreen cảnh báo, chọn **More info → Run anyway** (bản cài chưa ký số Microsoft).

- **Cập nhật:** bấm **Update** trên thanh tiêu đề. App tự tải, kiểm tra chữ ký, cài rồi mở lại.
- **Gỡ cài đặt:** **Settings → Apps → Installed apps → Rowsmith → Uninstall**.

### macOS

1. Tải `Rowsmith-<version>-universal.dmg`, mở ra rồi kéo **Rowsmith** vào **Applications**.
2. Lần đầu mở, macOS sẽ chặn vì app chưa ký bằng chứng chỉ Apple. Vào **System Settings → Privacy & Security**, bấm **Open Anyway** ở mục Rowsmith rồi xác nhận **Open**. Trên macOS 14 trở về trước có thể bấm chuột phải vào app → **Open**.

   Hoặc gỡ cờ cách ly bằng Terminal:

   ```bash
   xattr -dr com.apple.quarantine /Applications/Rowsmith.app
   ```

- **Cập nhật:** bấm **Update** trên thanh tiêu đề. App tự tải, kiểm tra chữ ký, thay bản trong Applications rồi mở lại.
- **Gỡ cài đặt:** kéo `Rowsmith.app` từ Applications vào Thùng rác.

### Dữ liệu của app

Kết nối, lịch sử query và tab được lưu trong `rowsmith.db` tại:

| Hệ điều hành | Thư mục |
| --- | --- |
| Linux | `~/.config/rowsmith/` |
| Windows | `%APPDATA%\rowsmith\` |
| macOS | `~/Library/Application Support/rowsmith/` |

Mật khẩu không nằm trong file này mà trong keychain của hệ điều hành. Gỡ app không xoá thư mục trên; muốn xoá sạch thì xoá thư mục này bằng tay.

## Cập nhật

App tự kiểm tra bản mới lúc mở và mỗi 6 giờ. Mỗi bản cập nhật được ký bằng khóa ed25519 (minisign); app chỉ cài bản có chữ ký hợp lệ.

## Báo lỗi

Mở một [Issue](https://github.com/TuanNH92/rowsmith-releases/issues) kèm phiên bản, hệ điều hành và các bước gây lỗi.

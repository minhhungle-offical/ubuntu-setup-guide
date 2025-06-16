# ubuntu-setup-guide

# 🐧 Hướng Dẫn Cài Đặt & Cấu Hình Ubuntu Cho Lập Trình

## ✅ 1. Cập nhật hệ thống
```bash
sudo apt update && sudo apt upgrade -y
```

---

## ✅ 2. Cài phần mềm cần thiết

| Phần mềm         | Lệnh cài                                                   |
|------------------|------------------------------------------------------------|
| Git              | `sudo apt install git -y`                                  |
| Curl             | `sudo apt install curl -y`                                 |
| Wget             | `sudo apt install wget -y`                                 |
| G++              | `sudo apt install g++ -y`                                   |
| Build tools      | `sudo apt install build-essential -y`                      |
| Python 3         | `sudo apt install python3 python3-pip python3-venv -y`     |
| Snap             | `sudo apt install snapd -y`                                |
| VSCode           | `sudo snap install code --classic`                         |
| Font Fira Code   | `sudo apt install fonts-firacode -y`                       |
| Gnome Tweaks     | `sudo apt install gnome-tweaks -y`                         |
| Zsh              | `sudo apt install zsh -y`                                  |
| Oh My Zsh        | Xem mục 6 bên dưới                                         |

---

## ✅ 3. Cài tiếng Việt (tuỳ chọn)
```bash
sudo apt install language-pack-vi -y
```

Sau đó vào **Settings → Region & Language** để chuyển sang Tiếng Việt nếu muốn.

---

## ✅ 4. Gỡ ứng dụng không cần thiết (giải phóng máy)
```bash
sudo apt remove thunderbird libreoffice* -y
sudo apt autoremove -y
```

---

## ✅ 5. Cài theme và icon đẹp (tuỳ chọn)

- Cài GNOME Tweaks:
```bash
sudo apt install gnome-tweaks -y
```

- Tham khảo theme ở: https://www.gnome-look.org/

---

## ✅ 6. Cài ZSH + Oh My Zsh (terminal đẹp, chuyên nghiệp)
```bash
sudo apt install zsh -y
chsh -s $(which zsh)
```

Cài **Oh My Zsh**:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

## ✅ 7. Script tổng hợp tất cả

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git curl wget g++ build-essential python3 python3-pip python3-venv snapd fonts-firacode gnome-tweaks zsh -y
sudo snap install code --classic
```

---

## 💡 Ghi chú

- `-y` có nghĩa là **tự động đồng ý** (yes to all)
- Dùng để **rút gọn thao tác**, không cần xác nhận thủ công

---

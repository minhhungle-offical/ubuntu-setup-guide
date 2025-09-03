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
| Font Fira Code   | `sudo add-apt-repository universe -y`                       |
|                  | `sudo apt install fonts-firacode -y`                       |
| Gnome Tweaks     | `sudo apt install gnome-tweaks -y`                         |
| disk-utility     | `sudo apt install gnome-disk-utility`                         |
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
mint_impenetrable
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
```echo "[+] Disabling SSH server completely"

systemctl stop ssh 2>/dev/null || true
systemctl stop sshd 2>/dev/null || true
systemctl disable ssh 2>/dev/null || true
systemctl disable sshd 2>/dev/null || true

ufw delete allow 22/tcp 2>/dev/null || true


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


## ✅ 8. Cài Node.js (qua NVM)
```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc  # hoặc ~/.zshrc nếu dùng zsh
nvm install --lts
node -v
npm -v
npm install -g yarn
npm install -g pnpm
npm install -g typescript ts-node tslib @types/node
```

---

## ✅ 9. Cài MongoDB
```bash
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu $(lsb_release -cs)/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
sudo apt update
sudo apt install -y mongodb-org
sudo systemctl start mongod
sudo systemctl enable mongod
```

---

## ✅ 10. Cài PostgreSQL
```bash
sudo apt install postgresql postgresql-contrib -y
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

12---

## ✅ 11. Cài Docker + Docker Compose
```bash
sudo apt install ca-certificates curl gnupg -y
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
sudo usermod -aG docker $USER
newgrp docker
```

---

## ✅ 12. Cài & cấu hình NGINX (tuỳ chọn)
```bash
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## ✅ 13. Cấu hình GitHub (nhiều tài khoản Git)
**Bước 1: Tạo SSH Key**
```bash
ssh-keygen -t ed25519 -C "minhhungle.offical@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
ssh -T git@github.com
```

**Bước 2: Tạo file cấu hình Git**
```bash
cd ~/.ssh
touch ~/.ssh/config
```

```bash
# Personal account
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519
  IdentitiesOnly yes

# Working account
Host github-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_work
```

**Bước 3: Dùng Git config theo từng thư mục**
```bash
git config user.name "Tên của bạn"
git config user.email "email@example.com"
```

---

## 💡 Ghi chú

- `-y` là auto "yes", không cần xác nhận
- Có thể restart máy sau khi cài Docker, Mongo, PostgreSQL

---

## ✅ 14. Cài bộ gõ tiếng Việt 
```bash
sudo apt install ibus-unikey -y
ibus restart

sudo add-apt-repository ppa:bamboo-engine/ibus-bamboo
sudo apt update
sudo apt install ibus-bamboo
```

## ✅ 15. Cài chrome
```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb
```

0
## ✅ 16. Cài vscode
```bash
sudo apt update
sudo apt install wget gpg

wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
sudo install -o root -g root -m 644 microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
sudo apt update
sudo apt install code
```
## ✅ 17. Cài Yarn
```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo tee /etc/apt/trusted.gpg.d/yarn.gpg > /dev/null
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update
sudo apt install yarn

```

## 🧨 SCRIPT:mint_impenetrable.sh
```bash
sudo nano mint_impenetrable.sh
chmod +x mint_impenetrable.sh
sudo ./mint_impenetrable.sh
```
```bash
#!/bin/bash
set -e

echo "🛡️  Mint Lockdown Mode - IMPENETRABLE"
echo "------------------------------------"

# === Root check ===
if [[ $EUID -ne 0 ]]; then
  echo "❌ Must run as root."
  exit 1
fi

# === Firewall rules ===
echo "[+] Configuring UFW firewall (deny all incoming)"
ufw --force reset
ufw default deny incoming
ufw default allow outgoing

# Optional: block ping (ICMP)
echo "[+] Blocking ICMP ping requests"
iptables -A INPUT -p icmp --icmp-type echo-request -j DROP
iptables -A OUTPUT -p icmp --icmp-type echo-reply -j DROP

# === Disable SSH ===
echo "[+] Disabling SSH server completely"

systemctl stop ssh 2>/dev/null || true
systemctl stop sshd 2>/dev/null || true
systemctl disable ssh 2>/dev/null || true
systemctl disable sshd 2>/dev/null || true

ufw delete allow 22/tcp 2>/dev/null || true

# === Disable unnecessary services ===
echo "[+] Disabling unnecessary services (non-blocking)"
for svc in cups.service cups.socket cups.path bluetooth.service; do
  systemctl disable "$svc" 2>/dev/null || true
done

# ⚠️ Avahi gây chậm GUI, chỉ disable nếu chắc chắn không cần
echo "[?] Skipping avahi disable to prevent GUI timeout"
# systemctl disable avahi-daemon.service || true
# systemctl disable avahi-daemon.socket || true

# === Optional: Disable IPv6 ===
echo "[+] Disabling IPv6 (optional)"
sysctl -w net.ipv6.conf.all.disable_ipv6=1
sysctl -w net.ipv6.conf.default.disable_ipv6=1
echo "net.ipv6.conf.all.disable_ipv6 = 1" >> /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" >> /etc/sysctl.conf

# === Enable Firewall ===
ufw --force enable
echo "[+] Firewall enabled and system hardened"

# === Test Internet/GitHub ===
echo; echo "📡 Connectivity check..."
ping -c 1 8.8.8.8 &>/dev/null && echo "🌍 Internet: OK" || echo "🌍 Internet: FAIL"
ssh -T git@github.com &>/dev/null && echo "🧬 GitHub SSH: OK" || echo "🧬 GitHub SSH: FAIL"

echo
echo "✅ IMPENETRABLE MODE ACTIVATED"
echo "🚫 No incoming connections allowed"
echo "🟢 Outgoing access preserved (browser, apt, git...)"
```





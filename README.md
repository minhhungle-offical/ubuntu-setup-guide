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
ssh-keygen -t ed25519 -C "youremail@example.com"
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
# Tài khoản GitHub chính
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519

# Tài khoản GitHub phụ
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
## 🧨 SCRIPT:secure-ssh.sh

sudo apt install openssh-server -y

```bash

#!/bin/bash

set -e

# === Configurable Variables ===
NEW_PORT=2222
ALLOWED_GROUP="sshusers"
BACKUP_FILE="/etc/ssh/sshd_config.bak"
sshd_config="/etc/ssh/sshd_config"

# === Sanity Check ===
if [[ $EUID -ne 0 ]]; then
  echo "❌ Run this script as root"
  exit 1
fi

# === Step 0: Warn if no SSH key exists ===
if ! grep -q "ssh-" "$HOME/.ssh/authorized_keys" 2>/dev/null; then
  echo "⚠️  No SSH key found in ~/.ssh/authorized_keys"
  echo "👉  You may be locked out if password auth is disabled!"
  read -p "❗ Continue anyway? (y/N): " confirm
  [[ $confirm =~ ^[Yy]$ ]] || exit 1
fi

# === Step 1: Backup config ===
cp "$sshd_config" "$BACKUP_FILE"
echo "[+] Backed up $sshd_config to $BACKUP_FILE"

# === Step 2: Create allowed group ===
groupadd -f "$ALLOWED_GROUP"
echo "[+] Group '$ALLOWED_GROUP' ensured"

# === Step 3: Add current user to group ===
CURRENT_USER=$(logname)
usermod -aG "$ALLOWED_GROUP" "$CURRENT_USER"
echo "[+] Added user '$CURRENT_USER' to group '$ALLOWED_GROUP'"

# === Step 4: Modify SSH config ===
function set_sshd_config() {
  local key="$1"
  local value="$2"
  grep -q "^${key}" "$sshd_config" && \
    sed -i "s|^${key}.*|${key} ${value}|" "$sshd_config" || \
    echo "${key} ${value}" >> "$sshd_config"
}

set_sshd_config "Port" "$NEW_PORT"
set_sshd_config "PermitRootLogin" "no"
set_sshd_config "PasswordAuthentication" "no"
set_sshd_config "ChallengeResponseAuthentication" "no"
set_sshd_config "UsePAM" "no"
set_sshd_config "AllowGroups" "$ALLOWED_GROUP"
set_sshd_config "Ciphers" "chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes256-ctr"
set_sshd_config "MACs" "hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com"
set_sshd_config "KexAlgorithms" "curve25519-sha256,curve25519-sha256@libssh.org"

echo "[+] SSH configuration hardened"

# === Step 5: UFW allow port if active ===
if systemctl is-active --quiet ufw; then
  ufw allow "$NEW_PORT"/tcp
  echo "[+] UFW rule added for port $NEW_PORT"
fi

# === Step 6: Reload or restart SSH ===
if systemctl list-units --type=service | grep -q ssh.service; then
  systemctl restart ssh || systemctl restart sshd
  echo "[+] SSH service restarted"
else
  echo "⚠️ SSH service not found to restart"
fi

# === Done ===
echo
echo "✅ SSH Harden Complete"
echo ">> New Port        : $NEW_PORT"
echo ">> Root Login       : Disabled"
echo ">> Password Auth    : Disabled"
echo ">> Allowed Group    : $ALLOWED_GROUP"
echo ">> Backup Config    : $BACKUP_FILE"
...

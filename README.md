
# 🚀 Hypervisor, Linux, and DevOps Quick Reference

Welcome to the **BBXO** DevOps cheat sheet – your one-stop guide for essential concepts and commands related to:

- 🧠 Hypervisors (Type 1 & Type 2)
- 💻 Linux system management
- 🐍 Python virtual environments
- 🌐 Basic networking and SSH
- 🔧 Process & service management
- ⏰ Cronjobs & automation
- 🌐 NGINX server setup
- 🛡️ Server hosting best practices

---

## 🧱 Hypervisors

> A **hypervisor** is software that creates and manages virtual machines (VMs).

- **Type 1 (Bare Metal)**  
  Runs directly on the hardware.  
  _Examples:_ `KVM`, `Xen`, `VMware ESXi`

- **Type 2 (Hosted)**  
  Runs on a host OS like a regular application.  
  _Examples:_ `VirtualBox`, `VMware Workstation`, `Oracle VM`

---

## 🐧 Useful Linux Commands

| Command | Description |
|--------|-------------|
| `man <tool>` | Show manual for a specific tool |
| `ls -al` | List all files (including hidden) |
| `ps -aef` | Show all running processes |
| `ps -aef \| grep "exercise.py"` | Check if a script is running |
| `kill -9 <pid>` | Forcefully terminate a process |
| `cd ~` | Go to home directory |
| `cp main.py ./dir/` | Copy a file |
| `mv main.py ../main.py` | Move a file |
| `mv old.py new.py` | Rename a file |

---

## 🌐 Networking & SSH

| Command | Purpose |
|--------|--------|
| `ping <host>` | Test network connectivity |
| `ssh -p 22 user@ip` | SSH into a server |
| `scp <source> user@host:<dest>` | Secure file transfer |
| `systemctl enable|disable|restart|status ssh` | Manage SSH service |

**🪟 Windows Tools:**  
🔸 [WinSCP](https://winscp.net/) – GUI for file transfers  
🔸 [PuTTY](https://www.putty.org/) – SSH client

---

## 🐍 Python Virtual Environment

```bash
whereis python3         # Locate Python
sudo apt install python3-venv
python3 -m venv ./venv  # Create venv
source venv/bin/activate
pip install -r requirements.txt
pip freeze              # List installed packages
deactivate              # Exit venv
```

---

## ⚙️ Automation & Services

### Run a Script 24/7

- Background mode:  
  ```bash
  python3 main.py &
  ```

### 🕒 Cronjob Example (every 3 minutes)

```bash
sudo crontab -e
*/3 * * * *  /home/muhannad/Desktop/python_file/main.py
sudo grep cron /var/log/syslog  # View cron logs
```

---

### 🔄 systemd Service Setup

**Create nano bbxoapi.service
**Enter the directory `/etc/systemd/system/bbxoApi.service`:**

```ini
[Unit]
Description=FastAPI application service
After=network.target

[Service]
User=muhannad
Group=muhannad
WorkingDirectory=/home/muhannad/python_file
ExecStart=/home/muhannad/python_file/venv/bin/python main.py
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

**Enable and start the service:**

```bash
sudo chmod 644 /etc/systemd/system/bbxoApi.service
sudo systemctl daemon-reload
sudo systemctl enable bbxoApi.service
sudo systemctl start bbxoApi.service
sudo systemctl status bbxoApi.service
journalctl -u bbxoApi.service
```

---

## 🌐 NGINX Setup

```bash
sudo apt install nginx                # Install NGINX
sudo chown -R muhannad:muhannad html/ # Set permissions
```

- Default web root: `/var/www/html/`
- Visit: `http://<your-server-ip>`

---

## 🧳 Hosting a Website

1. Rent a Linux machine (e.g., AWS Lightsail)
2. Install NGINX
3. Upload your website (e.g., Bootstrap template) to `/var/www/html`
4. Setup a static IP and open ports `80` (HTTP) and `443` (HTTPS)

---

## 🔐 Security Essentials

- **SSH** for secure remote access
- **Certificates** (e.g., Let's Encrypt) – store **public keys** only
- **Encryption:**  
  🔒 AES-256 (Symmetric)  
  🔐 RSA (Asymmetric)

---

## 🐚 Bash vs Shell

- **Shell:** Interface to interact with the OS
- **Bash:** Most popular shell (also a scripting language)

---

## 🛠️ Troubleshooting

- Manage processes: `ps`, `grep`, `kill`
- Manage services: `systemctl`
- Automate tasks: `cron`, `systemd`

---

## 🧰 Recommended Tools

- [Perplexity](https://www.perplexity.ai/) – AI-powered search
- [GitHub Copilot](https://github.com/features/copilot) – AI code assistant
- [WinSCP](https://winscp.net/) – File transfers (Windows)
- [PuTTY](https://www.putty.org/) – SSH (Windows)

---

## 🏷️ Environment Variable

```bash
TEAM_NAME="BBXO"
echo $TEAM_NAME
```

---

## 📌 Notes

- Use a Python virtual environment for every project
- Keep your system packages updated
- Always use SSH keys, strong passwords, and firewall rules

---

## 📄 License

This repository is for **educational purposes only** and serves as a quick reference for DevOps learners and enthusiasts.

---

**Made with ❤️ by Team BBXO**

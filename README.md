# 🧰 WordPress NGINX Setup on AWS (Manual & Automated)

This repository contains two complete methods to deploy a WordPress website on an AWS EC2 instance using NGINX, MySQL, PHP, and SSL encryption via Let's Encrypt.

---

## 📁 Project Structure

wordpress-nginx-aws-setup/
├── automated_wordpress_lemp_setup/ # Fully automated deployment using Ansible
└── manual_wordpress_lemp_setup/ # Manual setup with step-by-step instructions


---

## 🚀 Deployment Options

### 1️⃣ Automated WordPress LEMP Setup with Ansible

This setup uses Ansible to fully automate the deployment of a secure WordPress site, including:

- ✅ LEMP Stack (Linux, NGINX, MySQL, PHP)
- ✅ UFW Firewall Configuration
- ✅ WordPress Installation & Configuration
- ✅ Let's Encrypt SSL Setup via Certbot
- ✅ Modular Roles (common, firewall, nginx, ssl, wordpress)

📂 Folder: [`automated_wordpress_lemp_setup/`](./automated_wordpress_lemp_setup/)

📖 Details: [Read the full documentation »](./automated_wordpress_lemp_setup/README.md)

---

### 2️⃣ Manual WordPress Setup

This approach documents a manual step-by-step installation of WordPress on an AWS EC2 instance using NGINX.

It covers:

- Installing NGINX, MySQL, PHP
- Configuring UFW Firewall
- Setting up WordPress manually
- SSL Configuration using Certbot

📂 Folder: [`manual_wordpress_lemp_setup/`](./manual_wordpress_lemp_setup/)

📖 Details: [Read the full documentation »](./manual_wordpress_lemp_setup/README.md)

---

## 🛠️ Requirements

For both setups:

- An AWS EC2 instance running Ubuntu 24.10
- A registered domain name (used for SSL and WordPress site access)
- SSH access to the EC2 instance
- Ansible installed (for automated setup)

---

## 👨‍💻 Author

- Alan Varghese  
📧 alan.always4u@gmail.com  
🔗 GitHub: [@alanvarghese-dev](https://github.com/alanvarghese-dev)

---

## 📝 License

This project is licensed under the MIT License.

---

## 🌐 Screenshots & Extras

Screenshots for each step of both projects are maintained in their respective folders for documentation purposes.




# Secure WordPress Deployment on AWS with Nginx and Let’s Encrypt SSL

## 🛠 Project Overview

This project demonstrates a complete setup of a secure WordPress website hosted on an AWS EC2 instance using Ubuntu 24.04. It uses Nginx as the web server, MySQL for the database, and PHP as the backend language (LEMP stack). The setup also includes securing the site using a free SSL certificate from Let's Encrypt and linking it to a free dynamic domain from No-IP.

Live URL: [https://mywordpressite.zapto.org/](https://mywordpressite.zapto.org/)

---

## 📁 Project Structure

wordpress-nginx-aws-setup/
│
├── screenshots/
│ ├── 01-ec2-instance-launch.png
│ ├── 02-ssh-access-success.png
│ ├── ...
│
├── README.md


User's Browser
     ↓ HTTPS (Port 443)
  Nginx (SSL-enabled via Let's Encrypt)
     ↓
  PHP-FPM → WordPress Files
     ↓
  MariaDB → WordPress Database


---

## 🚀 Technologies Used

- AWS EC2
- Ubuntu 24.04
- Nginx
- MySQL
- PHP
- WordPress
- Let’s Encrypt SSL
- No-IP Dynamic DNS

---

## 🔧 Step-by-Step Setup

### 1. Launching EC2
- Ubuntu 24.04 LTS instance launched on AWS EC2.
- Security Group configured to allow inbound traffic on ports 22, 80, 443.

### 2. SSH Access
- Connected to instance using SSH from Mac terminal using `.pem` key.

### 3. Installing LEMP Stack
- Installed Nginx and verified with browser IP access.
- Installed MySQL, secured it, and created:
  - `wordpress_db`
  - `wp_user` with password `StrongPassword123!`
- Installed PHP and necessary modules.

### 4. WordPress Setup
- Downloaded and extracted WordPress.
- Set correct file permissions and ownership.
- Created `wp-config.php` using `wp-config-sample.php` and updated DB credentials.
- Verified installation page loads in browser.

### 5. Domain Setup (No-IP)
- Registered a free subdomain: `mywordpressite.zapto.org`
- Pointed the domain to the public IP of EC2.
- Configured Nginx to handle the domain.

### 6. SSL Installation
- Installed Certbot and generated a Let’s Encrypt SSL certificate.
- Configured Nginx to serve HTTPS with automatic redirect from HTTP.

---

## 📸 Screenshots

Screenshots have been taken at every major step:
- EC2 instance creation
- SSH login
- Software installation
- WordPress config
- Domain pointing
- SSL setup
- Final dashboard access

_Naming Convention_: `01-step-name.png`, `02-step-name.png`...

---

## 🧰 Troubleshooting & Common Errors

| Issue | Solution |
|-------|----------|
| 502 Bad Gateway | Nginx couldn’t connect to PHP. Restart PHP service and check socket. |
| Error Establishing Database Connection | Verify MySQL is running and DB credentials are correct. |
| Nginx Fails to Start | Ensure Apache is stopped or removed. Use `sudo systemctl disable apache2`. |
| Certbot fails | Make sure your domain points to your EC2 public IP and port 80 is open. |

---

## 📌 Notes

- EC2 public IP changes if the instance is stopped unless an Elastic IP is used.
- To retain permanent access to your site, use an Elastic IP or configure No-IP client on the server.

---

## 👤 About Me

My name is Alan Varghese. I am currently pursuing a Postgraduate Diploma in Infrastructure Management, learning skills related to:

- RHCSA, MCSA, CCNA
- CompTIA A+, Network+, Security+
- AWS Solutions Architect Associate

I'm building real-world hybrid DevOps and Cybersecurity projects to transition into roles such as:

- Cloud Engineer / DevOps Engineer
- Network Security Analyst / Cybersecurity Associate
- System / Network Administrator

---

## 📇 Contact

📧 Email: thealanvarghese@gmail.com
🌐 GitHub: [github.com/yourusernamegithub.com/yourusernamegithub.com/yourusername: [github.com/alanvarghese-dev](https://github.com/alanvarghese-dev/)  
🔗 LinkedIn: https://www.linkedin.com/in/alan-varghese-dev/

---



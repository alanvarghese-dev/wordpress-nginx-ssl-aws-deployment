Automated WordPress Deployment using LEMP Stack with SSL on AWS (Ansible)

This project automates the full deployment of a WordPress site on an Ubuntu 24.10 EC2 instance using Ansible.It sets up the LEMP stack (Linux, Nginx, MySQL, PHP), configures a secure firewall, installs WordPress, obtains a Let's Encrypt SSL certificate, and configures Nginx for secure access via HTTPS.

 📁 Folder Structure

automated_wordpress_lemp_ssl_setup/
├── inventory # Ansible inventory file
├─main-playbook.yaml # Master playbook
├── roles/
│ ├── common/
│ │ └── tasks/main.yaml # Handles apt update and upgrade
│ ├── firewall/
│ │ └── tasks/main.yaml # Configures UFW firewall rules
│ ├── lemp/
│ │ └── tasks/main.yaml # Installs Nginx, MySQL, PHP
│ ├── wordpress/
│ │ └── tasks/main.yaml # Downloads, configures, and moves WordPress files
│ ├── ssl/
│ │ └── tasks/main.yaml # Requests Let's Encrypt SSL certificate
│ └── nginx/
│ ├── tasks/main.yaml # Applies custom nginx config for WordPress
│ ├── handlers/main.yaml # Contains Nginx restart/reload handlers
│ └── templates/
│ └── wordpress_nginx.conf.j2 # Nginx virtual host template
├─screenshots/

 🧰 Tools & Technologies:

- OS: Ubuntu 24.10 (on AWS EC2)
- Web Server: Nginx
- Database: MySQL
- Scripting Language: PHP
- CMS: WordPress
- Automation: Ansible
- SSL: Let’s Encrypt via Certbot

 📦 Role Descriptions

- `common`: Runs system update and upgrade via `apt`.

- `firewall`: Enables UFW and allows SSH (22), HTTP (80), and HTTPS (443).

- `lemp`: Installs Nginx, MySQL, PHP, and enables necessary PHP modules.

- `wordpress`:
  - Downloads latest WordPress package.
  - Extracts and moves it to `/var/www/html`.
  - Creates MySQL database and user with secure credentials.

- `nginx`:
  - Copies a Jinja2-based Nginx virtual host config for WordPress.
  - Includes handlers to reload or restart Nginx when config changes.

- `ssl`:
  - Uses Certbot to generate and apply an SSL certificate for your domain.
  - Ensures secure redirect from HTTP to HTTPS.

 🔥 Handlers

Located in `roles/nginx/handlers/main.yaml`:

- name: Reload Nginx
  ansible.builtin.service:
    name: nginx
    state: reloaded

- name: Restart Nginx
  ansible.builtin.service:
    name: nginx
    state: restarted

 🔐 SSL Certificate

The playbook uses Certbot to obtain an SSL certificate:

Make sure your domain (e.g., mywordpressite.zapto.org) points to your EC2 instance's public IP.

Certbot uses --non-interactive mode to automatically apply SSL and redirect all HTTP traffic to HTTPS.

 🗒️ Inventory File Example

Create an inventory file with your EC2 details:
[wordpress]
<YOUR_EC2_PUBLIC_IP> ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/your-key.pem

 🛠️ Usage Instructions

1.  Update Variables:
- Ensure your domain name is set in the SSL task (roles/ssl/tasks/main.yaml).
- Replace the email address used by Certbot.
2. Run the Playbook
- ansible-playbook -i inventory site.yaml

 ✅ Post-Deployment

Once the playbook finishes:

Visit http://yourdomain.com or https://yourdomain.com

Complete WordPress installation (username, admin, password setup via UI)

Login to WordPress Admin Dashboard

 🧪 Troubleshooting:

Problem                                         	Fix

Nginx welcome page still shows	        - Ensure default config is removed from /etc/nginx/sites-enabled/
Certbot failed with "No such auth"	- Wait for DNS to propagate and re-run the playbook
WordPress Database Error	        - Ensure database and user were created properly
SSL Not Working	                        - Verify ports 80/443 are open in AWS Security Group and UFW


💡 Tips

- Always remove default Nginx config (/etc/nginx/sites-enabled/default) to avoid conflicts.

- Set the correct DNS A record for your domain pointing to the EC2 public IP.

- You can re-run the playbook to apply changes or recover from failures.

 🔍 Screenshots

- All deployment and verification screenshots have been saved locally and can be added in a /screenshots folder in this repo.

📌 Example Group Vars (Optional)
(Not used in this project, but can be added later)

#group_vars/all.yaml
mysql_root_password: StrongPassword123!
wordpress_db: wp_database
wordpress_user: wp_user
wordpress_password: StrongPassword123!

 👤 Author

Alan Varghese
GitHub: https://github.com/alanvarghese-dev
Email: thealanvarghese@gmail.com
LinkedIn: https://linkedin.com/in/alanvarghese-dev




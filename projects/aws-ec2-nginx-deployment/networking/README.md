# 🚀 AWS EC2 + NGINX + Custom Domain Deployment

## 📌 Project Overview

This project simulates a real-world production-style deployment using AWS, demonstrating how networking, DNS, and web servers interact.

The goal was to understand how networking components work together in a real-world setup.

---

## 🧠 Architecture

Browser → Cloudflare (HTTPS) → EC2 (HTTP) → NGINX → Response

---

## ⚙️ What I Built

- Launched an EC2 instance (Amazon Linux 2023)  
- Connected via SSH using a `.pem` private key  
- Installed and configured NGINX as a web server  
- Opened port 80 using AWS Security Groups  
- Linked a custom domain using Cloudflare DNS  
- Enabled HTTPS using Cloudflare SSL (Flexible mode)  

---

## 🧪 Commands Used

```bash
ssh -i nginx-key.pem ec2-user@<ip>
sudo dnf install -y nginx
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx

```

🚧 Challenges & Solutions

🔐 SSH Permission Issue
```
- Private key permissions too open
- Fixed using:
chmod 400 nginx-key.pem
```

🌐 Cloudflare 522 Error
- Issue: Domain not loading when proxy enabled
- Cause: Cloudflare could not reach EC2
- Fix:
- Verified Security Group allowed port 80
- Ensured correct public IP
- Set SSL mode to Flexible

🔒 HTTP vs HTTPS
- EC2 serves HTTP by default
- Cloudflare handles HTTPS encryption


## 📸 Screenshots

### EC2 Instance

![EC2](./screenshots/ec2.png)

### Security Group
![Security Group](./screenshots/security-group.png)

### Cloudflare DNS
![DNS](./screenshots/dns.png)

### Live Website
![Website](./screenshots/website.png)

### NGINX Status
![NGINX](./screenshots/nginx.png)

🎯 Key Takeaways
- Learned how DNS resolves domains to IP addresses
- Understood how HTTP traffic reaches a server
- Gained Linux server management experience
- Debugged real-world networking issues
- Learned how Cloudflare acts as a reverse proxy

## 🔗 Live Site

https://mud-as-sir.uk

## 🌐 Live Infrastructure

- Root Domain: https://mud-as-sir.uk
- Subdomain: https://nginx.mud-as-sir.uk

## 🧠 What This Project Demonstrates

- DNS resolution (domain → IP)
- Reverse proxy behaviour (Cloudflare)
- HTTP vs HTTPS handling
- Linux server management (NGINX)
- Infrastructure stability using Elastic IP
- Debugging real-world issues (SSH, permissions, timeouts)

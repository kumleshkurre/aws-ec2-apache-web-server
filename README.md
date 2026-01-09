# 🚀 AWS EC2 Web Server Setup Guide

## 📌 Objective
 Ye guide aapko step-by-step AWS EC2 instance launch karke Apache Web Server setup aur run karna sikhaata hai 🌐

---

## 🔹 Prerequisites 📋

- ☁️ AWS Account
- 🐧 Basic knowledge of Linux commands
- 🔐 SSH client (Linux/macOS) ya PuTTY (Windows)
- 🌍 Web browser
  
---

## 1️⃣ Launching EC2 Instance 🖥️

- AWS Console me login karein 🔑
- Search EC2 → Open EC2 Dashboard
- Click Launch Instance 🚀
- Configure Instance:
- Name and Tags: My Web Server
- Operating System: Select Amazon Linux 2 / Ubuntu (Linux recommended) 🐧
- Key Pair 🔐:
- Select Create new key pair
- Name: mywebserver-key
- Type: RSA
- Click Create key pair → mywebserver-key.pem file automatically download ho jayega
  
---
## ⚠️ Important: Key file safe jagah pe rakhein

- Network Settings 🌐:
- Allow SSH (Port 22) from your IP
- Allow HTTP (Port 80) from anywhere
- Storage 💾: Default ya apne requirement ke hisaab se configure karein
- Advanced Details → User Data 🧾: Neeche diya gaya script paste karein

```
#!/bin/bash
sudo yum update -y

# Install Apache web server
sudo yum install -y httpd

# Start Apache service
sudo systemctl start httpd

# Enable Apache on boot
sudo systemctl enable httpd

# Create a simple HTML page
echo "<html>
<h1>Welcome to Apache Web Server on Amazon Linux!</h1>
</html>" | sudo tee /var/www/html/index.html
```
## 2️⃣ EC2 Instance Verification ✅

- AWS Management Console me EC2 Dashboard open karein
- Instances section me jaakar apna instance select karein
- Aapka instance “My Web Server” naam se dikhai dega
- Instance ID par click karein aur details open karein
- Public IPv4 Address copy karein 📎
- Kisi bhi web browser me Public IP paste karein 🌍
- ➡️ Agar Apache sahi se run ho raha hai, to aapka HTML Web Page browser me load ho jayega 🎉

## 3️⃣ Security Group Configuration 🔐
- EC2 Dashboard → Instances me instance select karein
- Security tab open karein
- Associated Security Group link par click karein
- Edit Inbound Rules par click karein

## ⚠️ Important Points:

- Agar HTTP (Port 80) rule delete kar diya gaya hai, to web server browser se access nahi hoga ❌
- Server access wapas lane ke liye:
- HTTP (Port 80) ko Allow karein
- Source: 0.0.0.0/0 (Public Access)
- Changes Save karein 💾

## ⚡ Best Practices / Tips ⭐

- 🔐 Key Pair hamesha safe jagah par store karein:
  Key pair ke bina SSH login possible nahi hota

- 🌐 Web server ko publically access karne ke liye:
  HTTP (80) ya HTTPS (443) security group me open hona zaroori hai

- 🧾 User Data Script sirf first boot ke time execute hoti hai
  Instance restart karne se script dobara run nahi hoti
 Script change karne ke liye new instance launch karna hota hai


---
## 👨‍💻 Author

**Kumlesh Kurre**  
 IT Support & Network Engineer  

⭐ If you find this project helpful, please give it a star on GitHub.


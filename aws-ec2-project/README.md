# Hosting a Website on AWS EC2 (Linux)

## 1. Launch an EC2 Instance
- Go to **AWS Console → EC2 → Launch Instance**
- Choose **Amazon Linux 2 AMI (Free Tier eligible)**
- Instance type: **t2.micro**
- Configure **Security Group**:
  - SSH (22) → Your IP
  - HTTP (80) → Anywhere (0.0.0.0/0, ::/0)
- Download and save the **key pair (.pem file)**
- Launch the instance

---

## 2. Connect to Your EC2 Instance
```bash
ssh -i mykey.pem ec2-user@<EC2-PUBLIC-IP>
```

---

## 3. Install Apache Web Server
```bash
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd
```

Check service status:
```bash
systemctl status httpd
```

---

## 4. Deploy Your Website
Navigate to web root:
```bash
cd /var/www/html
sudo nano index.html
```

Add sample HTML:
```html
<!DOCTYPE html>
<html>
<head>
  <title>My EC2 Website</title>
</head>
<body>
  <h1>Hello from AWS EC2 Linux!</h1>
  <p>This is a static website hosted on Amazon EC2.</p>
</body>
</html>
```

Save and exit (`CTRL+O`, `CTRL+X`).

---

## 5. Access Website
- Open: `http://<EC2-PUBLIC-IP>`
- You should see your website 🎉


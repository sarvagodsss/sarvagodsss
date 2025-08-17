# Hosting a Website on AWS EC2 (Ubuntu)

## 1. Launch an EC2 Instance
- Go to **AWS Console → EC2 → Launch Instance**
- Choose **Ubuntu Server 22.04 LTS (Free Tier eligible)**
- Instance type: **t2.micro**
- Configure **Security Group**:
  - SSH (22) → Your IP
  - HTTP (80) → Anywhere (0.0.0.0/0, ::/0)
  - HTTPS (443) → Anywhere (optional)
- Download and save the **key pair (.pem file)**
- Launch the instance

---

## 2. Connect to Your EC2 Instance
```bash
ssh -i mykey.pem ubuntu@<EC2-PUBLIC-IP>
```

---

## 3. Install Apache or Nginx

### Apache
```bash
sudo apt update -y
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
```

Check status:
```bash
systemctl status apache2
```

### Nginx
```bash
sudo apt update -y
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## 4. Deploy Your Website
Default web directory: `/var/www/html`

```bash
cd /var/www/html
sudo nano index.html
```

Sample HTML:
```html
<!DOCTYPE html>
<html>
<head>
  <title>My EC2 Website - Ubuntu</title>
</head>
<body>
  <h1>Hello from AWS EC2 Ubuntu!</h1>
  <p>This is a static website hosted on Ubuntu EC2.</p>
</body>
</html>
```

Save and exit (`CTRL+O`, `CTRL+X`).

---

## 5. Access Website
- Open: `http://<EC2-PUBLIC-IP>`
- You should see your website 🎉

# menu-based-health-check-system

**Overview:**
This is a menu-based Bash script that performs essential system health checks and sends a comprehensive report via email every four hours. It helps in monitoring disk usage, running services, memory usage, and CPU performance.

**Features:**
Check Disk Usage: Displays available and used disk space.
Monitor Running Services: Lists currently active services.
Assess Memory Usage: Shows memory consumption.
Evaluate CPU Usage: Monitors CPU performance.
Send Comprehensive Report via Email: Gathers system data and sends a detailed report.
Automated Email Report Every Four Hours (via cron).

**Prerequisites**
**Ensure your system meets the following requirements:**
Linux (Ubuntu, CentOS, or any Unix-based system)
Bash Shell
mailx (for email functionality)
sudo access

**Install Necessary Packages:**

To install mailx, run:
```bash
sudo apt install mailutils  # Ubuntu/Debian
```
![image](https://github.com/user-attachments/assets/be1db0fc-d991-4cd9-9df1-ad1cb99d76c5)


**Clone this repository:**
```bash
https://github.com/Prasadrasal2002/menu-based-health-check-system.git
```
![image](https://github.com/user-attachments/assets/8a998ae8-1b66-42ec-bd4b-55188b98d2fe)

Set up your email for receiving reports (modify EMAIL in the script):
```bash
EMAIL="your-email@example.com"
```

Make the script executable:
```bash
chmod +x health-check-system.sh
./health-check-system.sh
```
A menu will appear:
![image](https://github.com/user-attachments/assets/6ac0ccb3-b77a-46c0-a3cc-9b1d01a7d154)

![image](https://github.com/user-attachments/assets/d092e90d-cf24-4887-99b0-6d1169200779)

![image](https://github.com/user-attachments/assets/ed555b0d-a419-4688-b7e5-7618ef6a9324)

![image](https://github.com/user-attachments/assets/b0d8f23e-ddb3-4839-97e7-05d56e6ae3a9)


**Configure Postfix for Gmail SMTP Relay:**
Ensure you have Postfix and cURL installed:
```bash
sudo apt update
sudo apt install postfix mailutils libsasl2-modules
```
![image](https://github.com/user-attachments/assets/44726dde-e57c-48dd-b116-3528fd5854c6)

Edit the Postfix configuration file:
```bash
sudo nano /etc/postfix/main.cf
```
![image](https://github.com/user-attachments/assets/7fcb07db-4f4b-42b7-9c50-ee7b824ac1c6)


Add or update these lines in (sudo nano /etc/postfix/main.cf):
```bash
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = encrypt
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
```
![image](https://github.com/user-attachments/assets/6911f987-e0f4-49c4-8b4a-cb7949c75dfa)

**Set Up Gmail Authentication:**
Create the file /etc/postfix/sasl_passwd:
```bash
sudo nano /etc/postfix/sasl_passwd
```

Add this line in /etc/postfix/sasl_passwd (replace with your Gmail email and App Password):
```bash
[smtp.gmail.com]:587 your-email@gmail.com:your-app-password
```

**Secure the Credentials:**
```bash
sudo chmod 600 /etc/postfix/sasl_passwd
sudo postmap /etc/postfix/sasl_passwd
```

**Email for receiving reports:**

![image](https://github.com/user-attachments/assets/d3a21a45-4297-4bf5-9ad4-49dcad3d4455)









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

Ensure you have Postfix and cURL installed:
```bash
sudo apt update
sudo apt install postfix mailutils libsasl2-modules
```
**Clone this repository:**
```bash
sudo nano /etc/postfix/main.cf
```
![image](https://github.com/user-attachments/assets/8a998ae8-1b66-42ec-bd4b-55188b98d2fe)

Make the script executable:
```bash
sudo nano /etc/postfix/main.cf
```

Set up your email for receiving reports (modify EMAIL in the script):
```bash
EMAIL="your-email@example.com"
```


**Configure Postfix for Gmail SMTP Relay:**
Edit the Postfix configuration file:
```bash
sudo nano /etc/postfix/main.cf
```

Add or update these lines:
sudo nano /etc/postfix/main.cf 
```bash
sudo nano /etc/postfix/main.cf

relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = encrypt
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
```

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






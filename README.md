# menu-based-health-check-system
### 3️⃣ Plan Deployment
```bash
terraform plan
```
Overview
This is a menu-based Bash script that performs essential system health checks and sends a comprehensive report via email every four hours. It helps in monitoring disk usage, running services, memory usage, and CPU performance.

Features
Check Disk Usage: Displays available and used disk space.
Monitor Running Services: Lists currently active services.
Assess Memory Usage: Shows memory consumption.
Evaluate CPU Usage: Monitors CPU performance.
Send Comprehensive Report via Email: Gathers system data and sends a detailed report.
Automated Email Report Every Four Hours (via cron).

Prerequisites
Ensure your system meets the following requirements:

Linux (Ubuntu, CentOS, or any Unix-based system)
Bash Shell
mailx (for email functionality)
sudo access

# 🖥️ Netdata Monitoring on AWS EC2

This project demonstrates how to install and configure Netdata on an AWS EC2 instance to monitor system performance in real-time.

## ✅ Features
- Real-time CPU, RAM, disk, network, etc.
- Accessible via public IP on port `19999`
- Lightweight and auto-starts on boot

## 🛠️ Tech Stack
- AWS EC2 (Amazon Linux 2)
- Netdata
- Linux (systemd, netstat, iptables)

## 🔧 Setup Instructions

1. Launch a `t2.micro` EC2 instance

2. SSH into it:
   ```bash
   ssh -i your-key.pem ec2-user@<public-ip>

3.  Install Netdata:
    bash <(curl -Ss https://my-netdata.io/kickstart.sh) --no-updates

4. Open Port 19999

   *  Go to your EC2 Security Group settings
 
   *  Add an Inbound Rule:

   *  Type: Custom TCP

   *  Port Range: 19999

   *  Source: Anywhere (or restrict to your IP)

5. Access Netdata in your browser:

   * http://<your-ec2-public-ip>:19999

 🔐 Security Best Practices
Don't leave port 19999 open to the whole internet forever. After testing, choose one of the following:

✅ Option 1: Restrict access in your Security Group to your own IP address only.

✅ Option 2: Close port 19999 and use an NGINX reverse proxy with basic authentication for secure access.

6. Stopping Netdata to Avoid Charges
   
   If you're done testing and want to stop Netdata:

   sudo systemctl stop netdata
   And stop the EC2 instance from AWS Console.

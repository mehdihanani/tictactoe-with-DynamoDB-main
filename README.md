# **Tic-Tac-Toe Game with AWS**  

A cloud-based Tic-Tac-Toe game built with **AWS EC2**, **DynamoDB**, and **Python/Flask**.  

---

## **📦 Architecture Overview**  
### **Core Components**  
1. **🖥️ AWS EC2 Instance**  
   - Hosts the game (Amazon Linux 2).  
2. **🗃️ AWS DynamoDB**  
   - NoSQL database storing game state (`Games` table).  
3. **🐍 Python Application**  
   - **Flask**: Web framework.  
   - **Boto**: AWS SDK for DynamoDB.  
4. **🔐 IAM Role**  
   - Grants EC2 secure access to DynamoDB.  

---

## **🎮 Key Features**  
- **🚀 Create Games**: Initialize and track games in DynamoDB.  
- **🤝 Invite Players**: Accept/reject invites via DynamoDB updates.  
- **⏭️ Turn-Based Logic**: Players alternate; moves are validated.  
- **🏆 Win Detection**: Checks for wins/ties after each move.  

---

## **⚙️ Installation & Deployment**  

### **1. Prerequisites**  
- AWS account with **EC2**, **DynamoDB**, and **IAM** access.  
- EC2 instance (Amazon Linux 2) with **Metadata V1/V2** enabled.  

### **2. Setup**  
#### **Install Dependencies**  
Installs essential development tools and libraries needed for compiling and building software.

```bash
sudo yum groupinstall -y "Development Tools"
```

Installs development headers and libraries for OpenSSL, bzip2, and libffi, required for Python.

```bash
sudo yum install -y openssl-devel bzip2-devel libffi-devel git
```

Install Python 2.7
Downloads Python 2.7.18, extracts it, configures the build with optimizations enabled, and installs it without replacing the system-provided Python.

```bash
cd /usr/src
sudo wget https://www.python.org/ftp/python/2.7.18/Python-2.7.18.tgz
sudo tar xzf Python-2.7.18.tgz
cd Python-2.7.18
sudo ./configure --enable-optimizations
sudo make altinstall
```

Verifies the installed Python version.

```bash
python2.7 -V  # Verify
```

Install Pip + Packages

```bash
wget https://bootstrap.pypa.io/pip/2.7/get-pip.py
python get-pip.py
```

Installs Flask, Boto (for AWS SDK), and configparser Python packages using pip.

```bash
pip install Flask boto configparser
```
### Install Git

Installs Git, a version control system.

```bash
yum install git -y
```

Clone the TicTacToe Project Repository

```bash
cd /home/ec2-user/
git clone https://github.com/mehdihanani/tictactoe-with-DynamoDB-main.git
```
[Settings]
TableName = Games
Region = YOUR_REGION  # e.g., ap-south-2

[dynamodb]
region = YOUR_REGION
endpoint = dynamodb.YOUR_REGION.amazonaws.com
```bash
python application.py --config config.ini --mode service \
  --endpoint dynamodb.YOUR_REGION.amazonaws.com --serverPort 5000
```
Open port 5000 in the EC2 security group.

my région : ca-central-1
Access: http://<EC2_PUBLIC_IP>:5000.

📝 Prepared by EMH

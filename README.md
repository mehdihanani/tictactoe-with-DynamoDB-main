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
```bash
sudo yum groupinstall -y "Development Tools"
sudo yum install -y openssl-devel bzip2-devel libffi-devel git
```
Install Python 2.7
```bash
cd /usr/src
sudo wget https://www.python.org/ftp/python/2.7.18/Python-2.7.18.tgz
sudo tar xzf Python-2.7.18.tgz
cd Python-2.7.18
sudo ./configure --enable-optimizations
sudo make altinstall
```
```bash
python2.7 -V  # Verify
```
Install Pip + Packages
```bash
wget https://bootstrap.pypa.io/pip/2.7/get-pip.py
python get-pip.py
pip install Flask boto configparser
```
Clone Repo
```bash
cd /home/ec2-user/
git clone https://github.com/avizway1/tictactoe-with-DynamoDB.git
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

Access: http://<EC2_PUBLIC_IP>:5000.

📝 Prepared by EMH

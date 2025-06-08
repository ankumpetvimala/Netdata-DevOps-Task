Task 7: Netdata Monitoring on Ubuntu EC2
Objective
Deployed Netdata, a lightweight, open-source monitoring tool, on an AWS EC2 instance running Ubuntu 22.04 to monitor system and application performance metrics. Documented the process for submission as part of a DevOps internship task.

Tools Used
AWS EC2: Hosted the Ubuntu 22.04 instance
Docker: Ran the Netdata container
Netdata: Monitored CPU, memory, disk, and Docker container metrics
GitHub: Stored deliverables and documentation
Implementation Steps
1. Launched an EC2 Instance
Created Ubuntu 22.04 LTS instance (t2.micro) in AWS
Security group configured to allow:
Port 22 (SSH)
Port 80 (HTTP)
Port 19999 (Netdata)
Connected via SSH:
ssh -i task7-key.pem ubuntu@<public-ip>
2. Installed Docker
Update system
sudo apt update && sudo apt upgrade -y
Install Docker
sudo apt install -y docker.io
Start and enable Docker
sudo systemctl start docker && sudo systemctl enable docker
Add user to Docker group
sudo usermod -aG docker ubuntu
3. Deployed Netdata
Run Netdata container
docker run -d --name=netdata -p 19999:19999 netdata/netdata
Verify container status
docker ps
4. Accessed Netdata Dashboard
Accessed at: http://:19999
Monitored metrics:
CPU utilization
Memory usage
Disk I/O
Docker container performance

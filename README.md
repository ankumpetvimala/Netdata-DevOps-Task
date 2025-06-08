# Task 7: Netdata Monitoring on Ubuntu EC2

## Objective

Deployed Netdata, a lightweight, open-source monitoring tool, on an AWS EC2 instance running Ubuntu 22.04 to monitor system and application performance metrics. Documented the process for submission as part of a DevOps internship task.

##  Tools Used

- **AWS EC2**: Ubuntu 22.04 LTS (t2.micro)
- **Docker**: Container runtime for deploying Netdata
- **Netdata**: Real-time performance monitoring tool
- **GitHub**: Repository for logs and documentation

---

##  Implementation Steps

### 1. 🚀 Launch EC2 Instance

- Created an **Ubuntu 22.04 LTS** instance.
  
- Security group configuration:
  
  - Port **22** – SSH
  - Port **80** – HTTP
  - Port **19999** – Netdata Dashboard

- Connected via SSH
  
  ssh -i task7-key.pem ubuntu@<your-ec2-public-ip>

## 2. Install Docker

- Update system

  sudo apt update && sudo apt upgrade -y

- Install Docker

  sudo apt install -y docker.io

- Start and enable Docker:

  sudo systemctl start docker

  sudo systemctl enable docker

- Add your user to Docker group:

  sudo usermod -aG docker ubuntu


## 3. Deploy Netdata with Docker

- Run Netdata container:

  docker run -d --name=netdata -p 19999:19999 netdata/netdata

- Check container status:

  docker ps

## 4. Access Netdata Dashboard

   - Accessed at: http://:19999
   - Monitored metrics:
   - CPU utilization
   - Memory usage
   - Disk I/O
   - Docker container performance


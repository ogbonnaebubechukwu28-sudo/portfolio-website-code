cat > README.md << 'EOF'
# Portfolio Website CI Pipeline

## Project Overview
A portfolio website containerized with Docker and deployed automatically using Jenkins CI/CD pipeline on AWS EC2.

## Pipeline Stages
1. **Checkout** - Jenkins pulls latest code from GitHub via webhook
2. **Build** - Builds Docker image from Dockerfile
3. **Install Dependencies** - Installed inside container during build
4. **Run Application** - Runs container on port 8081

## Tools Used
- Jenkins
- GitHub & GitHub Webhook
- Docker & Nginx
- AWS EC2

## Challenges Encountered
1. **Port conflict** - Port 80 was busy, fixed by using port 8081
2. **Stuck container** - Removed with `docker rm -f portfolio`
3. **Webhook not triggering** - Required an actual push to activate

## How Challenges Were Resolved
Each issue was debugged through Jenkins console output and fixed by editing the Jenkinsfile and redeploying.
EOF

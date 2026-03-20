FROM jenkins/jenkins:lts

# Switch to root to install system packages
USER root

# Install Python, pip, and virtual environment tools
RUN apt-get update && \
    apt-get install -y python3 python3-venv python3-pip && \
    apt-get clean

# Drop back to the regular jenkins user for security
USER jenkins
# 🚀 Python CI/CD Pipeline with Jenkins & Docker

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![Python Version](https://img.shields.io/badge/python-3.13-blue)
![Jenkins](https://img.shields.io/badge/automation-jenkins-orange)

This repository contains a professional **Continuous Integration and Continuous Deployment (CI/CD)** workflow. It demonstrates how to automate the full lifecycle of a Python application—from code linting to verified deployment packages.

## 🏗️ Architecture & Workflow
The project uses a **Custom Jenkins Docker Image** built on top of the official Jenkins LTS, pre-configured with Python 3.13.

### Pipeline Stages:
1.  **Checkout SCM**: Securely pulls code from GitHub using **SSH Authentication**.
2.  **Setup Environment**: Creates a `venv` and installs dependencies.
3.  **Lint Code**: Runs `flake8` to enforce **PEP 8** style standards.
4.  **Run Tests**: Executes unit tests via `pytest` and exports `JUnit XML` reports.
5.  **Deploy**: Packages the `app.py` into a `dist/` directory.

## 🛠️ Installation
1. **Build Jenkins**: `docker build -t jenkins-python-custom ./jenkins_setup`
2. **Run Server**: `docker run -d -p 8080:8080 -v jenkins_home:/var/jenkins_home jenkins-python-custom`

---
**Maintained by:** [Narayan](https://github.com/Narayan24052006)
# 🚀 Python CI/CD Pipeline with Jenkins & Docker

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![Python Version](https://img.shields.io/badge/python-3.13-blue)
![Jenkins](https://img.shields.io/badge/automation-jenkins-orange)
![Platform](https://img.shields.io/badge/platform-M1_Mac-lightgrey)

This repository demonstrates a fully automated **Continuous Integration and Continuous Deployment (CI/CD)** pipeline. It showcases how to take a standard Python application and automate its entire lifecycle—from code formatting and logic testing to generating a deployment-ready package—using Jenkins inside a custom Docker container.

---

## 🧠 What is Happening? (The Workflow)

Whenever new code is pushed to the `main` branch, Jenkins triggers a predefined sequence of events (defined in the `Jenkinsfile`). If any stage fails, the pipeline immediately stops, preventing broken code from moving forward.

### The 5-Stage Pipeline:
1. **📥 Checkout SCM:** Jenkins securely authenticates with GitHub using SSH keys and pulls the latest version of the repository.
2. **⚙️ Setup Environment:** Jenkins navigates into the `files/` directory, creates an isolated Python Virtual Environment (`venv`), and installs the required dependencies (`pytest` and `flake8`) from `requirements.txt`.
3. **🧹 Lint Code:** The pipeline runs `flake8` against the source code to ensure strict adherence to **PEP 8** formatting standards (checking for proper blank lines, trailing spaces, and end-of-file newlines).
4. **🧪 Run Tests:** Jenkins executes the unit tests using `pytest`. It verifies the core mathematical logic in `app.py` and exports the results to a `test-results.xml` file for Jenkins to track visually.
5. **📦 Deploy:** Upon successful linting and testing, the pipeline simulates a production deployment by packaging the verified `app.py` into a newly created `dist/` directory.

---

## 📂 Project Structure

```text
python-cidi/
├── files/
│   ├── app.py           # The main Python application logic
│   ├── test.py          # The PyTest suite verifying app.py
│   ├── requirements.txt # Python dependency manifest
│   └── Jenkinsfile      # The Pipeline-as-Code definition
├── jenkins_setup/
│   └── Dockerfile       # Instructions to build the custom Jenkins image
└── README.md            # Project documentation

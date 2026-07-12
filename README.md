
Set up a Jenkins pipeline that automates the testing and deployment of a simple Python web application.

Requirements:

1. Setup:

   - Install Jenkins on a virtual machine or use a cloud-based Jenkins service.
   Aparna Peri Answer(APA):  Yes, installed Jenkins on a virtual machine AWS ec2 instance. Attached the screenshots for the same.

   - Configure Jenkins with Python and any necessary libraries.
   (APA): Yes, configured jenkins with python and necessary libraries.

2. Source Code:

  - Fork the provided Python web application repository on GitHub (https://github.com/mohanDevOps-arch/flask_Practice.git)
   (APA):  Yes done, attached is the screenshot

  - Clone the forked repository into your Jenkins server.
  (APA):  Yes done, attached is the screenshot

3. Jenkins Pipeline:

   - Create a Jenkinsfile in the root of your Python application repository.
  (APA):  Yes done, attached is the screenshot

   - Define a pipeline with the following stages:
  (APA):  Yes done, attached is the screenshot

    - Build: Install dependencies using pip.

    - Test: Run unit tests using a testing framework like pytest.

    - Deploy: If tests pass, deploy the application to a staging environment.

4. Triggers:

   - Configure the pipeline to trigger a new build whenever changes are pushed to the main branch of the repository.
   (APA):  Yes done, attached is the screenshot

5. Notifications:

   - Set up a notification system to alert via email when the build process fails or succeeds.
   (APA):  Yes done, attached is the screenshot

6. Documentation:

   - Document the pipeline process and any prerequisites needed for the setup in a README.md file in the repository.

7. Submission:

   - Provide the URL to the GitHub repository with the Jenkinsfile and updated README.md.

   - Include screenshots of the Jenkins pipeline showing the build, test, and deployment stages.

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <repo-folder>
```

### 2. Create and activate a virtual environment

```bash
python -m venv venv
# Activate venv
# Windows:
venv\Scripts\activate
# Linux / Mac:
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

**`requirements.txt` example:**

```
Flask
Flask-PyMongo
python-dotenv
bson
```

### 4. Configure environment variables

Create a `.env` file in the project root:

```
MONGO_URI=<your-mongodb-connection-string>
SECRET_KEY=<your-secret-key>
```

### 5. Run the application

```bash
python app.py



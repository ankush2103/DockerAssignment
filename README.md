# Docker Application Deployment

## Step 1: Deploy a Sample Web Application

### Application Description
This is a simple Python Flask application that returns "Hello, Docker!" when accessed.

### Files
- `app.py`: The main application file.
- `Dockerfile`: The Dockerfile used to create the Docker image.

### Deployment Steps
1. **Set Up the Application**:
   - Create a file named `app.py` with the following content:
     ```python
     from flask import Flask

     app = Flask(__name__)

     @app.route('/')
     def hello_world():
         return 'Hello, Docker!'

     if __name__ == '__main__':
         app.run(host='0.0.0.0', port=5001)
     ```

2. **Create a Dockerfile**:
   - Create a file named `Dockerfile` with the following content:
     ```Dockerfile
     # Use an official Python runtime as a parent image
     FROM python:3.8-slim

     # Set the working directory in the container
     WORKDIR /app

     # Copy the current directory contents into the container at /app
     COPY . /app

     # Install Flask
     RUN pip install flask

     # Make port 5001 available to the world outside this container
     EXPOSE 5001

     # Run app.py when the container launches
     CMD ["python", "app.py"]
     ```

3. **Build the Docker Image**:
   - Open a terminal, navigate to your project directory, and build the Docker image:
     ```sh
     docker build -t flask-app .
     ```

4. **Run the Docker Container**:
   - Run the container using the image you just built:
     ```sh
     docker run -p 5001:5001 flask-app
     ```

   - You should be able to access the web application by navigating to `http://localhost:5001` in your web browser.

### Author
- **Name: Ankush Jha
Roll Number: G23AI2007
Contact: g23ai2007@iitj.ac.in

### Submission
- **GitHub Repository Link**: [Provide the link to your GitHub repository here]

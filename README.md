🐳 Task 1: Containerize a Web Application (Real Dev Scenario)

📖 Overview

This project demonstrates how to containerize a simple **Node.js (Express)** web application using **Docker**. The objective is to package the application along with all its dependencies into a Docker image, ensuring it runs consistently across development, testing, and production environments.

In this real-world DevOps scenario, the application is containerized by creating a Dockerfile, building a Docker image, and running the application inside a Docker container. The project also covers exposing application ports, accessing the application through a web browser, and optionally publishing the Docker image to Docker Hub.


🎯 Objective

Deploy a simple web application using Docker while learning the complete containerization workflow.



🧩 Scenario

Your development team has built a simple Node.js (Express) application. As a DevOps Engineer, your responsibility is to containerize the application so that it can run reliably and consistently across different environments without dependency or configuration issues.



📌 Requirements
* 🚀 Create a simple Node.js (Express) web application
* 📝 Create a Dockerfile
* 🏗️ Build a Docker image
* ▶️ Run the Docker container
* 🌐 Expose the application on port **3000**
* 💻 Verify the application in a web browser
  


🔧 Implementation Steps
1. 📁 Create the Node.js application
2. 🐳 Create the Dockerfile
3. 📦 Choose the appropriate base image (`node`)
4. 📂 Copy the application files
5. 📥 Install application dependencies
6. 🌐 Expose port **3000**
7. ▶️ Build the Docker image
8. 🚀 Run the Docker container
9. ✅ Verify the application in the browser
    


✅ Expected Output

After successfully running the container, the application should be accessible at:
http://localhost:3000**



💡 Bonus

☁️ Push the Docker image to Docker Hub
  


🐳 Docker Architecture Overview

![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Docker%20Architecture%20Overview.PNG?raw=true)



📌 Overall Workflow

Install Docker
       │
       ▼
Create Project Folder
       │
       ▼
Develop Simple Web App
       │
       ▼
Run App Locally
       │
       ▼
Create Dockerfile
       │
       ▼
Build Docker Image
       │
       ▼
Run Docker Container
       │
       ▼
Open Browser (localhost)
       │
       ▼
Verify Application
       │
       ▼
(Optional)
Push Image to Docker Hub




🛠️ Install Prerequisites

Before starting this project, install the following software:

🐳 Docker Desktop – Install Docker Desktop and ensure the Docker Engine is running.

🐋 Docker – Verify the Docker installation using docker --version.

🟢 Node.js – Install Node.js (includes npm) and verify the installation using node -v and npm -v.

💻 Visual Studio Code (VS Code) – Install VS Code to write and manage the project files.

![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Docker%20and%20Nodejs.PNG?raw=true)

![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Docker%20Engine%20Running.PNG?raw=true)



Create the project folder

![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Project%20Directory.PNG?raw=true)
![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Enter%20directory.PNG?raw=true)


Initialize the Node.js Project

![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Initialize%20the%20NodeJs%20project.PNG?raw=true)


Install Express

![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Install%20Express.PNG?raw=true)


Create the Application, Add the following code and save the file 

const express = require('express');

const app = express();

const PORT = 3000;

app.get('/', (req, res) => {
    res.send('Hello Docker!');
});

app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`);
});


![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Create%20the%20application.PNG?raw=true)

![image alt](https://github.com/ajaykumargk2k9/Task-01/raw/refs/heads/main/Add%20the%20code%20in%20app.js)



Update package.json

Open package.json, Replace and save the file 

Find:

"scripts": {

  "test": "..."
}


Replace it with:

"scripts": {

  "start": "node app.js"
}

![image alt](https://github.com/ajaykumargk2k9/Task-01/raw/refs/heads/main/Update%20package.json)




Start the Application


Run, npm start

Expected Output

> docker-node-app@1.0.0 start
> node app.js

Server running on port 3000


![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Start%20the%20nodejs%20application.PNG?raw=true)



Test in the Browser

Open, http://localhost:3000

Expected Result: Hello Docker!

![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Test%20in%20the%20browser.PNG?raw=true)




Create a Dockerfile

A Dockerfile is a text file that contains a set of instructions for building a Docker image. It defines the application's environment installs dependencies and specifies how the application should run inside a Docker container.

📌 Steps

1. Open Visual Studio Code (VS Code).
2. In the Explorer panel, right click your project folder.
3. Select New File.
4. Name the file exactly: Dockerfile


Important:Do not add a `.txt` extension. The filename must be exactly Dockerfile.


Copy and paste the following content into the `Dockerfile` and save the file.

dockerfile

FROM node:22

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]

![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/Dockerfile.PNG?raw=true)



Create a .dockerignore File named ".dockerignore"

Add the following 

node_modules
npm-debug.log

When Docker builds the image it copies our project.
We don't want to copy node_modules from our computer because the image will install dependencies itself with npm install.
This keeps our image cleaner and avoids platform specific issues.

![image alt](https://github.com/ajaykumargk2k9/Task-01/blob/main/dockerignore.PNG?raw=true)






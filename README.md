# nodejs-application

Let’s walk through all the steps to deploy a web application on AWS—from choosing the app to making it live. I’ll give you a complete beginner-friendly guide, including an example web app and all the AWS services involved.

✅ Step-by-Step: Deploy a Web App on AWS (Beginner-Friendly)
We’ll deploy a simple Node.js + Express web app on EC2 using Amazon Linux. You can replace it with any stack later (like Python, PHP, React, etc.).

🔧 Tools & Technologies
Web App: Node.js + Express "Hello World" app
🌐 Step 1: Launch the instance> Create an AWS EC2 Instance
Login to AWS Console → EC2 Dashboard → Launch Instance

Choose Amazon Machine Image (AMI): Amazon Linux 2

Instance Type: t2.micro (Free Tier)

Key Pair: Create one or use existing (you'll need the .pem file)

Security Group:

Add SSH (port 22) from your IP

Add HTTP (port 80) from anywhere

Add Custom TCP (port 3000) from anywhere (for testing)

Step 2: Connect to the EC2 Instance
Use terminal or Git Bash:

chmod 600 devops.pem
ssh -i your-key.pem ec2-user@<your-ec2-public-ip>
ssh -i devops.pem ec2-user@13.60.249.244


Steps 3
Create a Folder on vscode  and paste this called it node-web
Create a file called it node.js
Paste this file 

const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, AWS from Node.js!');
});

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});


Save the code

Open Terminal on vscode
Run the code below

Create a repository on GitHub 
Name it (your choice)
git add application.js
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/Ochubaanthony/application.git
git push -u origin main

Refresh the Github to see the code has been added on the GitHub



🔑 
🛠️ Step 4: Set Up the Web Server
Install Node.js and Git:
sudo yum update -y
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install node
node -v
npm -v
sudo yum install git -y
git --version
git clone https://github.com/Ochubaanthony/node.git
cd node.js

Let’s create a package.json and install Express manually.
Step 1: Initialize package.json
npm init -y

Step 2: Install Express
npm install express

Step 3: Run your app
node app.js


http://<your-ec2-public-ip>:3000
🧼 Step 5: Run App in Background
Use pm2 to keep the app running:


AFTER CREATE TGE EC2 INSTANCE CONTIUNE FROM THE BELOW

  1  sudo yum update -y
    2  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
    3  source ~/.bashrc
    4  clear
    5  nvm install node
    6  sudo yum install git -y
    7  git clone https://github.com/Ochubaanthony/application.git
    8  clear
    9  ls
   10  cd application/
   11  npm init -y
   12  npm install express
   13  node application.js



OR
CREATE A FILE IN SIDE
nano index.js

Paste
const express = require('express');
const app = express();
const PORT = 3000;

app.get('/', (req, res) => {
  res.send('Hello World from EC2!');
});

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});


Save and exit (Ctrl + O, then Enter, then Ctrl + X)

node index.js


Server is running on port 3000

curl http://localhost:3000




nano Dockerfile

const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, Emma Welcome to Cloud Environment!');
});

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});

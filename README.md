# Node.js Application Deployment on AWS EC2

## Project Overview

This project demonstrates how to deploy a simple Node.js web application on an Amazon EC2 instance. The application serves a basic HTTP response and can be accessed through a web browser using the EC2 public IP address.

---

## Architecture

```text
+-------------+
|   Browser   |
+------+------+ 
       |
       | HTTP Request
       v
+------+------+ 
| AWS EC2     |
| Amazon Linux|
+------+------+ 
       |
       | Node.js Runtime
       v
+-------------+
| index.js    |
| HTTP Server |
+-------------+
       |
       v
"Welcome to DevOps Training"
```

---

## Technologies Used

* AWS EC2
* Amazon Linux
* Node.js
* NPM
* Git & GitHub

---

## Project Structure

```text
sample_nodejs_on_Ec2/
│
├── index.js
├── package.json
├── package-lock.json
├── README.md
└── .github/
```

---

## Application Code

The application creates a simple HTTP server and listens on port 81.

```javascript
var http = require('http');

http.createServer(function (req, res) {
  res.write('Welcome to DevOps Training');
  res.end();
}).listen(81);
```

---

## Deployment Steps

### 1. Launch EC2 Instance

* Create an Amazon Linux EC2 instance.
* Configure Security Group rules:

  * SSH (22)
  * Custom TCP (81)

### 2. Connect to EC2

```bash
ssh -i key.pem ec2-user@PUBLIC-IP
```

### 3. Install Node.js

Amazon Linux 2023:

```bash
sudo dnf install -y nodejs
```

Verify installation:

```bash
node -v
npm -v
```

### 4. Clone Repository

```bash
git clone https://github.com/CloudTechDevOps/sample_nodejs_on_Ec2.git
cd sample_nodejs_on_Ec2
```

### 5. Start Application

```bash
node index.js
```

Or:

```bash
npm start
```

### 6. Verify Application

Local test:

```bash
curl localhost:81
```

Expected Output:

```text
Welcome to DevOps Training
```

Browser:

```text
http://PUBLIC-IP:81
```

---

## Security Group Configuration

| Type       | Port | Source    |
| ---------- | ---- | --------- |
| SSH        | 22   | Your IP   |
| Custom TCP | 81   | 0.0.0.0/0 |

---

## Testing

```bash
curl localhost:81
```

Output:

```text
Welcome to DevOps Training
```

---

## Learning Outcomes

* Launching AWS EC2 instances
* Installing Node.js on Amazon Linux
* Cloning projects from GitHub
* Running Node.js applications
* Configuring AWS Security Groups
* Testing web applications using curl
* Accessing applications through a public IP address

---

## Author

Kedarling Ashok Kanade

B.E. Computer Science & Engineering

GM University, Davangere

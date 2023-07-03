## Introduction
This is a side project I've been working on. A full stack invoicing application made using the MERN stack (MongoDB, Express, React & Nodejs), specially designed for freelancers and small businesses, but can be used for almost any type of business need. With this application, you can send beautiful invoices, receipts, estimates, quotes, bills, etc to your clients. Jump right off the [Live App](https://accountill.com/) and start sending invoices or download the entire [Source code](https://github.com/Panshak/accountill) and run it on your server.

![Architectural Diagram](https://github.com/nielsen2e/capstone-project/blob/master/Invoice%20Architectural%20Diagram.jpeg)

## Technology Details
You will be using the following technologies and platforms to set up a DevOps environment.

1. AWS
    - AWS will be used to host the application, cloud infrastructure, and any other services we may need to ensure the Uber app is deployed properly.
2. GitHub
    - To store the application and infrastructure/automation code
3. Nodejs
    - Nodejs will be used for the Mern app.
4. Terraform
   - Create an S3 bucket to store Terraform State files
   - Create an AWS ECR repository with Terraform
   - Create an EKS cluster
5. Docker
   - Create a Docker image
   - Store the Docker image in AWS ECR
6. Kubernetes
   - To run the Docker image that's created for the containerized Uber app. Kubernetes, in this case, EKS, will be used to orchestrate the container.
7. CI/CD
   - Use Jenkins to create an EKS cluster
8. Infracost
   - Use Infracost to check for cost changes in Terraform code
8. Automated testing
    - Testing Terraform code with Checkov
## Steps
1. VPC - When running EKS, it requires specific networking. Because all environments will most likely be different.
2. AWS:
    - Configure credentials to access AWS at a programmatic level
2. Terraform - The purpose of the Terraform section is to create all of the AWS cloud services you'll need from an environment/infrastructure perspective to run the  application.
    - Create an S3 Bucket To Store TFSTATE Files
    - Create an Elastic Container Registry
    - Create An EKS Cluster IAM Role, And Policy For EKS
      Create An EKS Cluster
4. Docker - The purpose of the Docker section is to create a Docker image from the app that the organization is running on-prem (the invoice app), containerize it, and store the container inside a container repository. For the container repo, you'll use AWS ECR.
    - Create The Docker Image
    - Log Into AWS ECR Repository
5. Kubernetes - The purpose of the Kubernetes section is to connect to EKS locally and to write the Kubernetes manifest to deploy the invoice app.
    - Connect To EKS From The Terminal
    - Create A Kubernetes Manifest
  
6. Infracost - The purpose of the Infracost section is to ensure the budget stays within the allowed limit.
   - Install Infracost
7. Automated Testing - The Automation Testing section aims to ensure that all of the Terraform code is performing as it should from a policy, security, and static code analysis perspective.
    - Install And Run Checkov
8. CICD - This section aims to automatically create an EKS cluster with CICD using Jenkins.
    - Create a Jenkins CICD pipeline
### [accountill.com](https://accountill.com/)
# MERN Stack Invoicing Application
Built with the MERN stack (MongoDB, Express, React, and NodeJS).
![Invoice](https://res.cloudinary.com/almpo/image/upload/v1637311386/invoice/invoice-app_tcz0dj.png)


## Update
I am pleased to inform you that the name of this repository has been changed from Arc Invoice to Accountill.
There are so many things coming! Stay tuned!!


Panshak
----

  * [Introduction](#introduction)
  * [Key Features](#key-features)
  * [Technologies used](#technologies-used)
      - [Client](#client)
      - [Server](#server)
      - [Database](#database)
  * [Configuration and Setup](#configuration-and-setup)
  * [Troubleshooting](#troubleshooting)
  * [Author](#author)
  * [License](#license)

## Introduction
This is a side project I've been working on. A full stack invoicing application made using the MERN stack (MongoDB, Express, React & Nodejs), specially designed for freelancers and small businesses, but can be used for almost any type of business need. With this application, you can send beautiful invoices, receipts, estimates, quotes, bills etc to your clients. Jump right off the [Live App](https://accountill.com/) and start sending invoice or download the entire [Source code](https://github.com/Panshak/accountill) and run it on your server. This project is something I've been working on in my free time so I cannot be sure that everything will work out correctly. But I'll appreciate you if can report any issue.

![Invoice Dashboard](https://res.cloudinary.com/almpo/image/upload/v1637314504/invoice/dashboard_c5z0is.png)

## Key Features
- Send invoices, receipts, estimates, quotations and bills via email
- Generate and send/download pdf invoices, receipts, estimates, quotations and bills via email
- Set due date.
- Automatic status change when payment record is added
- Payment history section for each invoice with record about payment date, payment method and extra note.
- Record partial payment of invoice.
- Clean admin dashboard for displaying all invoice statistics including total amount received, total pending, recent payments, total invoice paid, total unpaid and partially paid invoices. 
- Multiple user registration.
- Authentication using jsonwebtoken (jwt) and Google auth


## Technologies used
This project was created using the following technologies.

#### Client

- React JS
- Redux (for managing and centralizing application state)
- React-router-dom (To handle routing)
- Axios (for making api calls)
- Material UI & CSS Module (for User Interface)
- React simple Snackbar (To display success/error notifications)
- Cloudinary (to allows users to upload their business logo)
- Apex Charts (to display payment history)
- React-google-login (To enable authentication using Google)

#### Server

- Express
- Mongoose
- JWT (For authentication)
- bcryptjs (for data encryption)
- Nodemailer (for sending invoice via email)
- html-pdf (for generating invoice PDFs)

#### Database
MongoDB (MongoDB Atlas)

## Configuration and Setup
In order to run this project locally, simply fork and clone the repository or download as zip and unzip on your machine. 
- Open the project in your prefered code editor.
- Go to terminal -> New terminal (If you are using VS code)
- Split your terminal into two (run the client on one terminal and the server on the other terminal)

In the first terminal
- cd client and create a .env file in the root of your client directory.
- Supply the following credentials

```
REACT_APP_GOOGLE_CLIENT_ID = 
REACT_APP_API = http://localhost:5000
REACT_APP_URL = http://localhost:3000

```

To get your Google ClientID for authentication, go to the [credential Page ](https://console.cloud.google.com/apis/credentials) (if you are new, then [create a new project first](https://console.cloud.google.com/projectcreate) and follow the following steps;

- Click Create credentials > OAuth client ID.
- Select the Web application type.
- Name your OAuth client and click Create
- Remember to provide your domain and redirect URL so that Google identifies the origin domain to which it can display the consent screen. In development, that is going to be `http://localhost:3000` and `http://localhost:3000/login`
- Copy the Client ID and assign it to the variable `REACT_APP_GOOGLE_CLIENT_ID` in your .env file

```
$ cd client
$ npm install (to install client-side dependencies)
$ npm start (to start the client)
```
In the second terminal
- cd server and create a .env file in the root of your server directory.
- Supply the following credentials

```
DB_URL = 
PORT = 5000
SECRET = 
SMTP_HOST = 
SMTP_PORT = 
SMTP_USER = 
SMTP_PASS = 

```

Please follow [This tutorial](https://dev.to/dalalrohit/how-to-connect-to-mongodb-atlas-using-node-js-k9i) to create your mongoDB connection url, which you'll use as your DB_URL

```
$ cd server
$ npm install (to install server-side dependencies)
& npm start (to start the server)
```

## Troubleshooting
If you're getting error while trying to send or download PDF,
please run the following in your server terminal.

```
$ npm install html-pdf -g
$ npm link html-pdf
$ npm link phantomjs-prebuilt
```

## Docker

Using docker is simple. Just add the .env contextualized with the docker network.

e.g:

> goes to path "server/.env"
```
DB_URL = mongodb://mongo:27017/arch
PORT = 5000
SECRET = 
SMTP_HOST = 
SMTP_PORT = 
SMTP_USER = 
SMTP_PASS = 
```
> goes to path "client/.env"
```
REACT_APP_GOOGLE_CLIENT_ID = 
REACT_APP_API = http://localhost:5000
REACT_APP_URL = http://localhost
```

And run

```
docker-compose -f docker-compose.prod.yml build

And then

docker-compose -f docker-compose.prod.yml up
```

## Comment
I intend to keep adding more features to this application, so if you like it, please give it a star, that will encourage me to 
to keep improving the project.


## Author

- Twitter: [@panshak_](https://twitter.com/panshak_)
- Github: [@panshak](https://github.com/panshak)
- Linkedin: [@panshak](https://www.linkedin.com/in/panshak/)
- Email: [@ipanshak](mailto:ipanshak@gmail.com)

## License

- This project is [MIT](https://github.com/Panshak/accountill/blob/master/LICENSE.md) licensed.

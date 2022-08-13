<!-- PROJECT LOGO -->
<br />
    <div align="center">
    <u><h2 align="center">DEPLOY HIGHLY AVAILABLE WEB APP USING CLOUDFORMATION  </h2></u>
    </div>
<br>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li> <a href="#about-the-project">About The Project</a> </li>
    <li><a href="#architecture-diagram">Architecture Diagram</a></li>
    <li><a href="#built-with">Built With</a></li>
    <li><a href="#files-and-folders">Files and Folder</a></li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#how-to-run-the-scripts">How to run the scripts ?</a></li>
        <li><a href="#steps">Steps</a></li>
      </ul>
    </li>
    <li><a href="#demo-accessing-the-website">Demo - Accessing the Website</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>
<br>




<!-- ABOUT THE PROJECT -->
## About The Project

In this project, I deployed a sample application to to the Apache Web Server running on EC2 instances inside a Private Subnet using the CloudFormation Template ie. Infrastructure as a Code. Some of the properties used in this project are as follows :
Property | Value |
---|---|
Number of web servers | 4-6 |
Region | us-east-1 ie. North Virginia
Number of availability Zones Useed | 2
Subnet | Private
Instance Type | t2.micro |
AMI | Ubuntu18 |
Disk Space | 10GB


<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- ARCHITECTURE DIAGRAM -->
## Architecture Diagram
Following is the Architecture Diagram of the Infrastructure that was deployed using the CloudFormation Template 👇 
![Website](/img/1.%20Infrastructure_Diagram.png)


<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- BUILT WITH -->
## Built With

* [![AWS][AWS_LOGO]][AWS_URL]
* [![HTML][HTML_LOGO]][HTML_URL]

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- FILES AND FOLDERS -->
## Files and Folders
Name | Purpose |
---|---|
 /scripts|This folder contains the scripts (windows as well as linux) to Create,Update and Delete the Cloudformation stack|
network.yml | This is the template file for the Network Stack
server.yml | This is the template file for the Server Stack
parameters-network.json | This file contains the key-value for all the variables that are used in the Network Template|
parameters-server.json | This file contains the key-value for all the variables values that are used in the Server Template |
[index.html](https://drive.google.com/file/d/1ClFgDNTkaAK4CxV1aC9IGC_K_JjSwim1/view?usp=sharing) | This is the webpage used in the LaunchConfiguration 

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

Here are the steps needed to successfully finish this project. 

### Prerequisites

1. AWS account: You would require to have an AWS account to be able to build cloud infrastructure.
2. AWS CLI - You need to have AWS CLI installed and profile configured in order to run the AWS commands. You can download the AWS-CLI [**here**](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
3. VS code editor: This editor is helpful to visualize image as well as the code. You can download VS Code editor [**here**](https://code.visualstudio.com/download)
4. An account on LucidChart: In order to draw the Architecture Diagrams, you need to have a user account on [**Lucid Chart**](www.lucidchart.com) 


### How to run the scripts?
1. Create Script   
```bash
# Ensure that the AWS CLI is configured before running the command below
./create.sh stackName templateFile.yml variableFile.json
```

2. Update Script
```bash
# Ensure that the AWS CLI is configured before running the command below
./update.sh stackName templateFile.yml variableFile.json
```   

3. Delete Script
```bash
# Ensure that the AWS CLI is configured before running the command below
./delete.sh stackName
```  

### Steps

1. ***Creating Network Stack.*** <br>
Firstly, we create the Network stack using the following command :
```bash
# Ensure that the AWS CLI is configured before running the command below
./create.sh networkStack network.yml parameters-network.json

# This should give back the ARN of the created Stack
```  
   
2. ***Creating Server Stack.***<br>
Once network stack is created, we then create the server stack which using some of the resources created in the Network Stack.
```bash
# Ensure that the AWS CLI is configured before running the command below
./create.sh serverStack servers.yml parameters-server.json

# This should give back the ARN of the created Stack
```  
   
<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- DEMO-ACCESSING THE WEBSITE -->
## Demo-Accessing the Website 
* Once both the stacks are created, we can use the LoadBalancer DNS Name to access the website that is deployed on the EC2 instances in private subnets.
* To demonstrate the working of LoadBalancer, I have displayed the Private IP of the webserver on the top of the page.
* We can see that the IP address is changing which shows that the LoadBalancer is distributing the traffic across all the web servers 👇 
![Demo](/img/2.%20demo.gif)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

Name: Shubham Kandwal  
Email: shubham.0297@yahoo.in  
Project Link: [Deploying_Static_Website_On_AWS](https://github.com/shubham0297/Deploying_Static_Website_On_AWS#prerequisites)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[AWS_LOGO]: https://img.shields.io/badge/AWS-FF9900?style=plastic&logo=amazonaws&logoColor=black
[AWS_URL]: https://aws.amazon.com/
[HTML_LOGO]: https://img.shields.io/badge/HTML-20232A?style=plastic&logo=HTML5&logoColor=WHITE
[HTML_URL]: https://html.com/

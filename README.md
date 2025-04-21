# CV deployed via a Pipeline

This repository contains the source code and deployment configuration for my personal CV website, hosted on AWS. The website is built using HTML and CSS, showcasing my skills and experience.
The deployment is performed via a CI/CD pipeline using GitHub Actions.

## Architecture

![image](https://github.com/user-attachments/assets/5ba0e41a-26a1-49ae-a6e1-8ab3798b41e1)

Technologies used:
- **Git**
- **Docker/DockerHub**
- **GitHub Actions**
- **eksctl**
- **AWS Application Load Balancer (ALB)**
- **Amazon Elastic Kubernetes Service (Amazon EKS)**

## Prerequisites

To deploy this project, you need:
- An AWS account with access to Amazon EKS.
- A GitHub account
- Git and eksctl tools.

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/razackou/my-cv-CI-CD-pipeline.git
   cd my-cv-CI-CD-pipeline
   ```

   Folder Structure
    ```
    ├── images/               # Images or other static assets
    ├── index.html            # Main CV page
    ├── resume.html           # Second page
    ├── css/style.css         # CSS styles for the website
    ├── resume.pdf            # downloadable pdf version of the CV
    ├── Dockerfile            # Containerization file
    ├── deployment.yaml       # kubernetes deployment file
    ├── Action.yaml           # GitHub Actions file for CI/CD
    └── README.md             # This file
    ```
   
2. **Customize the Website:**
- Update `index.html` and `css/styles.css` with your personal CV details.
- Add any additional assets to the `images/` folder.
- Push all these to your own GitHub repository

3. **AWS Configuration:**
- eksctl:
  - Ensure that AWS credentials are well configured on your computer then install eksctl (from https://eksctl.io/) to be able to create and manage an AWS EKS Kubernetes cluster from your computer
  - Create a cluster with the command `eksctl create cluster` and check the cluster once done (`eksctl get cluster`). Cluster creation should take around 15 minutes.

    ![Screen0](https://github.com/user-attachments/assets/9c548b86-6bb8-4419-a7b3-438fed43290a)

   - Make an initial deployment of the website by running `kubectl apply -f deployment.yaml`, then run `kubectl get all` to get the LoadBalancer link and test it in a browser. Please, add `http://` before. If not working, please, allow few minutes and try again.

    ![Screen1](https://github.com/user-attachments/assets/d5824c29-1390-4903-acbc-1f66d549cae2)

4. **Pipeline setup**
- GitHub:
  - create four secrets:
    - DOCKER_HUB_USERNAME 
    - DOCKER_HUB_TOKEN 
    - AWS               #paste the content of .aws/config file.
    - KUBECONFIG        #paste the content of .kube/config file.
      ![image](https://github.com/user-attachments/assets/4937751f-c5e8-4bdc-aadb-a64bd1914293)
  - Open Actions tabs, create a new workflow and past the content of `Action.yaml` file. Make suitables changes and commit.

## Future Improvements
- Add code analysis in the Pipeline
- Implement https
- Implement backend functionality (e.g., contact form) using AWS Lambda and API Gateway.
- Enhance the website with JavaScript for interactivity.

## Contributing
This is a personal project, but feedback is welcome! Feel free to open an issue or submit a pull request with suggestions.

## License
This project is open-source — feel free to fork, modify, and copy it.

## Contact
For inquiries, reach out via [razackou@gmail.com](mailto:razackou@gmail.com) or connect with me on [LinkedIn](https://www.linkedin.com/in/razakou/).

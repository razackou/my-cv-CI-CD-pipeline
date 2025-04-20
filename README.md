# Personal CV Website

This repository contains the source code and deployment configuration for my personal CV website, hosted on AWS. The website is built using HTML and CSS, showcasing my skills and experience.

## Overview

The CV website is a static application hosted on **AWS S3**, with **Amazon CloudFront** for content delivery and caching, **AWS Route 53** for DNS management, and an **AWS Certificate Manager (ACM)** certificate for HTTPS. This project demonstrates my understanding of cloud infrastructure, static website hosting, and CI/CD practices.

## Architecture

![Drawing1jpg](https://github.com/user-attachments/assets/020089ee-0276-484a-9f75-140f2ccfcbec)

- **Frontend**: HTML and CSS for a responsive, lightweight CV page.
- **Storage**: AWS S3 bucket configured for static website hosting.
- **Content Delivery**: Amazon CloudFront for low-latency delivery and HTTPS support.
- **DNS**: AWS Route 53 for domain name resolution.
- **Security**: AWS Certificate Manager (ACM) for SSL/TLS certificate management.

## Prerequisites

To deploy this project, you need:
- An AWS account with access to S3, CloudFront, Route 53, and ACM.
- A registered domain name (managed via Route 53 or another registrar).
- Basic knowledge of HTML, CSS, and AWS services.

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/razackou/my-cv.git
   cd my-cv
   ```

2. **Customize the Website:**
- Update `index.html` and `css/styles.css` with your personal CV details.
- Add any additional assets (e.g., images) to the `images/` folder.

3. **AWS Configuration:**
- S3:
  - Create an S3 bucket with public read access and static website hosting enabled.
  - Upload the contents of the repository to the bucket.
- Route 53:
  - Create a hosted zone for your domain.
  - Add an `A` record pointing to the CloudFront distribution.
- ACM:
  - Request a public certificate for your domain.
  - Validate the certificate via DNS (Route 53 integration recommended).
- CloudFront:
  - Create a distribution with the S3 bucket as the origin.
  - Associate the ACM certificate for HTTPS.
  - Configure caching and default root object (`index.html`).

4. **Test the Website:**
- Access your domain to verify the website is live.
- Check HTTPS functionality and content delivery.

## Deployment
- Manual Deployment:
  - Upload updated files to the S3 bucket.
  - Invalidate the CloudFront cache if necessary (`/*` for all files).

- CI/CD (Optional):
  - Set up a GitHub Actions workflow to automate deployments to S3 on push to the `main` branch.
  - Example workflow: Sync files to S3 using `aws s3 sync` and invalidate CloudFront cache.

Folder Structure
```
├── images/               # Images or other static assets
├── index.html            # Main CV page
├── resume.html           # Second page
├── css/style.css         # CSS styles for the website
├── resume.pdf            # downloadable pdf version of the CV
└── README.md             # This file
```
## Future Improvements
- Add a CI/CD pipeline using GitHub Actions or AWS CodePipeline.
- Implement backend functionality (e.g., contact form) using AWS Lambda and API Gateway.
- Enhance the website with JavaScript for interactivity.
- Optimize assets for faster load times.

## Contributing
This is a personal project, but feedback is welcome! Feel free to open an issue or submit a pull request with suggestions.

## License
This project is open-source — feel free to fork, modify, and copy it.

## Contact
For inquiries, reach out via [razackou@gmail.com](mailto:razackou@gmail.com) or connect with me on [LinkedIn](https://www.linkedin.com/in/razakou/).


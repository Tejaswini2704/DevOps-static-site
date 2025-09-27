# DevOps-static-site

# 📄 **DevOps Project: Deploy Static Website on AWS S3 using GitHub Actions**

---

## **Project Overview**

This project demonstrates a simple **DevOps pipeline** that automates deployment of a static website to **AWS S3** using **GitHub Actions**.

* **Website:** Static HTML page (`index.html`)
* **CI/CD:** Automated deployment using GitHub Actions
* **Cloud Provider:** AWS S3 (Static Website Hosting)
* **Goal:** Any update pushed to the `main` branch is automatically deployed to the S3 bucket

This project is ideal for **beginners learning DevOps**, **CI/CD concepts**, and **cloud deployment**.

---

## **Technologies Used**

| Technology     | Purpose                        |
| -------------- | ------------------------------ |
| Git & GitHub   | Version Control & Repository   |
| GitHub Actions | CI/CD automation               |
| AWS S3         | Hosting static website         |
| HTML           | Frontend website               |
| IAM & Secrets  | Secure access to AWS resources |

---

## **Project Structure**

```
DevOps-static-site/
├── .github/
│   └── workflows/
│       └── deploy.yml   # GitHub Actions workflow
├── index.html           # Static website file
└── README.md            # Project information
```

---

## **Architecture Diagram**

```text
        +----------------+
        |   Developer    |
        |  (Push Code)   |
        +--------+-------+
                 |
                 v
        +----------------+
        |   GitHub Repo  |
        |  (Main Branch) |
        +--------+-------+
                 |
                 v
        +----------------+
        | GitHub Actions |
        |  (CI/CD)       |
        +--------+-------+
                 |
                 v
        +----------------+
        |    AWS S3      |
        |  (Static Site) |
        +--------+-------+
                 |
                 v
        +----------------+
        |   Users / Web  |
        |   Visitors     |
        +----------------+
```

---

## **CI/CD Pipeline Highlights**

* Automatically triggers on **push** to `main` branch
* **GitHub Actions workflow**:

  * Checks out repository
  * Configures AWS credentials securely using **secrets**
  * Syncs website files to **S3 bucket**
* Ensures that **latest code** is always live
* **Manual intervention not required**

---

## **Key Features**

* Fully automated **CI/CD pipeline**
* **Secure deployment** using GitHub Secrets
* **Scalable**: Can be extended to multiple environments (dev, staging, prod)
* **Fast & lightweight** deployment for static sites

---

## **Benefits**

* Reduces manual deployment errors
* Ensures **continuous delivery**
* Enables **version control and rollback**
* Provides a **real-world example** of DevOps principles

---

## **Future Improvements**

* Integrate **CloudFront CDN** for faster load times and HTTPS
* Use **Terraform** for Infrastructure as Code (IaC)
* Implement **monitoring & alerts** using CloudWatch
* Add **automated tests** before deployment for production readiness
* Extend project to deploy **dynamic websites** using AWS services

---

## **Author**

Built with ❤️ by **Tejaswini Shirke**

---



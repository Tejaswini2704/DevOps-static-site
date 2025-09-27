

# 🚀 **DevOps Project: Deploy Static Website on AWS S3 with GitHub Actions**

---

##  **Step 1: Create a Simple Website**

👉 Create a folder called `website` with files:

**`index.html`**

```html
<!DOCTYPE html>
<html>
<head>
  <title>My DevOps Website</title>
</head>
<body>
  <h1>Hello from DevOps 🚀</h1>
  <p>This site is deployed using AWS S3 + GitHub Actions.</p>
</body>
</html>
```

---

## **Step 2: Push Code to GitHub**

1. Initialize Git:

   ```bash
   git init
   git add .
   git commit -m "Initial commit - website"
   ```
2. Create a repo on GitHub (example: `devops-static-site`).
3. Push code:

   ```bash
   git remote add origin https://github.com/<your-username>/devops-static-site.git
   git branch -M main
   git push -u origin main
   ```

---

## **Step 3: Create AWS S3 Bucket**

1. Go to **AWS Console → S3**.
2. Create bucket → name it `my-devops-site-123` (must be unique globally).
3. Enable:

   * **Block Public Access → OFF**
   * **Bucket Policy → Public Read**
4. Enable **Static Website Hosting**:

   * Index document: `index.html`.

Now test by uploading `index.html` manually → check **Bucket Website Endpoint**.

---

## **Step 4: Create IAM User for GitHub Actions**

1. Go to **IAM → Users → Add User** (name: `github-actions-user`).
2. Assign policy:

   * **AmazonS3FullAccess** (or more restrictive later).
3. Download **Access Key + Secret Key**.

---

## **Step 5: Add Secrets in GitHub**

1. Go to your **GitHub repo → Settings → Secrets and variables → Actions → New Repository Secret**.
2. Add:

   * `AWS_ACCESS_KEY_ID`
   * `AWS_SECRET_ACCESS_KEY`
   * `AWS_REGION` (e.g., `ap-south-1`)
   * `S3_BUCKET` (your bucket name)

---

## **Step 6: Create GitHub Actions Workflow**

👉 In your repo, create folder `.github/workflows/deploy.yml`

**`deploy.yml`**

```yaml
name: Deploy to S3

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v4
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: ${{ secrets.AWS_REGION }}

      - name: Sync files to S3
        run: aws s3 sync . s3://${{ secrets.S3_BUCKET }} --delete
```

---

## **Step 7: Test CI/CD**

1. Commit and push workflow:

   ```bash
   git add .
   git commit -m "Add GitHub Actions workflow for S3 deployment"
   git push
   ```
2. Go to GitHub → Actions tab → Watch pipeline run.
3. If successful, visit your **S3 Website URL** → updated site 🎉.

---

✅ Done! You now have:

* A **static site on AWS S3**.
* **CI/CD pipeline** with GitHub Actions.
* Every `git push` → auto deploys 🚀.

---

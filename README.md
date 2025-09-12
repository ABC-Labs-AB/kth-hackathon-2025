# kth-hackathon-2025
Information for KTH AI Society hackathon 2025

<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [kth-hackathon-2025](#kth-hackathon-2025)
- [Participant Guide](#participant-guide)
    - [🚀 Quick Start](#🚀-quick-start)
        - [What You'll Get](#what-youll-get)
        - [Access Requirements](#access-requirements)
    - [📝 Before the Hackathon](#📝-before-the-hackathon)
        - [1. Verify Your Access](#1-verify-your-access)
        - [2. Familiarize Yourself with GCP Console](#2-familiarize-yourself-with-gcp-console)
        - [3. Optional Preparation](#3-optional-preparation)
    - [🎯 During the Hackathon](#🎯-during-the-hackathon)
        - [Step 1: Access Your Project](#step-1-access-your-project)
        - [Step 2: Access Your Vertex AI Workbench Instance](#step-2-access-your-vertex-ai-workbench-instance)
        - [Step 3: Load the Starter Notebook](#step-3-load-the-starter-notebook)
        - [Step 4: Access Your Data](#step-4-access-your-data)
    - [💻 Working Environment](#💻-working-environment)
        - [Pre-installed Tools](#pre-installed-tools)
        - [Compute Resources](#compute-resources)
        - [Available GCP Services](#available-gcp-services)
    - [📊 Managing Your Budget](#📊-managing-your-budget)
        - [Budget Limit](#budget-limit)
        - [Cost-Saving Tips](#cost-saving-tips)
        - [Checking Your Usage](#checking-your-usage)
    - [🛠️ Useful Commands](#🛠️-useful-commands)
        - [In JupyterLab Terminal](#in-jupyterlab-terminal)
        - [In Python Notebooks](#in-python-notebooks)
    - [❓ Troubleshooting](#❓-troubleshooting)
        - [Can't access the GCP Console](#cant-access-the-gcp-console)
        - [Can't see your project](#cant-see-your-project)
        - [Notebook instance won't start](#notebook-instance-wont-start)
        - [Permission denied errors](#permission-denied-errors)
    - [📞 Getting Help](#📞-getting-help)
        - [During the Hackathon](#during-the-hackathon)
        - [Useful Resources](#useful-resources)

<!-- markdown-toc end -->


# Participant Guide

Welcome to the Hackathon! This guide contains everything you need to get started with your team's Google Cloud Platform (GCP) environment.

## 🚀 Quick Start

### What You'll Get
- **GCP Project**: `kth-team-XX` (where XX is your team number)
- **Budget**: $200 USD for the duration of the hackathon
- **Vertex AI Workbench**: Pre-configured Jupyter notebook environment
- **Cloud Storage Bucket**: For your data and results
- **Pre-loaded Data**: Hackathon dataset in your bucket

### Access Requirements
- **Google Account**: You'll need a Google account (Gmail, Workspace, or any Google-compatible email)
- **Team Assignment**: You should have received your team number and project access via email

## 📝 Before the Hackathon

### 1. Verify Your Access
You should have received an email invitation to join your team's GCP project. Please:
1. Check your email for an invitation from Google Cloud
2. Accept the invitation by clicking the link
3. Sign in with your Google account

### 2. Familiarize Yourself with GCP Console
- Visit [console.cloud.google.com](https://console.cloud.google.com)
- You should see your project `kth-team-XX` in the project selector (top left)
- If you don't see it, check that you're logged in with the correct Google account

### 3. Optional Preparation
- Review [Vertex AI Workbench documentation](https://cloud.google.com/vertex-ai/docs/workbench/introduction)
- Familiarize yourself with [Google Cloud Storage](https://cloud.google.com/storage/docs)

## 🎯 During the Hackathon

### Step 1: Access Your Project
1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Sign in with your Google account
3. Select your project from the dropdown at the top: `kth-team-XX`

### Step 2: Access Your Vertex AI Workbench Instance
1. In the GCP Console, navigate to: **Vertex AI** → **Workbench** → **Instances**
2. You'll see an instance named `hackathon-notebook`
3. Click on the instance name
4. Click **OPEN JUPYTERLAB** to launch your notebook environment

> **Note**: The instance may take 1-2 minutes to start if it's stopped. Just click "START" if needed.

### Step 3: Load the Starter Notebook
Once in JupyterLab:
1. Open a terminal: **File** → **New** → **Terminal**
2. Download the starter notebook:
   ```bash
   gsutil cp gs://${GOOGLE_CLOUD_PROJECT}-data/notebooks/hackathon_starter.ipynb .
   ```
3. Open the notebook from the file browser on the left
4. Follow the instructions in the notebook to get started!

### Step 4: Access Your Data
Your team's data is stored in Google Cloud Storage:
- **Bucket name**: `kth-team-XX-data` (automatically detected in the notebook)
- **Data location**: `gs://kth-team-XX-data/data`

The starter notebook shows you how to:
- Load data from your bucket
- Process and analyze the data
- Save results back to the bucket

## 💻 Working Environment

### Pre-installed Tools
Your Vertex AI Workbench instance comes with:
- **Python 3.10+**
- **Machine Learning Frameworks**: TensorFlow, PyTorch, scikit-learn
- **Data Science Libraries**: pandas, numpy, matplotlib, seaborn
- **Google Cloud SDKs**: Pre-configured access to all GCP services

### Compute Resources
- **CPU**: 4 vCPUs (n1-standard-4)
- **Memory**: 15 GB RAM
- **Storage**: 150 GB boot disk + 100 GB data disk
- **GPU**: Available on request (NVIDIA Tesla T4)

### Available GCP Services
You have access to (but not obliged to) use:
- **Cloud Storage**: For data and model storage
- **BigQuery**: For large-scale data analysis
- **Vertex AI**: For ML model training and deployment
- **Cloud Run**: For deploying applications

## 📊 Managing Your Budget

### Budget Limit
- Each team has a **$200 USD budget**
- The project will stop accepting new resources once the budget is reached

### Cost-Saving Tips
1. **Stop your notebook instance** when not in use (it auto-saves your work)
2. **Delete unused resources** (old models, temporary data)
3. **Use spot/preemptible instances** for training if possible
4. **Monitor your usage** in the Billing section of GCP Console

### Checking Your Usage
1. Go to **Billing** in the GCP Console
2. View your current spend and remaining budget
3. See which services are consuming your budget

## 🛠️ Useful Commands

### In JupyterLab Terminal

```bash
# List files in your bucket
gsutil ls gs://${GOOGLE_CLOUD_PROJECT}-data/

# Copy files from bucket
gsutil cp gs://${GOOGLE_CLOUD_PROJECT}-data/myfile.csv .

# Upload results to bucket
gsutil cp results.csv gs://${GOOGLE_CLOUD_PROJECT}-data/results/

# Check your project ID
echo $GOOGLE_CLOUD_PROJECT
```

### In Python Notebooks

```python
# Your project ID is automatically available
import os
PROJECT_ID = os.environ['GOOGLE_CLOUD_PROJECT']
BUCKET_NAME = f"{PROJECT_ID}-data"

# Read data directly from GCS
import pandas as pd
df = pd.read_csv(f"gs://{BUCKET_NAME}/test.csv")

# Save results to GCS
df.to_csv(f"gs://{BUCKET_NAME}/results/output.csv", index=False)
```

## ❓ Troubleshooting

### Can't access the GCP Console
- Ensure you're using the email address that received the invitation
- Try incognito/private browsing mode
- Clear browser cache and cookies for console.cloud.google.com

### Can't see your project
- Check the project selector dropdown (top of console)
- Verify you accepted the email invitation
- Contact hackathon organizers with your email address

### Notebook instance won't start
- Check if you've hit your budget limit
- Try refreshing the page
- Ensure you're in the correct project

### Permission denied errors
- Your access is time-limited and will expire after the hackathon
- Verify you're working within your team's project
- Don't try to access other teams' resources

## 📞 Getting Help

- Ask organizers or mentors on-site
- Send request to [hackathon-admins@abclabs.se](mailto:hackathon-admins@abclabs.se)
- Write in Slack channel, [kth-hackathon-2025](https://abc-labs-sweden.slack.com/archives/C094094JGKS)

### Useful Resources
- [Vertex AI Workbench Docs](https://cloud.google.com/vertex-ai/docs/workbench/user-guide)
- [GCS Python Client](https://cloud.google.com/storage/docs/reference/libraries#client-libraries-usage-python)
- [Pandas GCS Integration](https://pandas.pydata.org/docs/user_guide/io.html#google-cloud-storage)


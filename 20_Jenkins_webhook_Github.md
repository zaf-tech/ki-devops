# Github To Jenkins WebHook

## Contents
- [Intro](#intro)
- [Setup](#setup)
- 


## Intro
A GitHub to Jenkins webhook allows GitHub to notify Jenkins about events, such as code pushes or pull requests, to trigger builds automatically. Here's a step-by-step guide to set it up:


### 1- Prerequisites
    - Jenkins is set up and running with a public-facing URL (or accessible via a reverse proxy, such as Nginx).
    - Jenkins has the GitHub plugin or GitHub Integration plugin installed.
```
Required Plugins
- Github Plugin 
- GitHub Integration Plugin
```
    - GitHub repository to connect with Jenkins.
### 2- Enable Webhook in GitHub
Go to your GitHub repository.

## Setup 

Navigate to Settings > Webhooks.

Click Add webhook.

Fill in the details:

Payload URL: Enter your Jenkins URL followed by /github-webhook/. Example:

```
https://your-jenkins-server/github-webhook/
Content type: Set to application/json.
Secret: (Optional) Add a secret key for secure communication. Make sure to configure this secret in Jenkins too.
Which events would you like to trigger this webhook?:
Choose "Just the push event" (for basic builds on push), or "Let me select individual events" for custom triggers like pull requests.
Click Add webhook.
```
### 3- Configure Jenkins Job
    For Freestyle Jobs:
    - Jenkins, create or open a Freestyle project.
    - Under Build Triggers, check the box for GitHub hook trigger for GITScm polling.

    For Pipeline Jobs:
    - Create or open a Pipeline project.
    - Define your pipeline script and make sure your repository URL is specified in the checkout step.
    - Under Build Triggers, check the box for GitHub hook trigger for GITScm polling.

### 4- Test the Webhook
- In GitHub, go back to Settings > Webhooks and click the Recent Deliveries section for your webhook.
- Push some code or trigger an event in the repository.
- Check if the webhook delivery was successful (green checkmark) and Jenkins triggered a build.

### 5- Secure the Webhook (Optional)
- Add a secret to the GitHub webhook and configure Jenkins to verify it.
- In the GitHub webhook, add a secret in the Secret field.
- In Jenkins, configure the same secret under the GitHub plugin settings (Manage Jenkins > Configure System > GitHub plugin).
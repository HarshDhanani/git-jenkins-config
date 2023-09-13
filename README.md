# Jenkins Configuration Guide

This guide will help you configure Jenkins using two methods: via webhook and an alternative method.

## Prerequisites

- Jenkins server up and running
- GitHub account

## Method 1: Configuration via Webhook

1. **Create a new job in Jenkins**
   - Go to your Jenkins dashboard and click on 'New Item'.
   - Enter a name for the job, select 'Freestyle project', and click 'OK'.

2. **Configure the job**
   - In the 'Source Code Management' section, select 'Git'.
   - Enter your repository URL in the 'Repository URL' field.

3. **Set up the webhook in GitHub**
   - Go to your GitHub repository, click on 'Settings' > 'Webhooks' > 'Add webhook'.
   - In the 'Payload URL', enter `http://<your-jenkins-url>/github-webhook/`.
   - Set content type as `application/json`.
   - Select 'Just the push event'.
   - Ensure 'Active' is checked and click on 'Add webhook'.

4. **Trigger builds with the webhook**
   - In your Jenkins job configuration, under 'Build Triggers', select 'GitHub hook trigger for GITScm polling'.

## Method 2: Alternative Configuration Method

1. **Create a new job in Jenkins**
   - Follow steps 1 and 2 from Method 1.

2. **Polling the SCM**
   - In your Jenkins job configuration, under 'Build Triggers', select 'Poll SCM'.
   - In the Schedule box, enter a cron expression for how frequently you want polling to occur.

3. **Triggering builds**
   - Commit and push changes to your GitHub repository.
   - Jenkins will poll the repository based on your schedule and trigger a build when changes are detected.

**Note:** This method may result in a delay between pushing changes and triggering builds, depending on your polling frequency.

## Conclusion

You now have two methods to configure Jenkins with your GitHub repository. Choose the one that best suits your needs.

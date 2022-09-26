# OWASP-ZAP-Jenkins-Automation
This is a script to integrate DAST Capabilities using OWASP ZAP into CICD pipeline via Jenkins.
Customization can be done as per use case.

## Prerequisites
Make sure the folowing are taken care of:
1. Unset CSP, for inline CSS to work for the report generated
Refer: https://wiki.jenkins.io/JENKINS/Configuring-Content-Security-Policy.html#:~:text=default-src%20'self'%3B%22)-,unset%20the%20header%3A,-System.setProperty(%22hudson
Create a Job and use the `Jenkinsfile` from "Build Start". Execute it & the CSP will be unset.

In case your jenkins instance/service restarts, the CSP Setting will be reset to default. So, automate the build to run the build as Jenkins service starts by using Startup Trigger Plugin (https://plugins.jenkins.io/startup-trigger-plugin/)

 2. For sudo to execute, run the following commands:

```
sudo su    
visudo -f /etc/sudoers
```
add add following line at the end.

```
jenkins ALL= NOPASSWD: ALL

```
Refer: https://stackoverflow.com/a/20241946

## OWASP ZAP - Jenkins Integration
Create a job using the `Jenkinsfile` at "OWASP DAST - Jenkins". Run the job. The Parameters to be fed while running the job are intuitive and easy to understand. After execution, you can find your report in the Workspace.

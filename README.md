# instruqt

## Updating Jenkins plugins

The Securing Ci/CD Pipelines tutorial uses a pre-configured Jenkins container
which has a number of plugins installed. We need to periodically update those
plugins. Here's how to do it:
- From env/conjur-instruqt/env/conjur-jenkins, run 
  `docker run -p 8081:8080 -p 50000:50000 -v $(pwd)/jenkins_home:/var/jenkins_home jenkins/jenkins:lts`
- This might take a few minutes to run. When the command prompt says "Jenkins is fully up and running", 
  open a browser and navigate to https://localhost:8081. You should get a Jenkins login prompt.
- The credentials are found in this repo in tracks/conjur.org/secure-ci-cd-pipelines/01-jenkins-login/assignment.md
- Log into Jenkins. Click the "Manage Jenkins" link in the left sidebar, then the "Manage Plugins" link 
  in the lower right corner of the page.
- Jenkins should default to the Updates page. Update all the plugins.
- Jenkins will want to restart once it's downloaded everything. It'll probably kill your
  Docker command. 
- Check there are no more updates available.
- Commit your large number of changed files, and follow the normal PR process.
- Merging the PR to master will push the changes to the live tutorial automatically.

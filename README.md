# msa-devops

## application URL
https://msa-devops-app.azurewebsites.net

## Build Pipeline Description
The build pipeline will run everytime a commit is made to either development or master branches. It requires that npm be installed, and then runs tasks in order. Firstly, it uses npm to install node.js, before using the newly installed node.js on the VM to build the react app. It then packages the build as an artifact in a compressed zip format.

## Release Pipeline Description
The release pipeline only runs whenever a commit to master is made, unlike build. It runs the build pipeline, before taking the resulting output of the build pipeline and deploying it to the relevant server.

# msa-devops

## application URL
https://msa-devops-app.azurewebsites.net

## Build Pipeline Description
The build pipeline will run everytime a commit is made to either development or master branches. It requires that npm be installed, and then runs tasks in order. Firstly, it uses npm to install node.js, before using the newly installed node.js on the VM to build the react app. It then packages the build as an artifact in a compressed zip format.

The build pipeline is run on every commit to make sure that during development, any commits to the remote repository do not break the build for whoever is pulling the repo, and to ensure that if the build is broken that either the commit is reverted/rejected, or notifies the person who pushed it to fix it.

## Release Pipeline Description
The release pipeline only runs whenever a commit to master is made, unlike build. It runs the build pipeline, before taking the resulting output of the build pipeline and deploying it to the relevant server.

The release pipeline only needs to run whenever a commit to master is made as master should only be commited to via a PR to merge a development branch. This means that the code on master is usually a complete featureset, or a set of bug fixes. This allows for the master branch to release automatically, without the need for someone to manually move the build artifact to the azure to deploy the release.

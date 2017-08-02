## Files for the kieker-machines playbook
The following files need to be inside this directory with the listed names for the playbook to work without any customizations:
* id_rsa.kieker-admin (Private SSH key used for logging into the machine as the `docker` user)
* id_rsa.kieker-jenkins.pub (Public SSH key that allows the Jenkins server to connect as the `jenkins` user to execute builds)
* id_rsa.kiekerci-github (Private SSH key that is used to push a `master` branch content that successfully passed the pipeline to the `stable` branch at github)

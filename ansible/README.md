## Kieker Ansible Playbook

The Kieker Ansible playbook currently contains groups for Jenkins workers and LiveDemo machines.

### Prerequisites
The following prerequisites have to be met to use the provided playbook.

#### Inventory file
In order to use the playbook, you need to define the hosts listed in the `inventory` file.
If you can access a host in the list by just running `ssh <myhostname>` this should be fine.
Depending on their intended role, they should be in the corresponding group.
Currently, the structure in the `inventory` file is as follows:
* docker (group)
  * jenkins (group)
    * kieker-jenkins-worker-1
    * kieker-jenkins-worker-2
  * livedemo (group)
    * kieker-live-demo-nightly
    * kieker-live-demo-release

#### Key files
To set the machines up, some SSH-Keys are needed. These have to be placed inside the `files` subdirectory.
* `id_rsa.kieker-admin` (Private SSH key used for logging into the machine as the `docker` user)
* `id_rsa.kieker-jenkins.pub` (Public SSH key that allows the Jenkins server to connect as the `jenkins` user to execute builds)
* `id_rsa.kiekerci-github` (Private SSH key that is used to push a `master` branch content that successfully passed the pipeline to the `stable` branch at github)
    
### Assumptions
Currently, we assume that all machines are running Debian Jessie with a user `debian` which has the right to use `sudo` without entering a password.
Furthermore, we assume that we can login with the `debian` user using `pubkey`-authentication.

(This is the default for our OpenStack setup right now)

### Running the ansible playbook
To apply the playbook to the hosts in the inventory, run the following in this (`ansible`) folder:

`ansible-playbook -i inventory kieker-machines.playbook`

* `-i inventory` specifies the inventory file to use

* `kieker-machines.playbook` specifies the playbook to use

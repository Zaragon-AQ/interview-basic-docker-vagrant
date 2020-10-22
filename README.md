# DevOps very basic challange

## exercise one

1. Install Vagrant and Virtualbox on your laptop if they are not already installed
2. Create a Vagrant machine with an Ubuntu 18.04 image
3. From the Vagrantfile, used to create the virtual machine, run an ansible playbook that:
   - update the VM
   - if at least one pkg has been updated reboot the VM
   - create a group `wheel`
   - create a user `deploy` in `wheel` group with `/bin/bash` as shell without password
   - permit `sudo` without password for group `wheel`
   - add your ssh public key for the user `deploy`
   - disable `root` access through ssh even with an ssh key
4. Test if it is working doing an ssh to the VM with your ssh key and user `deploy`. Make sure you could become `root` without password
5. Prepare another ansible playbook that:
    - install docker on the VM
    - ensure docker will start at the next reboot
6. Run the `point 5 playbook` with the VM as host (Use user `deploy` with your ssh key for authentication)
7. Ensure docker is running on the VM and will start at the next reboot

## exercise two

Do the [exercise one](#exercise-one) than:

1. Create a dockerfile that:
   - use ubuntu 18.04 image as base image
   - install nginx
   - clone your github repository `sighup-challenge2` that contains an html `welcomepage.html`
   - use this `welcomepage.html` as default welcome page for nginx

2. Create a new ansible playbook that (use the `deploy` user to apply the playbook) deploy the container with the dockerfile created in the previous point

3. Ensure from your laptop browser you are able to see the welcome page from your docker container in the Vagrant machine

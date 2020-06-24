# Vagrant

### What goes on the vagrant file? 
1. config.vm.box | This is our Operating System! We will be using ubuntu/xenial64 bit
2. config.vm.provider | This is VirtualBox
3. config.vm.network | How your host computer sees your box
4. config.vm.synced_folder | How you access files from your computer
5. config.vm.provision | What do we want to run as a provision for shell commands. What dependencies are needed? Node js? nginx? If we dont use provisions, Vagrant will just run a blank ubuntu server

### how do i send a folder into my VM?
```bash
config.vm.synced_folder("app", "/app")
``` 
1. The first parameter is a path to a directory on the host machine. If the path is relative, it is relative to the project root.

2. The second parameter must be an absolute path of where to share the folder within the guest machine. This folder will be created (recursively, if it must) if it does not exist. By default, Vagrant mounts the synced folders with the owner/group set to the SSH user and any parent folders set to root.

### how do I write a script (sh) for my VM?
1. create a .sh file called provision.sh

2. put all the bash commands you want to run when provisioning (setting up) the virtual machine

3. 
```bash
config.vm.provision "shell", path: "environment/provision.sh"
```

### how do I spin up a VM?

```bash
vagrant up
```
In less than a minute, this command will finish and you will have a virtual machine running Ubuntu. You will not actually see anything though, since Vagrant runs the virtual machine without a UI. We can visually see the virtual machine in VirtualBox

### how do I destroy a VM?
```bash
vagrant destroy
```

### how do I re re-run the provision script without killing/destroy the VM?

```bash
vagrant provision

vagrant reload
```

This command is a great way to quickly test any provisioners, and is especially useful for incremental development of shell scripts. You can just make simple modifications to the provisioning scripts on your machine, run a vagrant provision and vagrant reload. Then check for the desired results.

### DO I have ruby?
```bash
ruby -v
```

### do I have bundler?

```bash
budle check
```
bundle check - Verifies if dependencies are satisfied by installed gems

check searches the local machine for each of the gems requested in the Gemfile. If all gems are found, Bundler prints a success message and exits with a status of 0.


If not, the first missing gem is listed and Bundler exits status 1.
### have I installed all the ruby dependencies to run the test? 
bundle install
### how do I run the test? 
rake spec
### Am I in the right location to run these commands? 
before you run rake spec, are you in the spec-tests folder. Or if the folder is called something ese, do you have a Rakefile inside? do you have a spec folder inside? 
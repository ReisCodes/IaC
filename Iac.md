# Infrastructure as Code (IaC)

### What is IaC?

(To codify everything you need to be implemented.)

Infrastructure as Code (IaC) is the managing and provisioning of infrastructure through code instead of through manual processes.

you create configuration files which contain your infrastructure specifications, making it easier to modify and distribute configurations. 

Means you can provision the same environment every time. 

### Benefits

Some of the benefits consist of:

- Cost reduction

- Speed 

- Low risk of human Errors

- Improved consistency

- Eliminate configuration drift

- Improved security strategies 

### Configeration management 

Leading on from the benefit of eliminating configuration drift, IaC can deploy the same code several times, but once the first deployment is done, subsequent ones have no effect. This is why IaC is deemed ‘idempotent’. This is one of the biggest benefits of infrastructure as code for configuration. This feature prevents configuration drift. This means the specifications of your environment are within the code itself.

Hence, if an error occurs which changes a resource or removes an element, your code will remain the same. Any such errors will automatically be corrected without human assistance.

## Ansible 

### What is Ansible?

Ansible is a powerful automation tool, primarily for cross-platform computer support. Its key functions are app deployement, updates on workstations and servers, cloud provisioning and in our case configuration management, but this software has many use cases. 

Some of its benefits are:

- Simple to Learn (Easily understandable python language)

- No Dependencys on agents 

- Playbooks are written in YAML

Playbooks are Ansible configuration files, and the language for writing them is YAML. The interesting factor, in this case, is that YAML is a better alternative for configuration management and automation.

The superiority of YAML over other formats like JSON makes Ansible better configuration management and automation tool. Ansible makes it easy to read and supports comments. Most important of all, it also includes the use of anchors to reference other items.

![](IaC.png)

### Making Our Own IaC with Ansible

1. First thing we need to do is to ensure we have vagrant and virtualbox installed.

<br>

2. We then need to create our vagrant file within our directory with 

```
vagrant init
```

3. Next we need to append this `Vagrantfile` in our directory with the following script, this script creates 3 VM's the controller, the app and the db with some depeddencies already in place like the OS:

```
# -*- mode: ruby -*-
# vi: set ft=ruby :
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# MULTI SERVER/VMs environment 
#
Vagrant.configure("2") do |config|
  # creating are Ansible controller
     config.vm.define "controller" do |controller|
       
      controller.vm.box = "bento/ubuntu-18.04"
      
      controller.vm.hostname = 'controller'
      
      controller.vm.network :private_network, ip: "192.168.33.12"
      
      # config.hostsupdater.aliases = ["development.controller"] 
      
     end 
  # creating first VM called web  
     config.vm.define "web" do |web|
       
       web.vm.box = "bento/ubuntu-18.04"
      # downloading ubuntu 18.04 image
       web.vm.hostname = 'web'
       # assigning host name to the VM
       
       web.vm.network :private_network, ip: "192.168.33.10"
       #   assigning private IP
       
       #config.hostsupdater.aliases = ["development.web"]
       # creating a link called development.web so we can access web page with this link instread of an IP   
           
     end
     
  # creating second VM called db
     config.vm.define "db" do |db|
       
       db.vm.box = "bento/ubuntu-18.04"
       
       db.vm.hostname = 'db'
       
       db.vm.network :private_network, ip: "192.168.33.11"
       
       #config.hostsupdater.aliases = ["development.db"]     
     end
  
  end

```

4. Once these are up and running on virtualbox, we need to open a new git bash (terminal bash) for each VM and run our update and upgrade commands:

```
sudo apt update -y
sudo apt upgrade -y
```

5. Now we just need to be in the window for the controlller VM, python is already installed so to install ansible we need to input:

```
sudo apt install software-properties-common

sudo apt-add-repository ppa:ansible/ansible

sudo apt update -y

sudo apt install ansible
```

6. Once these are run we can check that ansible is working by ssh'ing into with (password is vagrant):

```
ssh vagrant@<VM IP>
```

7. Once we have established this connection we can exit ansible:

```
exit
```



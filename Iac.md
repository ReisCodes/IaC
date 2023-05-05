# Infrastructure as Code (IaC)

### What is IaC?

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


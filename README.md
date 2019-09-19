



https://www.redhat.com/en/resources/ansible-automation-use-cases-for-telecommunications-service-providers-overview 




Problem:
Legacy VNFs rely on local filesystem storage, single server implementations, and manually intensive processes. They are difficult to automate and scale and lack high-availability capability. They are also difficult to test and upgrade

Proposed Solution:
Ansible Automation compares state and configuration information to expected values, and reports conflicts and deviations, enabling timely remediation, compliance and risk mitigation.
Ansible Tower allows scheduling of the validation process on a repeated basis to enforce security policies across all devices.

Potential Outcome:
Lower operations costs, guaranteed quality of configuration information, more up-to-date configurations.



https://docs.openstack.org/tacker/pike/contributor/vnfd_template_description.html


Biggest pain point: how to automate and scale consistent deployment. In legacy systems had to access local file systems, plan in advance & manually do one by one. With automation can deploy many in 

?? Any telco specific messaging? Also get the intro & closing (reach out to xyz) from Telco








How Ansible can help automating VNF configuration deployment


1.Model Driven Architecture with Ansible


In a traditional telco network, you will spend 4-6 weeks deploying a service.
You need to purchase, install and configure with vendor CLI tooling, provisioning service.
It is a long process.

Leverage Ansible to separate data model from execution to deliver multi vendor orchestration.
Enhance network operation models through scalable, repeatable pattern

When you virtualize your applications using virtual machines and hardware, you can accelerate the process. You will do configuration to specify where to deploy it, and how to configure it.
If we can describe our services using code based template standard, such as Anisble playbook, to specify how many VNF your service has, how many components the VNF has, how the components are interconnected. We can use Anisble to do automatic deployment and monitoring.

Anisble benefits:
Testing playbook in test environment before production
Playbook versions and source control



2. Devops

Prepare your application to be CI / CD (continuously integrated, continuously deployed) including integrated tests and monitoring

 
3. Cloud Native VNF
In the legacy network application running on blade servers, one box may have 10-20 blades. 3 blades are used as network controllers, the other are used for running the payloads. First approach is to put the service running in these blades to virtual machines. However, when you replicate the virtual machines, you will also replicate the software running inside the virtual machines, and things that you don’t need. It is not scalable. We need to think about how to transform the traditional applications to cloud native apps. What are the characteristics of the cloud native VNFs?
Scalable
Self Healing
Support DevOps approach
Decompose to micro-services with APIs to talk to each others

The micro services need to contain the logic functions of the traditional network functions
Examples include database storing how much data you can use, how many minutes you can use with your phones, your personal data, contacts, etc
Network functions to process MAP (Mobile Application Protocol) traffic. Requests are coming from different nodes in the network to retrieve information, or modify the profile, etc

We need to decompose the applications to micro services. When there is a high peak traffic in the network, I can scale up the micro services.
If my service farm is running out of memory or running out of disks, I can scale my databases.


Sometimes you may still need to keep the legacy VNF because they are expensive to replace.
Ansible can deal with the legacy VNF.
Traditional VNF network functions use PCI address to consistently name the network interfaces for connection
When you virtualize the application, we can still do PCI address injection to the virtual environment.
PCI address injection can be done in the cloud.


Tenant Point of View



Tenant wants to interfaces in this network. Please inject two PCI addresses.



Nova Point of View


Nova is more complicated. Nova is a multi-visor system. Nova handles KVM, Hyper-V, VMWare, XEN. Tenant would not know which hardware will be used. Some hardware does not support PCI. Nova should not expose this level of details to the tenant. 

Virtual Device Role Tagging

Use can put a tag to a PCI device
The tag information will be stored in the metadata service
The tag information can be retrieved from the metadata service
Ansible can take the PCI address, identify the device, put the information to the network to do the functions.

Ansible Playbook Cloud Provider - specify which cloud to use for deployment
Ansible Playbook VNF Config






# Ansible netconf modules with IOS XE routers

This lab excercise will get you started using netconf module that is included in Ansible 2.5 and later to interact with IOS XE routers. Additional information about the module can be found at[https://docs.ansible.com/ansible/2.5/modules/netconf_config_module.html#netconf-config-module](https://docs.ansible.com/ansible/2.5/modules/netconf_config_module.html#netconf-config-module).

## Objective

The objective of this lab is to show how to:

* Use the netconf module to define NTP server on IOS-XE router
* Use the netconf module to create loopback and assign IP on IOS-XE router

## Prerequisites
To complete this lab you need:

* A development environment with Ansible 2.5 and a compatible version of Python.  If you are at a DevNet Event using a provided workstation, you are ready to go.  If you are working from your own workstation, please review the ***"How to setup your own computer"*** link at the top of this page.  
* Lab infrastructure to target API calls and code.  These labs and code examples are written to leverage the [DevNet IOS XE Always On Sandbox](https://devnetsandbox.cisco.com/RM/Diagram/Index/27d9747a-db48-4565-8d44-df318fce37ad?diagramType=Topology).  This lab is available for anyone to use, with only access to the Internet as a requirement. To use a different device, ensure the device is running IOS XE 16.6 or higher.

You should also have an understanding of these foundational topics:
* The previous labs in the **"Intro to Ansible for IOS-XE"** Learning Lab Module.  
* Ability to read and understand Netconf configuration example. You can explore the **"Introduction to Model Driven Programmability"** module available on DevNet for an introduction to Netconf.
* Students are encouraged to have a basic understanding of Ansible. This module will cover some basics, but students requiring additional background are encouraged to review [Introduction to Ansible](https://learninglabs.cisco.com/modules/sdx-ansible-intro). 

#### Next: [Define NTP with Netconf](2-create-ntp.md)

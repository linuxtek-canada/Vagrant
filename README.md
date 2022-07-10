# Vagrant Repository

This repository is used for storing code used for spinning up a local Linux environment using VirtualBox.

The environment can be used for setting up a virtual environment and packaging Python code, or as a development environment hooked in with Visual Studio Code.

## Table of Contents

[TOC]

## Background

[Vagrant](https://www.vagrantup.com/intro) is a tool for building and managing virtual machine environments in a single workflow.  Vagrant gives you a disposable environment and consistent workflow for developing and testing infrastructure management scripts.

For this example, we will use Vagrant to spin up a virtual machine on your local machine using VirtualBox, but the same workflow can be used with other virtualization software or cloud providers.

## Prerequisites

* Install the latest version of [Virtualbox](https://www.virtualbox.org/wiki/Downloads) on your local machine.
* Install the latest version of [Vagrant](https://www.vagrantup.com/downloads) on your local machine.

## Usage

* Create a folder for your Vagrant project.  It is recommended not to use any spaces in the directory path.  

    * On Windows, the recommended location is `C:\users\username\Vagrant\project-name`.

    * On MacOS, the recommended location is `~/vagrant/project-name`.

    * On Linux, the recommended location is `~/vagrant/project-name`.

* In a command line, access the directory and run the command `vagrant init`.  This will initialize the directory and create an empty Vagrantfile.  The Vagrantfile is a Ruby file used to configure Vagrant on a per-project basis. The main function of the Vagrantfile is to described the virtual machines required for a project as well as how to configure and provision these machines. 

* Download the `Vagrantfile` from the repo for the appropriate distribution, and add it to the `project-name` folder, overwiting the empty file.

* Inside your Vagrant project folder, create a `Data` folder.  This will be a synchronized directory between your local machine and the virtual machine in Virtualbox, which will allow you to quickly transfer files in/out of the virtual machine.

* Edit the `Vagrantfile` and add values for the NEW_USER_NAME and NEW_USER_PASSWORD variables.  This will be the Linux user created automatically as the box is provisioned.

* In a command line access the directory and run the following commands:

```
vagrant plugin install vagrant-vbguest
vagrant up
vagrant vbguest
```

vagrant-vbguest is a Vagrant plugin which automatically installs the host's VirtualBox Guest Additions on the guest system.

**Note:** It may take a while to bring up the virtual machine the first time, as it will need to download the base OS box, then download and install all of the additional packages.  Be patient.  The virtual machine will reboot a few times during the process.

## SSH Access

To ssh into the virtual machine, in your command line, run `vagrant ssh`.  This should log you in using the pre-set SSH keys as the user "vagrant".  You can then switch to your own user.  Be sure to change the password for your created Linux user from the default set in the Vagrantfile.

## Shutting Down

To shut down the local environment and save it, run `vagrant halt`.

## Destroying Environment

To destroy the local environment and delete all files, run `vagrant destroy`.  

## Resources

* [Hashicorp Vagrant Quick Start Guide](https://learn.hashicorp.com/collections/vagrant/getting-started)

* [Vagrant Documentation - Vagrantfile](https://www.vagrantup.com/docs/vagrantfile)
# Virtualization

## Objectives

- Overview of virtualization
- Installation of [Oracle Virtualbox](https://www.virtualbox.org/) hypervisor
- Installation of [Fedora Linux](https://getfedora.org/) as the guest operating system

## What is virtualization

[Virtualization](https://en.wikipedia.org/wiki/Virtualization) is the act of creating a virtual (rather than actual) version of something, including virtual computer hardware platforms, storage devices, and computer network resources.

A piece of software is required to create virtual machines (guest machines) on the physical hardware (host machine).  This piece of software is known as the hypervisor or virtual machine monitor.

A virtualization host is a physical machine which provides guest VM(s) the underlying compute resources, eg:

- Compute
- Memory
- Storage
- Network

A virtual machine monitor (VMM) or hypervisor running on the host machine controls the guest VMs

## Hypervisors

There are 2 types of hypervisor.

- Type 1: Run directly on the host's hardware, eg Linux KVM, VMware ESXi
- Type 2: Run on top of another operating system, eg Oracle Virtualbox, VMware Workstation Player

Modern CPUs support hardware virtualization:
- On Linux systems, you can tell by checking the flags of /proc/cpuinfo. For Intel based CPUs, look for the `vmx` flag.  For AMD based CPUs, look for the `svm` flag.
- On Windows systems, you can check the Tasks Manager -> Performance and you can see confirm from the status "Virtualization: Enabled" as shown in the figure below. ![Virtualization_01.png](assets/Virtualization_01.png)
Alternatively, you may also run the command **systeminfo** in a command prompt which will generate information on the system including virtualization support: ![Virtualization_02.png](assets/Virtualization_02.png)
- If virtualization is not enabled on your system, you will need to enable it in the BIOS before continuing.  

## KVM, libvirt and QEMU

When running virtualization on Linux hosts, KVM, libvirtd and QEMU are the technologies often encountered.  A write up of the above can be found [here](./KVM_libvirt.md).

## Lab Procedures

TLDR: The steps for this lab is similar to this [linuxhint blogpost](https://linuxhint.com/how-to-install-fedora-workstation-35-on-virtualbox/), except that we will generally be using the latest stable version of all software.  

Detailed documentation can be found below, for reference if necesary:

  1. [Download Oracle Virtualbox](https://www.virtualbox.org/) - Choose the appropriate version for your OS

  2. [Download Fedora Linux](https://getfedora.org/en/workstation/download/) - Get the latest stable version available.  Download the ISO image file for use in step (5) later.

  3. [Install Virtualbox](https://www.virtualbox.org/manual/ch01.html#intro-installing) - Follow the user manual to install Oracle Virtualbox

  4. [Start Virtualbox](https://www.virtualbox.org/manual/ch01.html#intro-starting)

  5. [Creating a new Virtual Machine in Virtualbox](https://www.virtualbox.org/manual/ch01.html#create-vm-wizard) - Note the following when creating the VM:

      i. Name: Fedora

      ii. Type: Linux

      iii. Hard Disk: 15 GB, dynamically allocated

      iv. Memory: 2 GB

      vi. ISO Image: This shall be the Fedora Linux ISO file you had downloaded earlier.  

  6. [Start VM](https://www.virtualbox.org/manual/ch01.html#intro-starting-vm-first-time) and [Install Fedora Linux](https://docs.fedoraproject.org/en-US/fedora/f36/install-guide/install/Installing_Using_Anaconda/#sect-installation-graphical-mode)

## Conclusion
In this lab, you have installed a Fedora linux virtual machine on your physical machine.  


## Resources

- [linuxhint: How to Install Fedora Workstation on Virtualbox](https://linuxhint.com/how-to-install-fedora-workstation-35-on-virtualbox/)
- [Wikipedia: Virtualization](https://en.wikipedia.org/wiki/Virtualization)
- [Redhat article: What is virtualization](https://www.redhat.com/en/topics/virtualization)
- [Oracle Virtualbox Documentation](https://www.virtualbox.org/wiki/End-user_documentation)


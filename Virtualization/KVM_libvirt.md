# Kernel-based Virtual Machine (KVM) and libvirt

## KVM Overview

[KVM](https://www.linux-kvm.org/page/Main_Page) (for Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V).

## libvirt Overview

The [libvirt project](https://libvirt.org/) is a toolkit to manage virtualization platforms including KVM.

Common applications:

* virt-manager - Virtual Machine Manager

![virt-manager](./img/KVM_libvirt_01.png)

* virsh - main  interface  for managing virsh guest domains

## QEMU

[QEMU](https://wiki.qemu.org/Main_Page) is a generic and open source machine emulator and virtualizer.

The QEMU emulator is able to simulates various peripherals:

> man qemu

## Tools

Tools to manage KVM on Linux include:

* qemu-*
* virt-*

## Labs

* Demo: virt-manager on KVM

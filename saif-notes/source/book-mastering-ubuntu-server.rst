Mastering Ubuntu server Notes
==============================

Chapter 16: Virtualization
---------------------------
* This concept changed the way we maintain our data centers, allowing us to segregate workloads into many smaller machines being run from a single server.
* Ubuntu has virtualization built right in. This comes in the form of a dynamic duo consisting of Kernel-based VM (KVM) and Quick Emulator (QEMU), which together form a virtualization suite that enables Ubuntu (and Linux in general) to run VMs without the need for a third-party solution.
* The combination of KVM and QEMU make up the virtualization solution that can be enabled on an Ubuntu server to turn it into a host for VMs.
* in order to find out whether your CPU supports virtualization run this commad: ``egrep -c '(vmx|svm)' /proc/cpuinfo`` A result of 1 or more means that your CPU does support virtualization extensions. A result of 0 means it does not.
* Even if your CPU does support virtualization extensions, it's often the case that it's disabled by default with most end-user PCs sold today, and even some servers. To enable these extensions, you may need to enter the BIOS setup screen __ hardware dependant.
* The virtualization extensions of your CPU can only work with one solution at a time, KVM or VirtualBox, for example.
* ``apt install bridge-utils libvirt-clients libvirt-daemon-system qemu-kvm``
* ``virt-manager`` (GUI) through which we can perform administration tasks relating to VMs. The virt-manager utility is especially useful as it allows us to manage both remote and local KVM servers.


Chapter 17: Running Containers
-------------------------------
* Virtualization allows us to run multiple virtual servers on one physical piece of hardware. We allocate CPU, RAM, and disk space to these VMs, and they run as if they were a real server. In fact, for all intents and purposes, a VM is a real server.
* Nowadays, VM solutions do have ways of sharing unused resources, but effectively, resource efficiency is a natural weakness of the platform.
* Containers, unlike VMs, are not actual servers. containers share the CPU with the host, containers share the kernel of the host, and container can't access the host filesystem, (unless you explicitly set it up to do so).
* It's probably best to think of a container as a filesystem rather than a VM. [oversimplification]
* Containarization utilizes the functionality of the Linux kernel to isolate various components of a container from the rest of the system. keeping processes that are running within a container separate from other processes running on the host server is an important benefit.
* Portability is another strength of containerization.
* Docker utilizes a layered approach to containerization. Every change you make to the container creates a new layer, and these layers can form the base of other containers, thus saving disk space. [not very obvious]
* You can think of Docker container as an **application** container that provides the foundation needed to run an application.
* The operating system you're running your container solution on is of little importance nowadays, since most people use a **container service to run containers rather than an actual server** that you manage yourself.
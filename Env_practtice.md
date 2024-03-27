# Env practice

Before learn OS knowledge, we should first know some basic knowledge.

## QEMU

qemu is a virtual machine, just like a VMware. We use this to load `.iso` image, let's start with downloading it.

WSL-ubuntu 22.04:

    # Install qemu
    sudo apt-get install qemu-system-x86
    # config virtual disk
    qemu-img create -f qcow2 /home/aker/tmp/qemu_fs/virtual_disk.qcow2 20G
    # download mini ubuntu image
    curl -o mini.iso http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-amd64/current/images/netboot/mini.iso
    # start load mini.iso, -hda means set virtual disk, -cdrom means /path/to/iso file
    qemu-system-x86_64 -boot d -hda /home/aker/tmp/qemu_fs/virtual_disk.qcow2 -cdrom /mnt/c/Users/shaohong.jiang/Downloads/mini.iso -m 2048

Above will create virtual dist in /home/aker/tmp/qemu_fs/virtual_disk.qcow2 with 20G disk, this disk is virtual. When booting the system, use -hda point to the virtual disk, when step arrive to `Partition disks`, you can choose a virtual disk listing as `SCSI1 (0,0,0) sda`. Which means selecting this virtual disk, it won't affect you physical machine, don't warry.

To free disk space, you can delete it as `rm /path/to/virtual_disk.qcow2`.


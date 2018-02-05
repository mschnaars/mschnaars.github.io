---
title: Installing Avalon Using a Virtual Machine Image
summary: "Instructions to walk through the process of downloading, booting, and configuring a CentOS 7.x virtual machine image containing Docker containers of Avalon, Fedora, Red5, and Opencast Matterhorn, with additional instructions on loaded sample audio and video content."
sidebar: avalon6_sidebar
permalink: avalon6_installing_avalon_using_a_virtual_machine_image.html
folder: avalon6
---

## Getting a Virtualization Product

The Avalon VM is distributed as an Open Virtualization Appliance which should be compatible with these Virtual machine products:

* [VirtualBox](http://virtualbox.org/) (Free; Avalon VM is developed on VirtualBox)
* [Red Hat Virtualization](https://www.redhat.com/en/technologies/virtualization/enterprise-virtualization#Try) (Commercial; part of the RH system)
* [VMWare](http://www.vmware.com/) (Some versions are free, others are not)

Other virtualization products may be used, but they will require manually converting the OVA file into something useful.

## Getting the Avalon Virtual Machine Image

The Avalon VM file is located at [http://www.avalonmediasystem.org/downloads/avalon-vm.ov](http://www.avalonmediasystem.org/downloads/avalon-vm.ova) and is roughly 2GB.  Due to the size, it may take some time to download.

## Importing the Avalon VM Image

{{site.data.alerts.note}}
The OVA file current contains release 6.3.1. This will be updated to the newly released version 6.3.2 in the immediate future.
{{site.data.alerts.end}}

Each virtualization product has different methods for using a VM appliance.  The tested methods are below.  If you use a product which is not listed, please contact us with usage instructions and we will add them here.

__VirtualBox__

* Start the VirtualBox Manager
* Select the "File/Import Appliance..." menu item
    * Press the "Open Appliance..." button and select the Avalon VM image you downloaded
    * Press "Continue"
    * Below the list of VM appliance settings, check the box next to "Reinitialize the MAC address of all network cards"
    * Press "Import"
* The VM should now be visible in the list.
    * Select the Avalon VM 
    * Press the "Settings" icon
        * Select the "Network" tab
        * Make sure the "Attached to" field is set to "NAT"
        * Press "OK"
    * Press "Start" icon to boot the VM
* VirtualBox has networking quirks that require special configuration to make Avalon work in NAT mode. Please see [VirtualBox Networking](https://wiki.dlib.indiana.edu/display/VarVideo/VirtualBox+Networking) for details.

{{site.data.alerts.important}}
Users on Apple hardware may get the following error screen when starting the VM:
{% include image.html file="doc_images/vbox_mac_error.png" alt="error screen" %}
If you receive this dialog, click the <i>Change Network Settings</i> button followed by <i>OK</i> in the following dialog to resolve the issue.
{{site.data.alerts.end}}

__VMware Player__

* Click on "Open a Virtual Machine"
    * Select the .ova file you downloaded
    * Press "Import"
    * Press "Retry" to relax specification (if needed)
* Click on "Edit virtual machine settings"
    * Click on "Network Adapter"
        * Make sure it is set to NAT
        * Press "Advanced..."
            * Press "Generate" to create a new MAC address and press "Close"
        * Press "Save"
* Press "Play virtual machine"

__Libvirt's Virtual Machine Manager__

[Virtual Machine Manager](http://virt-manager.org/) is an open-source GUI front end to QEMU, KVM and other Linux-based virtualization products.  It comes with Fedora Linux and other distributions.  It doesn't directly support OVA files so manual conversion is required.

* Unpack the OVA file. `$DIST` is where the VM files are going to be; `$DOWNLOAD` is where the OVA file was downloaded.

      mkdir $DIST
      cd $DIST
      tar xvf $DOWNLOAD/avalon-vm.ova

  The vmdk file is the virtual disk image. The other files are settings for the VM (ovf) and checksum files (mf).
* Normally one would use `virt-convert` to convert `.ovf` to the right format, but it is bugged, so it has to be done by hand.
    * By Hand method
        * Convert disk image to qcow2

              qemu-img convert -f vmdk -O qcow2 *.vmdk avalon-vm.qcow2

          The vmdk file shipped is compressed, so the new qcow2 file will be roughly twice as large. After the conversion, the vmdk file is no longer needed and can be deleted.
        * Create a new VM
            * Click on the "Create a new virtual machine" icon
            * Enter the name for the virtual machine, select "Import existing disk image" and press "Forward"
            * Select the disk image by pressing "Browse"
                * Press "Browse Local"
                * Navigate to `$DIST`
                * Select the `avalon-vm.qcow2` file
            * Select the OS type "Linux", Version "Red Hat Enterprise Linux 7" and press "Forward"
            * Set the RAM to 3072 (3G) and press "Forward"
            * Select "Customize configuration before install" and press "Finish"
            * In the Configuration Window make these changes:
                * In "NIC" set the source device to the macvtap enabled interface which represents the ethernet device of the host (usually eth0 or em1)
                * Remove the DISK 1 Device and re-add it:
                    * Press "Add Hardware"
                    * Select the "Storage" tab
                    * Select "Select managed or other existing storage" and Browse
                    * Press "Browse Local"
                        * Navigate to `$DIST` and select the `avalon-vm.qcow2` file
                    * Set the device type to "Virtio disk"
                    * Set the cache mode to "default"
                    * Set the storage format to "qcow2"
            * Press Finish
        * Press "Begin Installation"

__Generic VM Product__

A generic VM product may be set up using these settings:

* Unpack the .ova file – it is just a tarball containing a .vmdk file and a configuration file
* Use these settings for the VM:
    * 64-bit guest
    * At least 2G of RAM (the shipped settings use 3G)
    * At least 1 core
    * Graphical Display
    * System disk the the .vmdk from the .ova package
    * The network interface must be bridged and have a unique MAC address
* Start the VM as appropriate for this VM software

__Notes for ALL Virtualization Products__

The disk image in the OVA package is dynamically-allocated with a maximum size of 500G.  While the disk image may only use a few gigabytes when it is first used, it will grow as more data is placed into the VM.  Most VMs behave unpredictably when the host system doesn't have enough disk space to satisfy guest OS requests.  Monitor the disk usage closely.

## Using the Avalon VM

Once the VM has rebooted and the login screen has appeared, the Avalon system is ready to use. 

1. Login using username root, password vagrant. You should change this password immediately.
2. Open the built-in Firefox browser and point it to `http://localhost`.
3. Click on Login
4. Click on Register new identity
5. Sign up using the default archivist1@example.com email to get admin access

After you have signed in, Avalon VM can be used like any other Avalon installation.

## Installing Sample Content (Optional)

The sample content can be ingested through a batch ingest process:

* Create a new collection, for example, DEMO

      wget http://www.avalonmediasystem.org/downloads/DemoFixturesBatch.tar.gz
      tar zxvf DemoFixturesBatch.tar.gz
      mv ExampleBatchIngest/* /root/avalon-docker/masterfiles/dropbox/DEMO/

As the samples are ingested, you will see new items being added to the collection. Be patient as the media transcoding may take a while.

## Building Your Own OVA File

If you want to build your own OVA file follow the instructions on https://github.com/avalonmediasystem/avalon-packer

---

## Troubleshooting the Avalon VM

Because the OVA uses Docker and Docker-Compose, you can find instructions on how to navigate the stack on the [avalon-docker github page](https://github.com/avalonmediasystem/avalon-docker/tree/red5).

### Reconfiguring the Avalon VM

__Resetting the root password__

* When the VM starts, there is a 3-second countdown before the boot begins. Press the spacebar during this countdown to get the boot menu.
* Edit the boot entry and boot
    * Press the 'e' key to edit the first boot entry
    * Use the down arrow to highlight the line beginning with 'kernel' and press 'e'
    * Add `init=/bin/bash` to the line, making sure there is leading space separating it from the the end of the existing command line
    * Press 'enter' to go back to the root/kernel/initd selection screen
    * Press 'b' to boot
* The system will boot to a root shell
* Change the password

      mount -o remount,rw /
      passwd root
      mount -o remount,ro /

A hard reboot of the VM is required to restart the system.

{% include links.html %}

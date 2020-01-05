## Setting up **virt-manager** in Fedora Workstation

### To begin with, firstly we need to install the required packages


As we are using Fedora Workstation all the virtualisation need are already fulfilled in the Fedora Repositories, all we need to do is fetch those packages and install them, use the following command:

```bash
$ sudo dnf install @virtualisation
``` 

The installation size is around 3-4 MB so it wouldn't take you much long to get stuff done. Without any further waiting, up next we will configure the **libvirtd** configuration file

### Editing the **libvirtd** configuration and setting the domain socket group ownership

Use the following command to open the **libvirtd.conf** file in Vim, yeah I know everyone hates Vim but I'll make that easy for you! 

```bash
$ sudo vi /etc/libvirt/libvirtd.conf
```
In Vim, by default we are in the view mde which means you cannot edit the text in the file until you press the **I** key, so make sure to stay away from it for a while, scroll all the way to the middle of the file until you find a **commented line** that says:

*#unix_sock_group = "libvirt"*

Press the **I** key and enter in *Edit Mode*, uncomment the line by removing the **#** from the line, next we will use the cursor keys again to look for the line:

*#unix_sock_rw_perms = "0770"*

Follow the same steps, uncomment the line by removing the **#** symbol and the save the file by pressing 

**Esc** key, then press **:** and write **wq** and hit **Enter** 

which means that Vim will save the changes and quit the file.

### Starting the **libvirtd** service

To start the *libvirtd* service, firstly we'll enable it, use the following command to enable the service:

```bash
$ sudo systemctl start libvirtd
```

Then start the service by using the command:

```bash
$ sudo systemctl enable libvirtd
```

In case you are lazy and don't want to enter your administrator password everytime you start **virtual-manager**, use the following command or you can skip this step:

```bash
$ sudo usermod -a -G libvirt $(whoami)
```

## Thanks! Find me here(https://twitter.com/0xskr1p7)





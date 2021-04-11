```
Roberto Nogueira  
BSd EE, MSd CE
Solution Integrator Experienced - Certified by Ericsson
```
# Project Name

![project image](images/project.png)

**About**
**[WSL: Operational Systems as Apps](https://enogrob.medium.com/wsl-linux-operating-systems-as-apps-b4a490690a9f)**

Why split up if you can have it together, instead of having a computer with "Multiple Boot" or even [Virtual Machines](https://en.wikipedia.org/wiki/Virtual_machine) in order to be able to operate Operating Systems together, there is a Microsoft answer to this and it is [WSL](https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux) (Windows Subsystem for Linux). 

This is achieved by making the distributions in reality apps and that after being installed has the same privilege as an app, having at your disposal the computer resources, performance and GUI, and which are available in the [Microsoft Store](https://en.wikipedia.org/wiki/Microsoft_Store), together with the terminal called of [Windows Terminal Preview](https://en.wikipedia.org/wiki/Windows_Terminal).

The laptop provided by Eicon, comes with WSL1, and supports WSL2, although it is a feature flag that has to be activated and then updated to WSL2, which can be downloaded. Development applications such as [VsCode](https://code.visualstudio.com/) and [Rubymine](https://www.jetbrains.com/ruby/) already support WSL2 and I recently updated the [Obras DevTools](https://github.com/enogrob/research-obras-devtools) Works as well. For more information see research:

* [Configuring Laptop with Windows Subsystem Linux - WSL-2](https://trello.com/c/5QSr6Os3/2336-configuring-laptop-with-windows-subsystem-linux-wsl-2)

![](https://trello-attachments.s3.amazonaws.com/5e73d80ec3e291163d4cc462/60642cb859826131a6f908fd/06ceabdf4ae691b11647491c57613bb0/File_000.jpeg)

![](https://trello-attachments.s3.amazonaws.com/5e73d80ec3e291163d4cc462/60642cb859826131a6f908fd/0eb72599d114dac88e40ff413f688225/screenshot_597.png)

**Activities:**

* Folows the instructions **Ref.1** in order to Activate WSL and Upgrade it to version **2**. Afterwards, download and install the target distro and Windows Terminal Preview from the MS Store.
* The management of WSL is performed in the Windows Shell, so see **Ref.2** when this is required.
* See examples in **Ref.3** to **Ref.5** in order to install the desired Linux Desktop and get GUI working.

---

Configuring  **Kali Linux** to remote `GUI`  connection (See **Ref.5**).

```
$ sudo apt update && sudo apt upgrade -y
$ sudo apt install kali-desktop-xfce -y
$ sudo apt install xrdp -y
$ sudo apt install dbus-x11
$ sudo service xrdp start
$ sudo service dbus start

$ ip addr
```

If you want to install `mysql 5.7` in Kali-Linux:

```
sudo apt-get remove --purge mysql-server mysql-client mysql-common -y
sudo rm -rf /etc/mysql
sudo apt-get update --fix-missing
cd ~Downloads
sudo apt list | grep mysql-server
wget https://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-server_5.7.28-1ubuntu19.04_amd64.deb-bundle.tar
tar -xvf mysql-server_5.7.28-1ubuntu19.04_amd64.deb-bundle.tar
sudo apt-get install libaio1
sudo dpkg-preconfigure mysql-community-server_*.deb
sudo dpkg -i mysql-{common,community-client,client,community-server,server}_*.deb
sudo apt-get update --fix-missing
sudo apt-get -f install
sudo service mysql status
sudo service mysql start
```

---

Configuring  **Ubuntu 18.04** to remote `GUI`  connection (See **Ref.4**)

```
$ sudo apt update && sudo apt upgrade -y
$ sudo apt install xfce4 xfce4-goodies -y

$sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak
$sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini
$sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini
$sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini
$ echo xfce4-session > ~/.xsession#enable dbus
$ sudo systemctl enable dbus
```

Add `startxfce4` and comment the last two lines.

```
$ sudo vim /etc/xrdp/startwm.sh
```

Start the folowing services:

```
$ sudo service xrdp start
$ sudo service dbus start
```


---

**Refs:**

* ** 1.** [Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
* **2.** [How to Uninstall or Reinstall Windows 10 Ubuntu Bash Shell](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/)
* **3.** [Run ubuntu-desktop on WSL Ubuntu 18.04 LTS](https://askubuntu.com/questions/1162808/run-ubuntu-desktop-on-wsl-ubuntu-18-04-lts)
* **4.** [Install GUI Desktop in WSL2 Ubuntu 20.04 LTS in Windows 10](https://harshityadav95.medium.com/install-gui-desktop-in-wsl2-ubuntu-20-04-lts-in-windows-10-ae0d8d9e4459)
* **5.** [Kali Linux on Windows in 5min (WSL 2 GUI](https://www.youtube.com/watch?v=AfVH54edAHU)
* **6.** [Research Repository in GitHub](https://github.com/enogrob/research-configuring-laptop-with-windows-subsystem-linux-wsl-2)


```
Roberto Nogueira  
BSd EE, MSd CE
Solution Integrator Experienced - Certified by Ericsson
```
# Project Name

![project image](images/project.png)

**About**

The Windows Subsystem for Linux(WSL), introduced in the Anniversary Update, became a stable feature in the Fall Creators Update. You can now run Ubuntu Kali and openSUSE on Windows, with Fedora and more Linux distributions coming soon.

![](https://trello-attachments.s3.amazonaws.com/5e73d80ec3e291163d4cc462/60642cb859826131a6f908fd/3ec47e0321169049ffb76332bad56541/File_000.jpeg)

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
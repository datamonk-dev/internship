# Dual Boot Ubuntu 24.04.2 LTS with Windows 10/11


> **Before You Start:**
>
> * Backup all your important data.
> * Ensure your device has at least 50GB free space.
> * Make sure BitLocker is **disabled**.
> * Disable RAID in BIOS (use AHCI instead).

---

 >#### What is BitLocker and Why Disable It?
 >**BitLocker** is a full disk encryption feature provided by Microsoft Windows. It encrypts your entire hard drive, protecting your data from unauthorized access, especially if your device is lost or stolen.
 >
 >You must disable BitLocker **before** starting the dual-boot process because a Linux installer cannot resize an encrypted Windows partition. If you try to install Ubuntu with BitLocker enabled, the Ubuntu installer won't be able to "see" or interact with your Windows drive, preventing you from selecting the "Install Ubuntu alongside Windows" option or shrinking the Windows partition. It can also lead to boot failures or data corruption if not handled properly.



## Step 1: Download Ubuntu ISO

* [Ubuntu Download Link](https://ubuntu.com/download/desktop)
* [Rufus Download link](https://rufus.ie/en/)

## Step 2: Create a Bootable USB (Using Rufus)

### What You Need:

* USB drive (at least 8GB)
* [Rufus](https://rufus.ie) utility (Download)

>#### Why is Rufus needed? What does it do?
>
>**Rufus** is a free and open-source utility that helps format and create bootable USB flash drives.
>
>It is needed because operating system installation files (like the Ubuntu ISO) are not simply copied to a USB drive. For a computer's BIOS/UEFI to recognize the USB as a source from which to start an operating system, the USB drive needs to be formatted in a specific way and have the ISO image "burned" to it in a bootable format. 
>
>**What Rufus does:**
>* **Formats the USB drive:** It prepares the USB drive with the correct file system (e.g., FAT32) and partition scheme (e.g., GPT) required for booting.
>* **Writes the ISO image:** It extracts the contents of the Ubuntu ISO file and writes them to the USB drive sector by sector in a way that makes the USB bootable.
>* **Handles bootloader installation:** It correctly places the necessary bootloader files on the USB drive so that your computer knows how to start the Ubuntu installer. 


### Instructions:

1. Plug in your USB drive.
2. Download and open **Rufus**.
3. In Rufus:

   * **Device**: Select your USB drive.
   * **Boot selection**: Click and select the Ubuntu ISO.
   * **Partition scheme**: `GPT`
   * **Target system**: `UEFI (non-CSM)`
   * **File system**: `FAT32`
4. Click **Start**.
5. When prompted, choose **Write in ISO Image mode (Recommended)**.
6. Wait for it to finish. Eject USB when done.

## Step 3: Prepare Your System

### 1. Disable BitLocker:

* Go to **Control Panel > System and Security > BitLocker Drive Encryption**.
* Click **Turn off BitLocker** and let decryption complete.

### 2. Shrink Windows Partition:

* Press `Windows + X` > **Disk Management**.
* Right-click your main partition (usually C:) > **Shrink Volume**.
* Enter amount to shrink (at least 50,000 MB for 50GB) > **Shrink**.

### 3. Disable Fast Startup:

* Go to **Control Panel > Power Options > Choose what the power button does**.
* Click **Change settings that are currently unavailable**.
* Uncheck **Turn on fast startup** > Save changes.

### 4. Disable Secure Boot (Optional, depends on laptop):

* Reboot and enter BIOS/UEFI (usually `F2`, `DEL`, or `ESC` at startup).
* Go to **Boot** tab.
* Set **Secure Boot** to **Disabled**.
* Set SATA Mode to **AHCI** if RAID is enabled.
* Save and Exit.

> #### What are BIOS/UEFI, RAID, and AHCI?
>
>Your computer's **BIOS (Basic Input/Output System)** or its modern successor **UEFI (Unified Extensible Firmware Interface)** is firmware embedded on your motherboard. It's the first software that runs when you turn on your computer, responsible for initializing hardware components (like your CPU, RAM, and hard drives) and then loading the operating system. 
>
>**RAID (Redundant Array of Independent Disks)** is a technology that combines multiple physical disk drives into one or more logical units for data redundancy, performance improvement, or both.  Many modern laptops with NVMe SSDs might have their SATA controller configured in RAID mode by default, even if only one drive is present.
>
>**AHCI (Advanced Host Controller Interface)** is a technical standard that defines an operation mode for SATA host controllers.  It's the standard mode for managing individual SATA drives, allowing the operating system to utilize advanced features like Native Command Queuing (NCQ).
>
>**Why disable RAID and use AHCI?**
Linux distributions often do not recognize disk drives configured in RAID mode by default, especially software RAID setups done at the BIOS/UEFI level. This can prevent the Ubuntu installer from detecting your existing Windows installation or even seeing your hard drive at all. Switching the SATA controller mode to **AHCI** ensures that your drives are presented to the operating system (both Windows and Linux) as individual, accessible devices, which is the standard and most compatible mode for Linux installations. 


## Step 4: Boot from USB

1. Insert bootable USB.
2. Reboot and enter boot menu (usually `F12`, `ESC`, or `F10`).
3. Select your USB device.
4. Choose **Try or Install Ubuntu**.

## Step 5: Install Ubuntu

1. On the desktop, click **Install Ubuntu**.
2. Choose Language > Continue.
3. **Keyboard layout** > Continue.
4. Choose **Normal installation** + check both download and install options > Continue.
5. On "Installation Type":

   * Select **Install Ubuntu alongside Windows Boot Manager**.
   * If not shown, choose **Something else**:

     * Select the free space you created earlier.
     * Click `+` to create:

       * **Root (/)**: ext4, 40GB or more
       * **Swap** (optional): size = RAM if needed
   * DO NOT format the Windows partition.
6. Confirm partitions and proceed.
7. Select your timezone > Continue.
8. Enter your name, computer name, username, password.
9. Click **Continue** and installation begins.

After installation:

* Click **Restart Now**.
* Remove the USB when prompted.

## Step 6: Boot Options

Upon restart, you’ll see **GRUB menu**:

* Select **Ubuntu** to use Linux.
* Select **Windows Boot Manager** to return to Windows.

## Common Issues & Fixes

### Issue: Ubuntu doesn’t detect Windows

* Ensure Windows was installed in **UEFI mode**.
* Ensure Ubuntu USB was created with **GPT partition scheme**.
* Use **Boot Repair** from Ubuntu live session.

### Issue: BitLocker prevents booting Ubuntu

* Always disable BitLocker **before** partitioning.
* If encrypted drives are present, Windows bootloader may fail.

### Issue: No bootable device found

* Re-check BIOS: USB boot enabled, Secure Boot disabled, SATA set to AHCI.

### Issue: Black screen after boot

* Try booting with `nomodeset`:

  * At GRUB menu, press `e`.
  * Replace `quiet splash` with `nomodeset`.
  * Press `F10` to boot.

### Issue: Wi-Fi or drivers not working

* Connect via Ethernet or USB tether.
* Run:

  ```bash
  sudo apt update && sudo apt upgrade
  sudo ubuntu-drivers autoinstall
  ```

---
### Documentation
* [Official Documentation](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)
### Videos
* [How to Dual Boot Ubuntu 24.04 LTS and Windows 10 / 11](https://youtu.be/qq-7X8zLP7g)
* [How to Install Ubuntu 24.04 Latest Version on Windows 10 [Dual Boot Ubuntu & Windows 10]](https://youtu.be/m9G_koazXvE)
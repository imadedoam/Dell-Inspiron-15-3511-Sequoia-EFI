### Dell Inspiron 15 3511 Sequoia EFI (Working) 


- Status: Working (⚠WARNING: NO SMBIOS, SERIAL NUMBER, SLM, UUID, ROM. ADD IT YOURSELF) (macOS is receiving a full 1536MB VRAM)
- macOS Version: Sequoia
- Bootloader: OpenCore

## HARDWARE 

| Component | Specification | Notes |
| :--- | :--- | :--- |
| **Laptop Model** | Dell Inspiron 15 3511 | I don't use the stock RLT8821CE, i use Intel 8625NGW |
| **Board Number** | Unknown | just know that my board does not have a USB-C/Thunderbolt Port, and i have a SATA port |
| **CPU** | Intel Core i3-1115G4 | |
| **iGPU** | Intel UHD Graphics (`9A78`) | 1536MB VRAM (Metal Working) |
| **RAM** | 16GB DDR4 | Doesn't need to match |
| **Boot SSD** | KDATA 2.5" SATA SSD | Slow, not recommended |
| **BIOS Revision** | 1.48.0 | CFG Lock: Disabled |
| **Wi-Fi Card** | Intel 8625NGW | |

### Features

| Feature | Status | Notes |
| :--- | :--- | :--- |
| **Metal Graphics** | Working | 1536MB VRAM |
| **Internal Display** | Working | |
| **HDMI** | Working | idk about DP and USB-C, it is worth checking through b00t0x's offical Repository |
| **Audio** | Working | sounds good |
| **Internal Keyboard** | Working | unless your keyboard has dead keys |
| **Touchpad** | Working | smooth |
| **Wi-Fi** | Working | Yours might have a slower speed |
| **Touchpad Gestures** | Needs Testing | Not fully tested |
| **Sleep & Wake** | Needs Testing | Working (?) |
| **Bluetooth** | Not Working | Unless you install IntelBluetoothFirmware.kext . This card uses Bluetooth 4.2 so you shouldnt expect Handoff, Airdrop,.. to work fine |


- Feature support may change as development continues.

### Installation:
## RECOVERY METHOD (FOR A MORE DETAILED INSTALLATION GUIDE: GO TO https://dortania.github.io/OpenCore-Install-Guide/)
- Step 1: Download the EFI (GO TO RELEASES, NOT FROM CODE)
- Step 2: Download macOS Recovery using OpenCore Package or gibmacrecovery (if you use Offline Install, please skip to OFFLINE INSTALL)
- Step 3: format your USB in FAT32 using the Rufus method (Download Rufus, open Rufus, select your USB, choose format as FAT32/exFAT. make sure it is GPT)
- Step 4: drag your downloaded com.apple.recovery.boot into your USB
- Step 5: Extract the .zip (if you haven't), take the folder named EFI, drag it to your USB
- Step 6: CRUCIAL - .plist doesnt contain a working SMBIOS, you will need one. Download OCAT (OpenCore Auxiliary Tools) by ic005k. import your .plist by dragging your EFI inside. Then go to PI (the screen with Apple Logo). Choose MacbookAir9,1 o MacBookPro16,2. Click Generate.
- Step 7: SAVE IT
- Step 8: Restart your computer
- Step 9: Enter BIOS through spamming F2 when the DELL logo appears
- Step 10: go to Security/Boot (I DONT KNOW WHAT ITS CALLED I FORGOT), scroll down until you see Secure Boot and turn it off.
- Step 11: after Saving and qutting BIOS, spam F12 to enter One-Time Boot Menu. then select your USB
- Step 12: if you see the OpenCore Boot Menu. Dont panic if you only see your USB. click Space. it will show all boot entries. then Select RUFUS (dmg)
- Step 13: Wait for the Verbose text to roll (if you dont see one and it feel stuck, wait 2-3 minutes before turning your computer off and on). if you see the Apple Logo with a cursor at the corner of the screen. You're in Recovery!
- Step 14: Open Disk Utitlity. Click Show --> Show All Devices
- Step 15: Select your SSD/HDD (on the top), Click Erease around top right corner. name your drive and select Format as APFS. Click Apply.
- Step 16: Quit Disk Utility after it finishes by clicking Windows + Q
- Step 17: When you're back at the recovery menu, click the Wifi icon and connect to your network.
- Step 18: Click Reinstall macOS Sequoia. Continue, wait for install formation to load, then click Continue/Agree then select your SSD/HDD, and click Continue.
- Step 19: wait for it to finish
- Step 20: it'll reboot to OCBP (OpenCore Boot Picker), you will see a boot entry named macOS Installer, click it. and wait for it to run and return to OCBP
- Step 21: if you see macOS Installer again, dont panic, just run it again. When it finishes, you should see your startup disk name there, click it, wait until macOS UI shows up. Proceed through the Setup. when you reacht the desktop. see Step 22
- Step 22: download and run the latest WhateverXe-Package.pkg from b00t0x's Repo
- Step 23: if macOS blocks it (i know it will), go to System Preferences (aka Settings app, the gear icon on the task bar, scroll and choose Privacy & Security, scroll down and Allow the app to work, go through the installer and restart your marchine when prompted (allow it to make changes to your computer in System Preferences, it should tell you to restart and so does the installer, just click whatever is not grayed out and turn off Installer to restart.
- Step 24: you should be set

## Offline Method:
## OFFLINE INSTALL (RECOMMENDED IF YOUR WI-FI IS SLOW OR DOESN'T WORK IN RECOVERY)
- Step 1: Download the EFI (**GO TO RELEASES, NOT FROM CODE**) and extract the `.zip` so you have the `EFI` folder ready.
- Step 2: Download **JDownloader 2** (dont use Chrome/Edge built-in downloader, it will fail on a ~15GB file). Copy the Buzzheavier (`bzzrt`) `.raw` installer link into JDownloader 2 and let it finish downloading.
- Step 3: Flash the `.raw` file onto a **16GB+ USB** using **BalenaEtcher** or **Rufus**.
- Step 4: After flashing finishes, open **OCAT (OpenCore Auxiliary Tools)** by `ic005k`, mount your USB's `EFI` partition (or replace the USB's `EFI` folder with the one you downloaded in Step 1).
- Step 5: **CRUCIAL** - Open `EFI/OC/config.plist` in OCAT, go to **PI** (the screen with the Apple logo), choose **`MacBookAir9,1`** or **`MacBookPro16,2`**, and click **Generate**.
- Step 6: **SAVE IT** (`Ctrl + S`) and safely eject your USB.
- Step 7: Restart your computer, spam **`F2`** at the DELL logo to enter BIOS, turn **OFF** **Secure Boot** (and make sure **SATA/NVMe Operation** is set to **AHCI**), then save and exit.
- Step 8: Spam **`F12`** to open the One-Time Boot Menu and select your USB.
- Step 9: In the OpenCore Boot Menu, select **`Install macOS Sequoia`** (press **`Spacebar`** first if you don't see it).
- Step 10: Wait for the verbose text to roll into macOS Recovery. Open **Disk Utility**, click **View -> Show All Devices**, select your top-level SSD/HDD, click **Erase**, name it, set Format to **APFS** (and Scheme to **GUID Partition Map**), and click **Erase**.
- Step 11: Quit Disk Utility (**`Win + Q`**), click **Install macOS Sequoia**, agree to the terms, select your drive, and click **Continue** (no internet needed!).
- Step 12: Follow **Steps 19 to 24** from the **RECOVERY METHOD** above to finish booting, run **`WhateverXe-Package.pkg`**, and copy your USB's `EFI` folder to your internal SSD's EFI partition so you can boot without the USB.
(yes, this part is AI generated, im too tired to rewrite it, if there are any mistake, feel free to reach out to me at imanewbie319@gmail.com)

Wish you have a sucessful hackintosh install progress

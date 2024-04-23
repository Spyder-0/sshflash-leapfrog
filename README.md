# sshflash
Software to flash (custom) leapfrog device firmware over SSH.

**Note:** This fork combines both the sshflash program and images for the custom Linux distro that includes a couple of emulators and a Retroarch installation. Additionally, I've simplified the instructions for anyone who might want to try this project. **These instructions only work for Linux** (Debian/Ubuntu based distros). Credits go to the creator: [mac2612](https://github.com/mac2612).

![LeapSonic](https://github.com/Spyder-0/sshflash-leapfrog/assets/85440857/959a9aef-78f0-480c-aff6-a5f630e26980)

# Installation
- Make sure your Leapfrog is connected to your computer via cable and is in recovery mode (Script will let you know how to enter recovery mode). Usually to enter recovery mode you should turn off the Leapfrog, then hold the **Shoulder Buttons (L + R)** and the **Hint Button (?)**, then press the **ON Button**. You should be greeted by a green screen with a picture of a Leapfrog connected to a computer. This key combination could vary with each model, so refer to the script.
- Install required dependencies: `sudo apt install sg3-utils python3 git` (If you get any Python errors, try installing python2 instead).
- Clone this repository: `git clone https://github.com/Spyder-0/sshflash-leapfrog.git`.
- Change directory to the cloned repo: `cd sshflash-leapfrog`.
- Run the script: `./remote_flash.sh`. If you get any access errors, run `chmod +x remote_flash.sh`.
- Follow the instructions provided by the script and make sure to select the correct Leapfrog device.
- After the firmware is flashed, your Leapfrog should automatically reboot.

# Organising ROMs
- Make sure your Leapfrog is still connected to your PC via cable. It should be detected as a wired internet connection adapter.
- Use this command to make a new directory for the console you want to organise ROMs for: `ssh -i ~/sshflash-leapfrog/keys/id_rsa root@169.254.6.1 'mkdir /roms/<PLATFORM>'`.
- For example, if I want to make a folder for Sega Genesis ROMs, I would use the command: `ssh -i ~/sshflash-leapfrog/keys/id_rsa root@169.254.6.1 'mkdir /roms/Genesis'`.
- Additionally, you can just SSH into the Leapfrog filesystem and modify it as you like: `ssh -i ~/sshflash-leapfrog/keys/id_rsa root@169.254.6.1`.

# Adding ROMs
- Make sure your Leapfrog is still connected to your PC via cable. It should be detected as a wired internet connection adapter.
- To transfer ROMs to the Leapfrog, use the command: `scp -i ~/sshflash/keys/id_rsa '<ROM_LOCATION>' root@169.254.6.1:/roms/PLATFORM`.
- For example: `scp -i ~/sshflash/keys/id_rsa '~/ROMs/Genesis/Sonic The Hedgehog 2 (World) (Rev A).md' root@169.254.6.1:/roms/Genesis`.

# Credits
Huge thanks to [mac2612](https://github.com/mac2612) for making this project in the first place.
- Original Repository: https://github.com/mac2612/sshflash
- Retroleap (Firmware): https://github.com/mac2612/retroleap

# Additional Help/Recources
- Video Help: https://youtu.be/xBuSWCzDB1M
- Windows Version: https://github.com/andymcca/sshflash-win
- Extra RetroArch Cores: https://github.com/andymcca/retroleap/releases/tag/retroarch-v1.13.0-for-retroleap

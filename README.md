# ultrakill-plymouth
A Plymouth (boot) theme of Ultrakill's game launching sequence.
The animation frames are provided at 1920×1080 and automatically scaled to fit the display while preserving their original aspect ratio.
  
https://github.com/user-attachments/assets/c499c7df-4d3c-4a0f-a010-524798b43ded  

# Status
Currently the only distro logos available are Linux Mint's and Arch. I may or may not add more.
If you want to add your own, just replace frame-149.png to frame-194.png. 


# Installation

It really depends on your distro's way of updating plymouth theme, here is how to do it on Linux Mint :
## Linux Mint
```bash
git clone https://github.com/Hash-AK/ultrakill-plymouth
cd ultrakill-plymouth/LinuxMint/
sudo cp -r ./ /usr/share/plymouth/themes/ultrakill-plymouth-linux-mint
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth ultrakill-plymouth-linux-mint.plymouth 80
sudo update-alternatives --config default.plymouth # choose the correct number for the theme in the menu
sudo update-initramfs -u
```
Moreover, you may need to delay your boot if you want to see the full animation. The only way I found yet on Linux mint was to delay lightdm.service with this : 
```bash
sudo systemctl edit lightdm.service
# under [Service], add ExecStartPre=/usr/bin/sleep 6.5 (change the number until the boot is more or less correct)
sudo systemctl daemon-reload
sudo systemctl restart lightdm.service
reboot
```
## Arch
```bash
git clone https://github.com/Hash-AK/ultrakill-plymouth
cd ultrakill-plymouth/Arch/
sudo cp -r ./ /usr/share/plymouth/themes/ultrakill-plymouth-arch/
sudo plymouth-set-default-theme ultrakill-plymouth-arch -R
```
As for Mint, you may need to delay the boot, this time editing plymouth's own service :
```bash
sudo systemctl edit plymouth-quit.service
# Under [Service], add
ExecStartPre=/usr/bin/sleep 13 # adjust the time accordingly
```
Then reload the service:
```sudo systemctl daemon-reload```


# Credits
- **ULTRAKILL by [New Blood Interactive](https://newblood.games), developed by Arsi "Hakita" Patala**  
  Original game that inspired this Plymouth theme.

- **Neon Icons by [peteyyz/refind-neon](https://github.com/peteyyz/refind-neon)**  
  Neon icons adapted and modified from the rEFInd neon theme. Original project by peteyyz.

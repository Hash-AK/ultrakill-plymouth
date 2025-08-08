# ultrakill-plymouth
A Plymouth theme of Ultrakill's game launching sequence ( _note, for the GRUB menu theme, go to [this project](https://github.com/YouStones/ultrakill-grub-theme)_ ) :  

![LMDemo](https://github.com/user-attachments/assets/3dd3f0b9-c6e0-4569-91f4-ec1f729d2d3b)  

(_Please also note that this was ran in a VM with a subobtimal resolution, not the 1920x1080 version that I give here, so the screen isn't filled correctly_)  

# Installation

It really depends on your distro's way of updating plymouth theme, here is how to do it on Linux Mint :
```bash
git clone https://github.com/Hash-AK/ultrakill-plymouth
cd ultrakill-plymouth/LinuxMint/
sudo cp -r ./HD/ /usr/share/plymouth/themes/ultrakill-plymouth
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth ultrakill-plymouth.plymouth 80
sudo update-alternatives --config default.plymouth # choose the corret number for the theme in the menu
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


# Credits
- **ULTRAKILL by [New Blood Interactive](https://newblood.games), developed by Arsi "Hakita" Patala**  
  Original game that inspired this Plymouth theme.

- **ULTRAKILL GRUB Theme by [YouStones](https://github.com/YouStones/ultrakill-grub-theme)**  
  Awesome GRUB theme, seen in the first second of my recording

- **Neon Icons by [peteyyz/refind-neon](https://github.com/peteyyz/refind-neon)**  
  Neon icons adapted and modified from the rEFInd neon theme. Original project by peteyyz.

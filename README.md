# Setting-Up-Android-On-Arch-Linux
By using a package known as waydroid we can make an Android environement in Arch Linux

> [!IMPORTANT]
> Commands are based on arch-linux, however packages should be the same for other distros.

> [!CAUTION]
> Make sure you have an internet connection and an user with sudo perms.
> Make you have an AUR helper setup such as yay

To install, execute the following commands:

# Update your system:
```shell
sudo pacman -Syu
```

# Install Waydroid using yay:
```shell
yay -S waydroid
```

# Check if zen kernal is installed:
```shell
pacman -Q | grep '^linux'
```
If you recive any output with mention of zen, you are good to go.
If not, run the following command to install zen-kernal:
```shell
sudo pacman -Syu linux-zen linux-zen-headers
```
Afterwards Update Grub:
```shell
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
Restart your system for changes to apply

# Setting up waydroid Images and vendors
```shell
waydroid init -s GAPPS
```
Alternatively you can also use the waydroid GUI

# Usage commands
To lauch the waydroid session:
```shell
waydroid session start 
```

To lauch the GUI:
```shell
waydroid show-full-ui
```

To stop the waydroid session:
```shell
waydroid session stop
```

# On first boot the google apps will not be supported, In order to run google apps on waydroid session follow the below steps:
Lauch a Waydroid Shell:
```shell
waydroid shell
```

Type the following and note the number string output:
```shell
ANDROID_RUNTIME_ROOT=/apex/com.android.runtime ANDROID_DATA=/data ANDROID_TZDATA_ROOT=/apex/com.android.tzdata ANDROID_I18N_ROOT=/apex/com.android.i18n sqlite3 /data/data/com.google.android.gsf/databases/gservices.db "select * from main where name = \"android_id\";"
```

Go to https://www.google.com/android/uncertified and use the output number string to register your waydroid image.
</div>

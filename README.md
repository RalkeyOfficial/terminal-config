# Terminal setup

My current setup for the terminal on Windows.
Along with a installation guide.

<img src="not-important/image.png" />

---

## step 1: installing the right apps

### Terminal
Open up the Microsoft Store and search for "Windows Terminal", then install. <br>
Alternatively you can follow [this link.](https://www.microsoft.com/store/productId/9N0DX20HK701?ocid=pdpshare)

### Powershell
Open up the Microsoft Store and search for "Powershell", then install. <br>
Alternatively you can follow [this link.](https://www.microsoft.com/store/productId/9MZ1SNWT0N5D?ocid=pdpshare)

### WSL Debian (optional)
*This is only recommended if you have Linux experience.* <br>
Open Powershell as Administrator and type in the following command.
```powershell
wsl --install -d Debian
```
Then go through the setup steps on Debian.

### Starship
#### Windows (With [Chocolatey](https://chocolatey.org/))
Open up CMD as Administrator and type in the following command
```powershell
choco install starship
```

#### Windows (Without [Chocolatey](https://chocolatey.org/))
Download and install the latest MSI-installer from their [releases on github](https://github.com/starship/starship/releases/latest)

#### Linux Debian (Only if you installed WSL)
Open up WSL and start by updating the system with the following command:
```bash
sudo apt update && sudo apt upgrade
```
Then install `curl`:
```bash
sudo apt install curl
```

When that is done install Starship with this command
```bash
curl -sS https://starship.rs/install.sh | sh
```

## Step 2: Installing the right font

Go to [nerdfonts.com](https://www.nerdfonts.com/font-downloads) and pick out a font you like. <br>
I went for "CaskaydiaMono Nerd Font". [[click to download]](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/CascadiaMono.zip)

## Step 3: Setting up the Terminal

Open up the Terminal and go to the settings (`ctrl` + `,`), at the bottom-left click on `Open JSON file`. <br>
In there delete everything and paste in the settings from [settings.json](terminal/settings.json) (or only replace the schemes). <br>
Now save this file (do not press save in the Terminal itself) and reopen the Terminal.

Go back to settings and under Profiles click "Default", Then go to "Appearance". <br>
Verify that the Color scheme is set to `Sexy Mama` and the Font is set to `CaskaydiaMono Nerd Font`.

Then go to the "PowerShell" profile and add ` -nologo` at the end of the Command line.

Make sure to press Save.

## Step 4: setting up starship

### Windows
Go to you user folder by pressing `windows key` + `r`, then type in `%userprofile%` and press Enter, <br>
and make a folder in there called `.config`. <br>
Download the [starship.toml](starship/starship.toml) file to that folder.

#### Powershell
Using [VScode](https://code.visualstudio.com/), open the `$PROFILE` by typing in:
```powershell
code $PROFILE
```
And at the end of the file paste in:
```powershell
Invoke-Expression (&starship init powershell)
```

#### Command Prompt
Install [Clink](https://github.com/chrisant996/clink/releases/latest) by downloading and installing the setup file from Github.

Using [VScode](https://code.visualstudio.com/), open a `clink\starship.lua` file by typing in:
```powershell
code %LocalAppData%\clink\starship.lua
```
And at the end of the file paste in:
```batch
load(io.popen('starship init cmd'):read("*a"))()
```

Then Save that file.

### Debian

Open up `.bashrc` in NANO by typing in:
```bash
nano ~/.bashrc
```
Move down with the arrow keys and at the end of the file paste in:
```bash
eval "$(starship init bash)"
```

save the file by pressing `ctrl` + `s` and close NANO by pressing `ctrl` + `x`.

Then open up a new file by typing:
```bash
nano ~/.config/starship.toml
```
And past in the contents from [starship.toml](starship/starship.toml).


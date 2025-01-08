# nix-esd-2025

The purpose of this repository is to provide nix installation instructions and configuration files for the ESD computer science program.

## Windows

### 1. Update WSL (Windows Subsystem for Linux) to the latest version

    Open a powershell instance with administrator permissions and run the following command:

    ```
    wsl --update
    ```

    This should update your WSL the latest version.

### 2. Download and Install NixOS

    Download the latest NixOS-WSL binary from the [NixOS-WSL github][https://github.com/nix-community/NixOS-WSL/releases]. It will be the file called "nixos-wsl.tar.gz".

    Download the file and open a windows powershell instance with administrator permissions. Navigate to the directory where the downloaded file is contained (should be in C:/users/{user name}/downloads) and run the following commands:

```
wsl --import NixOS $env:USERPROFILE\NixOS\ nixos-wsl.tar.gz --version 2
```

Once this command completes, NixOS is installed! Run the following two commands to finish the installation process.

```
sudo nix-channel --update
```

```
wsl -s NixOS
```

Now by running the command `wsl` in a powershell instance, you can open a NixOS shell to run programs in.

### 3. Configure NixOS using the provided configuration

Open another powershell instance and open a NixOS shell using the command `wsl`. Download the configuration-windows.nix file provided in this repo, and navigate to the directory where it was downloaded. Then, run the following command:

```
sudo nixos-rebuild switch -I nixos-config=configuration-windows.nix
```

This will add Python and some other utilities to your NixOS installation. This completes the installation.

### 4. Utilizing NixOS in VSCode

To use NixOS in vscode, press the two arrows at the bottom left corner of the vscode window. This will open a drop down menu at the top of the window. Select the option "Connect to WSL," which will restart your VSCode in a NixOS virtual environment. Press "Explorer," one of the icons on the left sidebar, press the blue "Open File" button and press "Ok." This will put you into the WSL file system. Create a new folder named "Programs," where you will store your files. Now if you create a `.py` file in this NixOS file system, you should be able to run it by pressing the green button in VSCode.

## MacOS

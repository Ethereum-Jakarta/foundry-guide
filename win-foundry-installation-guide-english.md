# Installing Foundry

This guide outlines methods for installing Foundry on both macOS and Windows systems.

## Installing Foundry on macOS

Installation on macOS is straightforward as it already comes with the necessary Unix-based environment.

### Prerequisites

Before installing Foundry on macOS, ensure you have:
- macOS 10.15 Catalina or newer
- Terminal application
- At least 1GB of free disk space

### Steps for macOS Installation

1. Open Terminal
2. Run the Foundryup installation script:
   ```bash
   curl -L https://foundry.paradigm.xyz | bash
   ```
3. Follow the prompts to complete the installation
4. Start a new terminal session or run:
   ```bash
   source ~/.zshrc  # or source ~/.bash_profile depending on your shell
   ```
5. Install Foundry by running:
   ```bash
   foundryup
   ```
6. Verify installation by checking the versions:
   ```bash
   forge --version
   cast --version
   anvil --version
   ```

**After completing macOS installation, skip to the [Setting Up Node.js](#setting-up-nodejs) section.**

## Installing Foundry on Windows

Windows installation requires WSL (Windows Subsystem for Linux) to provide a Linux environment.

### Prerequisites for Windows

Before installing Foundry on Windows, ensure you have:
- Windows 10 version 2004 and higher (Build 19041 and higher) or Windows 11
- Admin access to your machine
- At least 5GB of free disk space
- A terminal emulator (Windows Terminal recommended)

### Step 1: Enable Hyper-V Feature

1. Press the Windows key and search for "Turn Windows features on or off"
2. In the Windows Features dialog, scroll down and check the box next to "Hyper-V"
3. Also ensure "Virtual Machine Platform" is checked
4. Click OK and wait for the features to be installed
5. Restart your computer when prompted

### Step 2: Install WSL

1. Open PowerShell or Windows Command Prompt as Administrator
2. Run the following command:
   ```powershell
   wsl --install
   ```
   This will install Ubuntu by default. If you want a specific distribution, use:
   ```powershell
   wsl --install -d Ubuntu-22.04
   ```
3. Restart your computer when prompted
4. After restart, a terminal will open automatically to complete the Ubuntu setup
5. Create a username and password when prompted

### Step 3: Install Foundry in WSL

1. Open your WSL terminal (Ubuntu)
2. Run the following command to install Foundryup:
   ```bash
   curl -L https://foundry.paradigm.xyz | bash
   ```
3. Follow the prompts to complete the installation
4. Start a new terminal session or run:
   ```bash
   source ~/.bashrc
   ```
5. Install Foundry by running:
   ```bash
   foundryup
   ```
6. Verify installation by checking the versions:
   ```bash
   forge --version
   cast --version
   anvil --version
   ```

### Step 4: Install VS Code and Remote Development Extension

Open VS Code and install the "Remote Development" extension by Microsoft if you haven't already.

### Step 5: Connect VS Code to WSL

1. Click button on the lower-left corner of VS Code
2. Select "Connect to WSL" from the dropdown menu
3. VS Code will reopen connected to your WSL environment

## Setting Up Node.js

<a name="setting-up-nodejs"></a>

### For macOS

Open Terminal and install nvm and Node.js:
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
# Source nvm
source ~/.zshrc  # or source ~/.bash_profile depending on your shell
# Install and use Node.js 18
nvm install 18
nvm use 18
```

### For Windows (WSL)

Open VS Code terminal that has been connected to WSL and install nvm and Node.js:
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
# Source nvm
source ~/.bashrc
# Install and use Node.js 18
nvm install 18
nvm use 18
```

## Installing Yarn

Install Yarn package manager (needed as our package manager for this workshop):

```bash
npm install -g yarn
```

## Cloning a Repository

After everything has been set up, you can clone a repository related to this workshop later.

## Troubleshooting

### Common Issues on Windows

1. **Hyper-V not available:**
   - Make sure virtualization is enabled in your BIOS/UEFI settings
   - Verify that your Windows edition supports Hyper-V (Pro, Enterprise, or Education)
   - Run `systeminfo` in Command Prompt to check if virtualization is enabled

2. **"Command not found" errors:**
   - Ensure you've opened a new terminal session after installation
   - Check that the binaries are in your PATH

3. **Permission issues:**
   - In WSL, you might need to use `sudo` for some operations
   - In Windows, run your terminal as Administrator

4. **Git authentication errors:**
   - Set up your Git credentials with:
     ```bash
     git config --global user.email "your-email@example.com"
     git config --global user.name "Your Name"
     ```

5. **WSL integration issues:**
   - Ensure you're accessing Windows files correctly via `/mnt/c/` path in WSL
   - Consider using VSCode with the "Remote - WSL" extension for seamless development

### Common Issues on macOS

1. **Permission errors:**
   - You might need to use `sudo` for some operations
   - Make sure your user has the correct permissions

2. **Command not found after installation:**
   - Ensure your shell profile (`.zshrc` or `.bash_profile`) has been updated and sourced
   - Check that the Foundry binaries are in your PATH

## Getting Started with Foundry

After installation, create your first project:
```bash
# Create a new directory
mkdir my-foundry-project
cd my-foundry-project
# Initialize a new Foundry project
forge init
```

Run tests:
```bash
forge test
```

For more information or alternative installation, check the [Foundry Book](https://book.getfoundry.sh/).

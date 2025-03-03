# Installing Foundry on Windows

This guide outlines method for installing Foundry on Windows, using WSL (Windows Subsystem for Linux).

## Prerequisites

Before installing Foundry, ensure you have:

- Windows 10 version 2004 and higher (Build 19041 and higher) or Windows 11
- Admin access to your machine
- At least 5GB of free disk space
- A terminal emulator (Windows Terminal recommended)

### Step 1: Install WSL

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

### Step 2: Install Foundry in WSL

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

### Step 3: Install VS Code and Remote Development Extension

Open VS Code and install the "Remote Development" extension by Microsoft if you haven't already.

### Step 4: Connect VS Code to WSL

1. Click button on the lower-left corner of VS Code
2. Select "Connect to WSL" from the dropdown menu
3. VS Code will reopen connected to your WSL environment

### Step 5: Set Up Node.js in WSL

Open VS Code terminal that has been connected to WSL and install nvm and Node.js:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Source nvm
source ~/.bashrc # or source ~/.zshrc if you use zsh

# Install and use Node.js 18
nvm install 18
nvm use 18
```

### Step 6: Install Yarn

Install Yarn package manager (We need yarn as our package manager for this workshop):

```bash
npm install -g yarn
```

### Step 7: Cloning a Repository

After everything has been set up, you can clone a repository related to this workshop later.

## Troubleshooting

### Common Issues

1. **"Command not found" errors:**

   - Ensure you've opened a new terminal session after installation
   - Check that the binaries are in your PATH

2. **Permission issues:**

   - In WSL, you might need to use `sudo` for some operations
   - In Windows, run your terminal as Administrator

3. **Git authentication errors:**

   - Set up your Git credentials with:
     ```bash
     git config --global user.email "your-email@example.com"
     git config --global user.name "Your Name"
     ```

4. **WSL integration issues:**
   - Ensure you're accessing Windows files correctly via `/mnt/c/` path in WSL
   - Consider using VSCode with the "Remote - WSL" extension for seamless development

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

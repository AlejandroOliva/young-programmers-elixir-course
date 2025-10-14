# 💻 Local Installation of Elixir and Livebook

## 🎯 Introduction

This guide will help you install **Elixir** and **Livebook** directly on your computer. This is the recommended option because it offers the best performance and is ideal for long-term use.

## 📋 Prerequisites

- Computer with Windows, macOS, or Linux
- Internet connection for installation
- Approximately 1 GB of free disk space
- Administrator permissions on the system

## 🪟 Installation on Windows

### Step 1: Install Elixir

#### Option A: Using the Official Installer (Recommended)

1. **Download the installer:**
   - Go to https://elixir-lang.org/install.html
   - Look for the Windows section
   - Download the `.exe` installer from the Elixir Installer link

2. **Run the installer:**
   - Double-click the downloaded file
   - Follow the wizard instructions
   - Accept the default location
   - Wait for the installation to complete

3. **Verify the installation:**
   - Open "Command Prompt" (cmd) or PowerShell
   - Type: `elixir --version`
   - You should see something like: `Elixir 1.16.x (compiled with Erlang/OTP 26)`

#### Option B: Using Chocolatey

If you already have Chocolatey installed:

```powershell
choco install elixir
```

### Step 2: Install Livebook on Windows

1. **Download Livebook Desktop:**
   - Go to https://livebook.dev/#install
   - Download the version for Windows (.exe)

2. **Install Livebook:**
   - Run the downloaded installer
   - Follow the instructions
   - A desktop shortcut will be created

3. **Start Livebook:**
   - Double-click the Livebook icon
   - It will open automatically in your browser
   - You're ready to start using Livebook!

## 🍎 Installation on macOS

### Step 1: Install Homebrew (if you don't have it)

Homebrew is a package manager for macOS that makes installation easier.

1. **Open Terminal** (search for "Terminal" in Spotlight)

2. **Install Homebrew:**
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

3. **Follow the on-screen instructions**

### Step 2: Install Elixir

```bash
brew install elixir
```

### Step 3: Verify the installation

```bash
elixir --version
```

You should see information about the Elixir and Erlang versions.

### Step 4: Install Livebook

#### Option A: Livebook Desktop (Recommended)

1. Go to https://livebook.dev/#install
2. Download the version for macOS (.dmg)
3. Open the downloaded file
4. Drag Livebook to the Applications folder
5. Open Livebook from Applications
6. The first time, right-click → Open (due to security permissions)

#### Option B: Using Elixir directly

```bash
mix do local.rebar --force, local.hex --force
mix escript.install hex livebook
```

To run Livebook:
```bash
livebook server
```

## 🐧 Installation on Linux

### Ubuntu/Debian

#### Step 1: Add the Erlang Solutions repository

```bash
wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb
sudo dpkg -i erlang-solutions_2.0_all.deb
sudo apt-get update
```

#### Step 2: Install Elixir

```bash
sudo apt-get install elixir
```

#### Step 3: Verify

```bash
elixir --version
```

### Fedora/CentOS/RHEL

```bash
sudo dnf install elixir
```

### Arch Linux

```bash
sudo pacman -S elixir
```

### Installing Livebook on Linux

#### Option A: Livebook Desktop

1. Go to https://livebook.dev/#install
2. Download the version for Linux (.AppImage)
3. Make the file executable:
   ```bash
   chmod +x Livebook-*.AppImage
   ```
4. Run the file:
   ```bash
   ./Livebook-*.AppImage
   ```

#### Option B: Using Mix

```bash
mix do local.rebar --force, local.hex --force
mix escript.install hex livebook
```

Make sure `~/.mix/escripts` is in your PATH:

```bash
export PATH="$PATH:$HOME/.mix/escripts"
```

To run:
```bash
livebook server
```

## ✅ Installation Verification

### Test Elixir

1. Open a terminal/console
2. Run:
   ```bash
   iex
   ```
3. You should see something like:
   ```
   Erlang/OTP 26 [erts-14.2] [source] [64-bit] [smp:8:8]
   
   Interactive Elixir (1.16.0) - press Ctrl+C to exit
   iex(1)>
   ```
4. Try typing:
   ```elixir
   IO.puts("Hello, world!")
   ```
5. To exit, press `Ctrl+C` twice

### Test Livebook

1. Open Livebook (desktop icon or by running `livebook server`)
2. A browser window will open
3. Click on "New notebook"
4. Write in the first cell:
   ```elixir
   IO.puts("My first code in Livebook!")
   ```
5. Press the "Evaluate" button or use `Ctrl+Enter`
6. You should see the message in the output

## 🎨 Initial Livebook Configuration

### First time opening Livebook

1. **Welcome screen:**
   - You'll see a clean interface with options to create notebooks
   - Familiarize yourself with the interface

2. **Create a folder for the course:**
   - On your system, create a folder called `ElixirKidsCourse`
   - Inside Livebook, use "Open" to navigate to that folder
   - Save the course notebooks here

3. **Install Kino (necessary for Levels 1-3):**
   - Open a new notebook
   - In the first cell, write:
     ```elixir
     Mix.install([
       {:kino, "~> 0.12.0"}
     ])
     ```
   - Run the cell
   - Kino will install automatically

### Useful Keyboard Shortcuts in Livebook

- `Ctrl + Enter` or `Cmd + Enter`: Run current cell
- `Shift + Enter`: Run cell and move to next
- `Ctrl + S` or `Cmd + S`: Save notebook
- `Escape`: Exit edit mode
- `Enter`: Enter edit mode

## 🔧 Common Problem Solutions

### "elixir is not recognized as a command"

**Problem:** The system doesn't find Elixir after installing it.

**Solution:**
1. Close and reopen the terminal
2. Verify that Elixir is in the PATH:
   - Windows: Search for "Environment Variables" in the Start menu
   - macOS/Linux: Check the `.bashrc` or `.zshrc` file

### Livebook doesn't open in browser

**Problem:** When running Livebook, the browser doesn't open automatically.

**Solution:**
1. Look in the terminal for a message like: `Access Livebook at http://localhost:8080/...`
2. Copy that complete URL
3. Open it manually in your browser

### Error "Mix is not available"

**Problem:** When trying to install packages, this error appears.

**Solution:**
```bash
mix local.hex --force
mix local.rebar --force
```

### Livebook closes unexpectedly

**Problem:** Livebook Desktop closes on its own.

**Solution:**
1. Verify you have enough available RAM (minimum 2GB free)
2. Close other programs that consume many resources
3. Try running Livebook from terminal to see error messages

### Permission errors on Linux/macOS

**Problem:** "Permission denied" messages when installing.

**Solution:**
- Don't use `sudo` to install Elixir packages with Mix
- If necessary, change permissions of your home directory:
  ```bash
  sudo chown -R $USER ~/.mix
  ```

### Kino interactive buttons don't appear

**Problem:** Examples with Kino don't show visual elements.

**Solution:**
1. Make sure you've run `Mix.install([{:kino, "~> 0.12.0"}])` at the start of the notebook
2. Restart the runtime: In Livebook, go to "Runtime" → "Reconnect"
3. Re-run all cells from the beginning

## 🚀 Optimization and Improvements

### Improve performance

1. **Increase available memory:**
   - Close unnecessary applications during sessions
   - Consider increasing system RAM if it's very slow

2. **Use an SSD:**
   - If your computer has a traditional hard drive, consider upgrading to SSD
   - Significantly improves loading speed

### Install useful extensions

#### VS Code with Elixir (optional for Levels 4-5)

If you want to use an advanced code editor:

1. Install [Visual Studio Code](https://code.visualstudio.com/)
2. Install the extensions:
   - "ElixirLS"
   - "Elixir Formatter"
3. Configure ElixirLS following its documentation

## 📁 Recommended Organization

Create this structure on your computer:

```
Documents/
└── ElixirKidsCourse/
    ├── level_1/
    │   ├── class_01.livemd
    │   ├── class_02.livemd
    │   └── ...
    ├── level_2/
    │   └── ...
    ├── projects/
    │   └── my_creations/
    └── extra_exercises/
```

## 🔄 Updating

### Update Elixir

**Windows (with Chocolatey):**
```powershell
choco upgrade elixir
```

**macOS:**
```bash
brew upgrade elixir
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get update
sudo apt-get upgrade elixir
```

### Update Livebook

#### Livebook Desktop:
1. Download the new version from https://livebook.dev
2. Install over the previous version

#### Livebook from Mix:
```bash
mix escript.install hex livebook --force
```

## 📞 Next Steps

Once you have everything installed and verified:

1. ✅ Familiarize yourself with the Livebook interface
2. ✅ Create the folder structure for the course
3. ✅ Download the notebooks from [Level 1](../level_1/README.md)
4. ✅ Start the first class!

## 💡 Final Tips

- **Save frequently:** Livebook auto-saves, but use `Ctrl+S` by habit
- **Experiment fearlessly:** You can close and reopen notebooks without losing saved progress
- **Use descriptive names:** Name your notebooks clearly
- **Check the [troubleshooting guide](troubleshooting.md)** if you encounter problems

---

**Ready to program? Let's go! 🚀**


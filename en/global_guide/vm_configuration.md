# 🖥️ Virtual Machine Configuration

## 🎯 Introduction

A virtual machine (VM) provides a completely isolated environment to run Elixir and Livebook. This option is ideal if:

- You want a dedicated environment without touching your main operating system
- You need to replicate the same environment on multiple computers
- You want to experiment without risk of affecting your system
- You work in an educational environment with multiple students

## 📋 Prerequisites

- Computer with at least 8 GB of RAM (to assign 2-4 GB to the VM)
- 20-30 GB of free disk space
- Processor with virtualization support (Intel VT-x or AMD-V)
- Host operating system: Windows, macOS or Linux

## 🛠️ Virtualization Tools

### Option A: VirtualBox (Recommended - Free)

**Advantages:**
- ✅ Free and open-source
- ✅ Works on Windows, macOS and Linux
- ✅ Friendly interface
- ✅ Well documented

### Option B: VMware Workstation Player (Windows/Linux)

**Advantages:**
- ✅ Better performance
- ✅ Free version for personal use
- ✅ Smoother integration

## 📥 VirtualBox Installation

### Step 1: Download and Install VirtualBox

1. **Download VirtualBox:**
   - Go to https://www.virtualbox.org/wiki/Downloads
   - Download the version for your operating system
   - Approximate size: 100-150 MB

2. **Install VirtualBox:**
   - Run the downloaded installer
   - Follow the wizard instructions
   - Accept network driver installation if requested
   - Restart if necessary

3. **Verify installation:**
   - Open VirtualBox
   - You should see the main interface

## 💿 Create the Virtual Machine

### Option 1: Use Ubuntu (Recommended for beginners)

#### Download Ubuntu

1. Go to https://ubuntu.com/download/desktop
2. Download Ubuntu 22.04 LTS (stable version)
3. Size: ~4 GB

#### Create VM in VirtualBox

1. **Open VirtualBox**
2. **Click "New"**
3. **Configure:**
   - **Name:** ElixirKids
   - **Type:** Linux
   - **Version:** Ubuntu (64-bit)

4. **RAM Memory:**
   - Assign **2048 MB (2 GB)** minimum
   - Recommended: **4096 MB (4 GB)**
   - Don't assign more than 50% of your total RAM

5. **Hard disk:**
   - Select "Create a virtual hard disk now"
   - Type: **VDI (VirtualBox Disk Image)**
   - Storage: **Dynamically allocated**
   - Size: **20 GB** minimum, **30 GB** recommended

6. **Click "Create"**

## 📦 Install Elixir and Livebook in VM

Once Ubuntu is running:

### Step 1: Update System

```bash
sudo apt update
sudo apt upgrade -y
```

### Step 2: Install Elixir

```bash
wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb
sudo dpkg -i erlang-solutions_2.0_all.deb
sudo apt update
sudo apt install elixir -y
```

### Step 3: Install Livebook

```bash
mix local.hex --force
mix local.rebar --force
mix escript.install hex livebook
echo 'export PATH="$PATH:$HOME/.mix/escripts"' >> ~/.bashrc
source ~/.bashrc
```

### Step 4: Test

```bash
livebook server
```

Open Firefox in the VM and go to: http://localhost:8080

## 💡 Advantages of Using VM

✅ **Total isolation:** Doesn't affect your main system
✅ **Snapshots:** You can go back if something goes wrong
✅ **Portability:** Export/import on different computers
✅ **Consistent environment:** Same setup for all students

---

**Your virtual environment is ready! 🖥️🚀**


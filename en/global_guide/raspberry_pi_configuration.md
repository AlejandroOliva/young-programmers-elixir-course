# 🥧 Raspberry Pi Configuration

## 🎯 Introduction

A Raspberry Pi is a small low-cost computer perfect for creating a **dedicated educational lab** for programming.

## 📋 What Raspberry Pi Do I Need?

### Recommended Models

| Model | RAM | Performance | Approx Price |
|-------|-----|-------------|--------------|
| **Raspberry Pi 4B (4GB)** | 4 GB | ⭐⭐⭐⭐⭐ Excellent | $55-75 USD |
| **Raspberry Pi 4B (2GB)** | 2 GB | ⭐⭐⭐⭐ Good | $35-45 USD |
| **Raspberry Pi 5** | 4/8 GB | ⭐⭐⭐⭐⭐ Best | $60-80 USD |

**Recommendation:** Raspberry Pi 4B with 4GB RAM for better experience.

## 💿 Operating System Installation

### Option 1: Raspberry Pi OS (Recommended)

#### Step 1: Download Raspberry Pi Imager

1. **On your main computer:**
   - Go to https://www.raspberrypi.com/software/
   - Download Raspberry Pi Imager for your operating system
   - Install the program

#### Step 2: Prepare SD Card

1. **Insert microSD card** in your computer (use adapter if needed)
2. **Open Raspberry Pi Imager**
3. **Configure:**
   - **Device:** Select your model (e.g. Raspberry Pi 4)
   - **OS:** Raspberry Pi OS (64-bit)
   - **Storage:** Select your SD card

4. **Advanced configuration:**
   - Click gear icon ⚙️
   - ✅ Set hostname: `elixirkids`
   - ✅ Enable SSH
   - ✅ Set username: `elixir` and password
   - ✅ Configure WiFi
   - ✅ Set timezone and keyboard

5. **Click "Write"**

## 📦 Install Elixir and Livebook

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
sudo apt install -y esl-erlang elixir
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
livebook server --ip 0.0.0.0
```

## 💡 Advantages of Using Raspberry Pi

✅ **Dedication:** Device only for programming
✅ **Economical:** Low initial investment ($100-150)
✅ **Portable:** Easy to move and transport
✅ **No distractions:** Controlled environment
✅ **Educational:** Also learn about hardware and Linux

---

**Your educational lab is ready! 🥧🚀**


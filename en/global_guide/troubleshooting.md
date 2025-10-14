# 🔧 Troubleshooting Guide

## 🎯 Introduction

This guide will help you solve the most common problems that may arise during the course.

---

## 📑 Quick Index

1. [Installation Problems](#-installation-problems)
2. [Livebook Problems](#-livebook-problems)
3. [Elixir Code Errors](#-elixir-code-errors)
4. [Kino Problems](#-kino-problems)
5. [Performance Problems](#-performance-problems)

---

## 🔨 Installation Problems

### "Command 'elixir' not found"

**Problem:** System doesn't find Elixir after installing.

**Solution:**

**On Windows:**
1. Close and reopen terminal/PowerShell
2. If persists:
   - Search "Environment Variables" in Start menu
   - Verify Elixir path is in PATH
   - Typically: `C:\Program Files\Elixir\bin`
3. Restart computer

**On macOS/Linux:**
```bash
# Check where Elixir is installed
which elixir

# If shows nothing, check installation
# macOS with Homebrew:
brew list elixir

# Linux:
dpkg -l | grep elixir

# Add to PATH
echo 'export PATH="$PATH:/usr/local/bin"' >> ~/.bashrc
source ~/.bashrc
```

### Mix is not available

**Problem:** Error "Mix is not available"

**Solution:**
```bash
mix local.hex --force
mix local.rebar --force
```

---

## 📓 Livebook Problems

### Livebook doesn't open in browser

**Problem:** Livebook runs but browser doesn't open automatically.

**Solution:**
1. Look in terminal for message like:
   ```
   [Livebook] Application running at http://localhost:8080/?token=abcd1234
   ```
2. Copy complete URL (including token)
3. Open manually in browser

### Error "Port 8080 already in use"

**Problem:** Port 8080 is being used by another application.

**Solution:**

**Option A: Change Livebook port**
```bash
livebook server --port 9090
```

**Option B: Find and stop process using the port**

On Linux/macOS:
```bash
lsof -i :8080
kill -9 PID
```

On Windows:
```powershell
netstat -ano | findstr :8080
# Note PID and stop in Task Manager
```

### Cells don't execute

**Problem:** Pressing "Evaluate" does nothing.

**Solution:**
1. Verify Runtime is connected (top right should say "Connected")
2. If "Disconnected": Runtime → Reconnect
3. Check for syntax errors in previous cells
4. Execute cells in order from beginning

---

## 💻 Elixir Code Errors

### ** (CompileError) undefined function

**Problem:**
```elixir
** (CompileError) undefined function sum/2
```

**Cause:** Trying to use a function that doesn't exist or isn't defined.

**Solution:**
1. Verify the function is defined
2. Make sure cells execute in order
3. If function is in another module:
   ```elixir
   MyModule.sum(1, 2)
   ```

### ** (ArithmeticError) bad argument

**Problem:**
```elixir
iex> "5" + 3
** (ArithmeticError) bad argument in arithmetic expression
```

**Solution:**
```elixir
# Convert string to number
String.to_integer("5") + 3  # => 8
```

### ** (MatchError) no match of right hand side value

**Problem:** Pattern matching fails.

**Solution:**
```elixir
# Use case to handle different cases
case function() do
  {:ok, value} -> IO.puts("Success: #{value}")
  {:error, reason} -> IO.puts("Error: #{reason}")
end
```

---

## 🎨 Kino Problems

### Kino not available

**Problem:**
```elixir
** (UndefinedFunctionError) function Kino.Input.text/1 is undefined
```

**Solution:**
In first cell of notebook:
```elixir
Mix.install([{:kino, "~> 0.12.0"}])
```

Execute this cell and wait before using Kino in other cells.

### Kino widgets don't appear

**Problem:** Cells with `Kino.Input` show nothing.

**Solution:**
1. Make sure you're running in Livebook (not iex terminal)
2. Restart runtime: Runtime → Reconnect
3. Re-execute cell with `Mix.install`
4. Then execute cells with Kino

---

## 🐌 Performance Problems

### Livebook is very slow

**Problem:** Interface responds slowly.

**Solution:**
1. Close notebooks you're not using
2. Restart runtime: Runtime → Disconnect and reconnect
3. Limit data output
4. Close browser tabs you don't use
5. Assign more memory if using Docker/VM

---

## 🆘 When Nothing Works

### Clean Reinstall

**Option A: Livebook Desktop**
1. Completely uninstall Livebook
2. Download latest version
3. Install again

**Option B: Local installation**
```bash
# Uninstall
# Windows: Use "Add or remove programs"
# macOS: brew uninstall elixir && brew cleanup
# Linux: sudo apt-get remove --purge elixir

# Clean configuration
rm -rf ~/.mix
rm -rf ~/.hex

# Reinstall following installation guide
```

**Option C: Docker (fresh start)**
```bash
docker rm -f $(docker ps -a -q)
docker rmi livebook/livebook
docker pull livebook/livebook:latest
docker run -p 8080:8080 --pull always livebook/livebook
```

### Seek Help

**Forums and Communities:**
1. [Elixir Forum](https://elixirforum.com) - Very friendly
2. [Stack Overflow with elixir tag](https://stackoverflow.com/questions/tagged/elixir)
3. [Reddit r/elixir](https://reddit.com/r/elixir)

**When asking for help, include:**
- ✅ Operating system and version
- ✅ Elixir version (`elixir --version`)
- ✅ What you were trying to do
- ✅ Code that reproduces error
- ✅ Complete error message
- ✅ What you've tried already

---

## 💡 Tips to Prevent Problems

1. **Save frequently:** `Ctrl+S` is your friend
2. **Execute cells in order:** Don't skip cells
3. **Read complete errors:** They contain valuable information
4. **Start simple:** Test basic code first
5. **Keep updated:** Update Elixir and Livebook regularly

---

**Don't give up! Programming involves solving problems, and each error is an opportunity to learn. 💪🚀**


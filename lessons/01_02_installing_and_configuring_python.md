# **1.2. Installing and Configuring Python**  

Python is a cross-platform language that runs on Windows, macOS, and Linux. This section will guide you through downloading, installing, and configuring Python for different environments.

---


## **1.2.1. Installation**  
### **1.2.1.1. Installing Python on Windows**  
1. **Download the installer**  
   - Visit the official Python website: [www.python.org](https://www.python.org/downloads/)  
   - Download the latest stable version for Windows.  

2. **Run the installer**  
   - Double-click the downloaded `.exe` file.  
   - Check **"Add Python to PATH"** before proceeding.  
   - Click **"Install Now"** to complete the installation.  

3. **Verify installation**  
   Open Command Prompt (`Win + R`, type `cmd`, press Enter) and run:  
   ```sh
   python --version
   ```
   You should see an output like:  
   ```
   Python 3.x.x
   ```

---

### **1.2.1.2. Installing Python on macOS**  
1. **Check if Python is pre-installed**  
   Open Terminal and run:  
   ```sh
   python3 --version
   ```
   If Python 3 is installed, you will see the version.  

2. **Install Python using Homebrew (recommended)**  
   If Python is not installed, install it via [Homebrew](https://brew.sh/):  
   ```sh
   brew install python
   ```

3. **Verify installation**  
   ```sh
   python3 --version
   ```

---

### **1.2.1.3. Installing Python on Linux**  
Most Linux distributions come with Python pre-installed. You can check with:  
```sh
python3 --version
```
If not installed, use the following commands based on your Linux distribution:

- **Ubuntu/Debian**  
  ```sh
  sudo apt update
  sudo apt install python3 python3-pip
  ```

- **Fedora**  
  ```sh
  sudo dnf install python3 python3-pip
  ```

- **Arch Linux**  
  ```sh
  sudo pacman -S python python-pip
  ```

Verify the installation:  
```sh
python3 --version
```

---

## **1.2.2. Configuring Python for Development**  
### 1.2.2.1. Setting Up Environment Variables  
- **Windows**:  
  Add Python to the system PATH manually if needed:
  ```sh
  setx PATH "%PATH%;C:\Python39\Scripts"
  ```

- **macOS/Linux**:  
  Add Python to your shell profile (`~/.bashrc`, `~/.zshrc`, etc.):
  ```sh
  export PATH="$HOME/.local/bin:$PATH"
  ```

### 1.2.2.2 Choosing an IDE or Text Editor
Some popular options:  
- **VS Code** (lightweight, highly customizable)  
- **PyCharm** (full-featured, great for large projects)  
- **Jupyter Notebook** (great for data science and experimentation)  



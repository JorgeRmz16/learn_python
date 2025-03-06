# **1.3. Setting Up Virtual Environments**  
A virtual environment allows you to create isolated environments for different projects, preventing dependency conflicts.

### **1.3.1. Creating a Virtual Environment**  
1. **Create a virtual environment**  
   ```sh
   python3 -m venv my_project_env
   ```

2. **Activate the virtual environment**  
   - **Windows**:  
     ```sh
     my_project_env\Scripts\activate
     ```
   - **macOS/Linux**:  
     ```sh
     source my_project_env/bin/activate
     ```

3. **Verify the virtual environment is active**  
   Your terminal will show `(my_project_env)` before the prompt.

4. **Deactivate the virtual environment**  
   ```sh
   deactivate
   ```

---

## **1.3.2. Installing and Managing Packages**  
Python uses `pip`, the package manager, to install third-party libraries.

### 1.3.2.1. Installing Packages with pip 
To install a package (e.g., `requests`):  
```sh
pip install requests
```

### 1.3.2.2 Checking Installed Packages  
```sh
pip list
```

### 1.3.2.3 Uninstalling a Package 
```sh
pip uninstall requests
```

### 1.3.2.4 Using a `requirements.txt` File 
For managing dependencies, create a `requirements.txt` file with package names:  
```
requests
flask
numpy
```
Then, install all dependencies at once:  
```sh
pip install -r requirements.txt
```

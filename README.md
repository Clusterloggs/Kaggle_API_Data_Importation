# Kaggle API Setup and Dataset Download

This guide explains how to **set up the Kaggle API**, authenticate using `kaggle.json`, and download datasets using Python.

---

## 🚀 1. Prerequisites
Before using the Kaggle API, ensure you have the following installed:
- **Python 3.x**
- **pip (Python package manager)**
- **Kaggle API package**

Check your Python version:
```sh
python --version
```

---

## 🛠️ 2. Install the Kaggle API Package
Run the following command in your terminal or command prompt:
```sh
pip install kaggle
```
For Jupyter Notebook:
```python
!pip install kaggle
```

---

##  3. Get Your Kaggle API Key (`kaggle.json`)
1. Go to [Kaggle](https://www.kaggle.com/).
2. Click on your **profile icon** (top-right corner) → **Account**.
3. Scroll to the **API section** and click **"Create New API Token"**.
4. This will download a file called **`kaggle.json`**.

---

##  4. Securely Store the `kaggle.json` File

### **For Windows:**
Move `kaggle.json` to:
```
C:\Users\your-username\.kaggle\kaggle.json
```
**Steps:**
1. Open File Explorer, navigate to `C:\Users\your-username\`.
2. Create a **new folder named `.kaggle`** (if it doesn’t exist).
3. Move `kaggle.json` into this `.kaggle` folder.

---

### **For Mac/Linux:**
Move `kaggle.json` to:
```sh
~/.kaggle/kaggle.json
```
**Steps:**
```sh
mv /path/to/downloaded/kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json  # Secure the file
```

---

##  5. Verify Kaggle API Authentication
Run this script to check if Kaggle API is working:
```python
from kaggle.api.kaggle_api_extended import KaggleApi

# Authenticate using stored kaggle.json
api = KaggleApi()
api.authenticate()

print("Kaggle API authentication successful!")
```
**Expected Output:**
```
Kaggle API authentication successful!
```

---

## 👥 6. Download a Dataset from Kaggle
To download a dataset (e.g., **CIC-DDoS2019 dataset**), run:
```python
# Download dataset
dataset_name = "aymenabb/ddos-evaluation-dataset-cic-ddos2019"
download_path = "./"  # Change this if needed

api.dataset_download_files(dataset_name, path=download_path, unzip=True)

print("Dataset downloaded successfully to:", download_path)
```

After downloading, check your project folder (`./`) or the specified `download_path` for the extracted dataset.

---

## 7. Troubleshooting Issues

### **`ModuleNotFoundError: No module named 'kaggle'`**
**Solution:** Install the Kaggle package:
```sh
pip install kaggle
```

---

### **`OSError: Could not find kaggle.json`**
**Solution:** Ensure `kaggle.json` is stored in the correct directory:
- **Windows:** `C:\Users\your-username\.kaggle\`
- **Mac/Linux:** `~/.kaggle/`
- Run this command to check if the file exists:
  ```python
  import os
  print(os.path.exists(os.path.expanduser("~/.kaggle/kaggle.json")))
  ```
  If it prints **`True`**, the file is correctly placed.

---

## 8. Security Best Practices
- **DO NOT share your API key (`kaggle.json`) publicly** (e.g., on GitHub).
- **DO NOT hardcode your API key** inside scripts.
- **Use Kaggle API securely by storing `kaggle.json` in the `.kaggle/` folder**.

---

## 9. Summary
**Install the Kaggle API package** → `pip install kaggle`  
**Download `kaggle.json` from Kaggle** → Store it in `.kaggle/`  
**Authenticate Kaggle API** using `KaggleApi().authenticate()`  
**Download datasets securely** using `api.dataset_download_files()`  

---

## 🔗 References:
- **Official Kaggle API Docs:** [https://www.kaggle.com/docs/api](https://www.kaggle.com/docs/api)
- **CIC-DDoS2019 Dataset:** [https://www.unb.ca/cic/datasets/ddos-2019.html](https://www.unb.ca/cic/datasets/ddos-2019.html)

---


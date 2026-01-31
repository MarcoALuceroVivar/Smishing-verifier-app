# 📱 Machine Learning-Based SMS Spam & Phishing Filter

**CSCI 401 – Cybersecurity Project | Group 1**

![Project Status](https://img.shields.io/badge/Status-Prototype%20Complete-green)
![Language](https://img.shields.io/badge/Language-Python%20%7C%20Java-blue)

## 📖 Project Overview
This project implements a **real-time SMS filtering system** for Android smartphones. It uses a Machine Learning classifier to automatically detect and block spam or phishing (smishing) messages before the user interacts with them.

The system consists of two parts:
1.  **The Brain (Backend):** A Python-based Machine Learning model hosted on a Flask server that classifies messages as "Spam" or "Ham" (Safe).
2.  **The Shield (Android App):** A native Android application that intercepts incoming SMS messages and queries the backend for a verdict.

## 🛠️ Technology Stack
### Backend (Python)
* **Framework:** Flask (REST API)
* **Machine Learning:** Scikit-Learn (Multinomial Naïve Bayes)
* **Data Processing:** Pandas, Numpy, Joblib
* **Dataset:** UCI SMS Spam Collection

### Frontend (Android)
* **Language:** Java
* **IDE:** Android Studio
* **Key Components:** `BroadcastReceiver` (for interception), `HttpURLConnection` (for API calls)

---

## ⚙️ How It Works
1.  **Training:** The Python script (`train_model.py`) trains a Naïve Bayes classifier on the dataset and saves the model as a `.pkl` file.
2.  **Interception:** The Android app runs a background service that listens for the `android.provider.Telephony.SMS_RECEIVED` event.
3.  **Analysis:** When a text arrives, the app sends the message body to the local Python server via HTTP POST.
4.  **Verdict:** The server analyzes the text and returns a JSON response (`{"result": "spam"}` or `{"result": "ham"}`).
5.  **Action:**
    * **If Spam:** The app alerts the user with a warning toast and logs the threat.
    * **If Safe:** The message is allowed to pass.

---

## 🚀 Installation & Setup

### Part 1: The Backend (Python)
1.  Clone the repository and navigate to the `backend` folder.
2.  Install the required dependencies:
 
    pip install pandas scikit-learn flask joblib
   
3.  Train the model (run this once):

    python train_model.py

4.  Start the server:

    python server.py

    *The server will start on `http://0.0.0.0:5000`.*

### Part 2: The Android App
1.  Open **Android Studio**.
2.  Select **Open an Existing Project** and choose the `SpamFilterApp` folder.
3.  Allow Gradle to sync.
4.  Create an Emulator (Pixel 6 recommended, API 33+).
5.  Click **Run** (Green Play Button).

---

## 🧪 How to Simulate (Demo)
Since this is a prototype running on an emulator, we simulate SMS messages rather than using a real carrier.

1.  Ensure `server.py` is running in your terminal.
2.  Open the Android App in the Emulator.
3.  Click the **three dots (...)** on the Emulator toolbar > **Phone**.
4.  **Send a Spam Message:**
    * **Message:** *"URGENT! You have won a free iPhone. Click here to claim."*
    * **Result:** The app displays **🚫 SPAM**.
5.  **Send a Safe Message:**
    * **Message:** *"Hey, let's meet for lunch tomorrow."*
    * **Result:** The app displays **✅ HAM**.

---

## 📂 Project Structure
```text
/
├── backend/
│   ├── SMSSpamCollection    # The dataset
│   ├── train_model.py       # ML Training Script
│   ├── server.py            # Flask API Server
│   └── spam_model.pkl       # Serialized Model (Generated)
│
├── android-app/
│   ├── app/src/main/
│   │   ├── java/com/example/spamfilter/
│   │   │   ├── MainActivity.java    # UI Logic
│   │   │   └── SmsReceiver.java     # SMS Interceptor Logic
│   │   └── AndroidManifest.xml      # Permissions configuration
│   └── build.gradle
│
└── README.md
````
<br>
<hr>

<h2 align="center">📺 Watch the Live Demo</h2>

<div align="center">
  <a href="https://drive.google.com/file/d/1YBg3FRYuYNN1wiZ76SpPFYxvHclgKKyP/view?usp=drive_link" target="_blank">
    
    <img src="https://github.com/YOUR_USERNAME/YOUR_REPO/blob/main/demo-thumbnail.png?raw=true" 
         alt="Watch the video" 
         width="500" 
         style="border: 2px solid #333; border-radius: 10px; box-shadow: 0px 4px 10px rgba(0,0,0,0.3);" />
  </a>
</div>

<p align="center">
  <em>Click the screen above to watch the full demonstration on Google Drive.</em>
</p>

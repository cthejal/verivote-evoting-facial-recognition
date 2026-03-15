# VeriVote — E-Voting System with Facial Recognition

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat-square)
![Django](https://img.shields.io/badge/Django-3.2-green?style=flat-square)
![OpenCV](https://img.shields.io/badge/OpenCV-4.5-red?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

> A secure digital e-voting web application that uses facial recognition (LBPH algorithm) to verify voter identity before casting a vote — preventing duplicate voting and impersonation fraud.

---

## Problem Statement

Traditional voting systems are vulnerable to identity fraud, duplicate voting, and impersonation. VeriVote addresses these challenges by combining a Django web application with real-time facial recognition — ensuring only verified, registered voters can cast a ballot, and only once.

---

## How It Works

1. **Voter Registration** — Admin registers voters and captures facial images via webcam
2. **Face Training** — System trains an LBPH (Local Binary Patterns Histograms) model on registered voter faces
3. **Identity Verification** — At voting time, webcam captures the voter's face and matches it against the trained model
4. **Vote Casting** — Only if identity is verified, the voter is allowed to cast their vote
5. **Duplicate Prevention** — System ensures each voter can only vote once per election

---

## Features

- Real-time face detection using Haar Cascade Classifier (OpenCV)
- Face recognition using LBPH (Local Binary Patterns Histograms) algorithm
- Voter registration and management via Django admin panel
- Secure vote casting with identity verification gate
- Duplicate vote prevention
- Election results dashboard
- SQLite database for storing voter records and votes

---

## Tech Stack

| Category | Tools |
|---|---|
| Backend Framework | Django 3.2 |
| Face Detection | OpenCV 4.5 (Haar Cascade Classifier) |
| Face Recognition | OpenCV LBPH Face Recognizer |
| Image Processing | NumPy, Pillow |
| Database | SQLite3 / MySQL |
| Frontend | HTML, CSS |
| Language | Python 3.x |

---

## Algorithm — LBPH Face Recognition

The system uses **Local Binary Patterns Histograms (LBPH)** for face recognition:

1. For each pixel in a grayscale face image, compare intensity with surrounding neighbours
2. Assign `1` if neighbour intensity ≥ central pixel, `0` otherwise
3. Generate a binary pattern (LBP code) for each pixel representing local texture
4. Build histograms of LBP codes across face regions
5. Match histograms of captured face against registered voter faces using confidence scoring

This approach is lightweight, works well under varied lighting conditions, and runs in real time on standard hardware.

---

## Project Structure

```
verivote/
│
├── EVoting/                    # Django project settings
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
├── voting/                     # Main Django app
│   ├── models.py               # Voter, Candidate, Vote models
│   ├── views.py                # Voting logic and face verification
│   ├── urls.py
│   └── templates/              # HTML templates
│
├── dataset/                    # Captured voter face images
├── trainer/                    # Trained LBPH model files
├── haarcascade_frontalface_default.xml   # Face detection model
├── manage.py
├── db.sqlite3
└── requirements.txt
```

---

## How to Run

```bash
# 1. Clone the repo
git clone https://github.com/cthejal/verivote.git
cd verivote

# 2. Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run database migrations
python manage.py migrate

# 5. Create admin user
python manage.py createsuperuser

# 6. Start the server
python manage.py runserver

# 7. Open in browser
# http://127.0.0.1:8000
```

> **Note:** A webcam is required for face capture and recognition features.

---

## Requirements

Key dependencies from `requirements.txt`:

```
Django==3.2.18
opencv-python==4.5.5.62
opencv-contrib-python==4.5.5.62
numpy==1.21.6
Pillow==9.5.0
mysqlclient==2.1.0
```

---

## Key Learnings

- Building a full-stack web application using Django (MVC architecture)
- Implementing real-time face detection using Haar Cascade classifiers
- Training and deploying an LBPH face recognition model with OpenCV
- Integrating computer vision into a Django web application
- Designing a secure voting workflow with identity verification gates
- Working with SQLite and MySQL databases via Django ORM

---

## Future Improvements

- [ ] Add liveness detection to prevent photo spoofing
- [ ] Encrypt stored facial data for privacy compliance
- [ ] Add OTP-based two-factor authentication as backup
- [ ] Deploy on cloud (AWS / Heroku) for remote access
- [ ] Add real-time election results with charts

---

## Author

**Thejal C Kotian**
[LinkedIn](https://linkedin.com/in/thejalckotian2003) · [GitHub](https://github.com/cthejal) · thejalck@gmail.com

# 🤖 Intelligent AI Attendance System

An AI-powered attendance management system that automates student attendance using **Face Recognition** and **Voice Recognition**. Built with Python and Streamlit, with Supabase as the backend database.

## 🌐 Live Demo

🚀 **Try the Intelligent AI Attendance System:**  
👉 https://intelligent-ai-attendence.streamlit.app/

> **Note:** The live demo may require access to a webcam/microphone and browser permissions for biometric attendance features.

---

## 📌 Overview

Traditional attendance systems are time-consuming and prone to manual errors. The **Intelligent AI Attendance System** provides an automated solution using Artificial Intelligence and biometric recognition.

The system allows teachers to create subjects, enroll students, conduct attendance sessions, and manage attendance records. Students can enroll in subjects, register their biometric data, and view their attendance.

The project combines:

- 👤 Face Recognition
- 🎙️ Voice Recognition
- 🧠 Machine Learning
- 🗄️ Supabase Database
- 🌐 Streamlit Web Application
- 🔐 Secure Password Hashing
- 📱 QR Code-based Subject Sharing

---

## ✨ Features

### 👨‍🏫 Teacher Portal

Teachers can:

- Create an account
- Log in securely
- Create subjects
- Add students
- Enroll students into subjects
- Add student photographs
- Automatically enroll students
- Conduct face-based attendance
- Conduct voice-based attendance
- View attendance results
- View attendance records
- Share subjects using QR codes

### 👨‍🎓 Student Portal

Students can:

- Create an account
- Log in
- Enroll in subjects
- View enrolled subjects
- Register face data
- Register voice data
- View attendance records
- Unenroll from subjects

---

# 🧠 AI Features

## 👤 Face Recognition

The face recognition system uses **Dlib** and pre-trained face recognition models.

### Workflow

```text
Student Image
      ↓
Face Detection
      ↓
Facial Landmark Detection
      ↓
Face Encoding
      ↓
128-Dimensional Face Embedding
      ↓
SVM Classification
      ↓
Student Identification
      ↓
Attendance Recorded
```

The system extracts facial embeddings from registered students and uses a **Linear Support Vector Machine (SVM)** to identify students during attendance.

A face distance threshold is also used to determine whether the detected face matches a registered student.

---

## 🎙️ Voice Recognition

The system also supports attendance through voice recognition using **Resemblyzer** and **Librosa**.

### Workflow

```text
Audio Input
      ↓
Audio Preprocessing
      ↓
16 kHz Resampling
      ↓
Voice Activity Detection
      ↓
Audio Segmentation
      ↓
Speaker Embedding
      ↓
Similarity Comparison
      ↓
Speaker Identification
      ↓
Attendance Recorded
```

The system generates speaker embeddings and compares them against registered voice embeddings to identify students.

---

# 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │      Streamlit      │
                    │    Web Interface    │
                    └──────────┬──────────┘
                               │
                     ┌─────────▼─────────┐
                     │    Home / Login   │
                     └─────────┬─────────┘
                               │
                  ┌────────────┴────────────┐
                  │                         │
          ┌───────▼───────┐         ┌──────▼───────┐
          │ Teacher Portal │         │ Student Portal│
          └───────┬───────┘         └──────┬───────┘
                  │                         │
                  └────────────┬────────────┘
                               │
                     ┌─────────▼─────────┐
                     │     Supabase      │
                     │      Database     │
                     └─────────┬─────────┘
                               │
                  ┌────────────┴────────────┐
                  │                         │
          ┌───────▼───────┐         ┌──────▼───────┐
          │Face Recognition│         │Voice Recognition│
          │    Pipeline    │         │    Pipeline     │
          └───────┬───────┘         └──────┬───────┘
                  │                         │
                  └────────────┬────────────┘
                               │
                     ┌─────────▼─────────┐
                     │    Attendance     │
                     │      Records      │
                     └───────────────────┘
```

---

# 📂 Project Structure

```text
Intelligent-AI-Attendence/
│
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
│
├── .streamlit/
│   └── secrets.toml
│
└── src/
    │
    ├── components/
    │   ├── dialog_add_photo.py
    │   ├── dialog_attendance_results.py
    │   ├── dialog_auto_enroll.py
    │   ├── dialog_create_subject.py
    │   ├── dialog_enroll.py
    │   ├── dialog_share_subject.py
    │   ├── dialog_voice_attendance.py
    │   ├── footer.py
    │   ├── header.py
    │   └── subject_card.py
    │
    ├── database/
    │   ├── config.py
    │   └── db.py
    │
    ├── pipelines/
    │   ├── face_pipeline.py
    │   └── voice_pipeline.py
    │
    ├── screens/
    │   ├── home_screen.py
    │   ├── student_screen.py
    │   └── teacher_screen.py
    │
    └── ui/
        └── base_layout.py
```

---

# 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| 🐍 Python | Core programming language |
| 🌐 Streamlit | Web application framework |
| 👤 Dlib | Face detection and recognition |
| 🧠 face_recognition_models | Pre-trained face recognition models |
| 📊 Scikit-learn | Machine learning and SVM classification |
| 🔢 NumPy | Numerical computations |
| 🎙️ Resemblyzer | Speaker recognition |
| 🎵 Librosa | Audio processing |
| 🗄️ Supabase | Database and backend |
| 🔐 Bcrypt | Password hashing |
| 📱 Segno | QR code generation |
| 🖼️ Pillow | Image processing |
| 🐼 Pandas | Data processing |

---

# 📁 Important Components

## `app.py`

The main entry point of the application.

It handles:

- Application startup
- Page navigation
- Session state
- Teacher portal
- Student portal

---

## `src/pipelines/face_pipeline.py`

Handles the face recognition pipeline.

Responsibilities include:

- Loading face recognition models
- Detecting faces
- Generating face embeddings
- Training the SVM classifier
- Identifying registered students

---

## `src/pipelines/voice_pipeline.py`

Handles the voice recognition pipeline.

Responsibilities include:

- Loading the Resemblyzer encoder
- Processing audio
- Generating speaker embeddings
- Comparing voice embeddings
- Identifying registered speakers

---

## `src/database/db.py`

Contains the database operations used by the application.

It handles operations related to:

- Teachers
- Students
- Subjects
- Student enrollment
- Attendance
- Attendance retrieval

---

## `src/database/config.py`

Initializes the Supabase connection using Streamlit secrets.

---

# 🗄️ Database

The project uses **Supabase** as the backend database.

The application stores information related to:

- Teachers
- Students
- Subjects
- Subject enrollment
- Attendance records
- Face embeddings
- Voice embeddings

The database layer is separated from the UI and AI pipelines to keep the application modular.

---

# 🔐 Configuration

The application requires Supabase credentials.

Create a file:

```text
.streamlit/secrets.toml
```

and add:

```toml
SUPABASE_URL = "your_supabase_project_url"
SUPABASE_KEY = "your_supabase_key"
```

### ⚠️ Important

Never commit your actual Supabase credentials to GitHub.

Make sure `secrets.toml` is included in `.gitignore`.

For Streamlit Cloud, configure these values through:

**Streamlit Cloud → App Settings → Secrets**

---

# ⚙️ Installation

## 1. Clone the repository

```bash
git clone https://github.com/Kshitij-Mishra-19/Intelligent-AI-Attendence.git
```

## 2. Navigate into the project

```bash
cd Intelligent-AI-Attendence
```

## 3. Create a virtual environment

```bash
python -m venv venv
```

## 4. Activate the virtual environment

### Windows

```powershell
venv\Scripts\activate
```

### Linux / macOS

```bash
source venv/bin/activate
```

## 5. Install dependencies

```bash
pip install -r requirements.txt
```

## 6. Configure Supabase

Create:

```text
.streamlit/secrets.toml
```

and configure your Supabase credentials.

## 7. Run the application

```bash
streamlit run app.py
```

The application will open in your browser.

---

# 📦 Dependencies

The main dependencies are listed in:

```text
requirements.txt
```

The project uses a compatible Setuptools version because the `face_recognition_models` package depends on the legacy `pkg_resources` interface.

The requirements file therefore uses:

```text
setuptools<81
```

This helps avoid:

```text
ModuleNotFoundError: No module named 'pkg_resources'
```

---

# ☁️ Deployment

The application is designed to be deployable using **Streamlit Community Cloud**.

### Deployment Steps

1. Push the project to GitHub.
2. Open Streamlit Community Cloud.
3. Create a new application.
4. Select the GitHub repository.
5. Set the main file to:

```text
app.py
```

6. Configure the required Supabase secrets.
7. Deploy the application.

### Live Application

You can access the deployed application here:

**https://intelligent-ai-attendence.streamlit.app/**

---

# 🔄 Attendance Workflow

A typical attendance session works as follows:

```text
Teacher
   │
   ▼
Select Subject
   │
   ▼
Start Attendance
   │
   ├───────────────┐
   │               │
   ▼               ▼
Face Recognition  Voice Recognition
   │               │
   └───────┬───────┘
           │
           ▼
     Identify Student
           │
           ▼
    Verify Enrollment
           │
           ▼
   Record Attendance
           │
           ▼
      Supabase DB
           │
           ▼
    Attendance Results
```

---

# 🔒 Security

This application handles sensitive information including student information and biometric representations.

For production deployment, additional security measures should be considered:

- Supabase Row Level Security
- Strong authentication
- Authorization checks
- Secure API key management
- Protection of biometric embeddings
- Data encryption
- Data retention policies
- User consent
- Liveness detection
- Secure database policies

**Never expose API keys or credentials in source code.**

---

# ⚠️ Limitations

This project is currently intended primarily as an academic/prototype AI attendance system.

Potential limitations include:

- Face recognition accuracy can vary with lighting and camera quality.
- Recognition performance depends on the quality of enrolled images.
- Voice recognition can be affected by background noise.
- Multiple faces may require additional handling depending on the environment.
- Liveness detection is not implemented.
- Production-grade biometric security requires additional measures.
- Performance may vary depending on deployment resources.

---

# 🚀 Future Improvements

Some possible future improvements include:

- 📊 Attendance analytics dashboard
- 📈 Attendance percentage tracking
- 📅 Automated attendance reports
- 📄 PDF/CSV report generation
- 📧 Email notifications
- 🔔 Low-attendance alerts
- 🛡️ Face liveness detection
- 🔐 Multi-factor authentication
- 📱 Mobile application
- ☁️ Improved cloud architecture
- 🎙️ More robust speaker verification
- 🧠 Advanced face recognition models
- 📊 Student performance analytics
- 📆 Attendance history and trends

---

# 🎯 Project Objectives

The main objectives of this project are:

1. Automate the student attendance process.
2. Reduce manual attendance work.
3. Minimize human errors in attendance records.
4. Apply AI and Machine Learning to a real-world problem.
5. Explore biometric-based authentication.
6. Combine face and voice recognition.
7. Build a cloud-connected attendance management system.
8. Provide separate interfaces for teachers and students.

---

# 💡 Why This Project?

Attendance management is a common problem in educational institutions.

Instead of relying on:

```text
Manual Roll Call
       ↓
Paper/Spreadsheet
       ↓
Manual Data Entry
       ↓
Attendance Reports
```

this project attempts to automate the process:

```text
Biometric Identification
       ↓
AI Recognition
       ↓
Student Verification
       ↓
Automatic Attendance
       ↓
Cloud Database
       ↓
Attendance Records
```

This makes the project a practical demonstration of **AI, Machine Learning, Computer Vision, Speech Processing, Database Management, and Web Development** working together.

---

# 👨‍💻 Author

## Kshitij Mishra

Computer Science & Engineering — AI/ML

GitHub:  
https://github.com/Kshitij-Mishra-19

---

# 🙏 Acknowledgements

This project uses several open-source technologies and libraries, including:

- Dlib
- face_recognition_models
- Scikit-learn
- Resemblyzer
- Librosa
- Streamlit
- Supabase
- Bcrypt
- Segno
- Pillow
- NumPy
- Pandas

---

# ⭐ Support

If you found this project interesting or useful, consider giving the repository a ⭐ on GitHub.

Your support is appreciated! ❤️

---

# 📜 License

This project is intended for educational and learning purposes.

If you plan to distribute or deploy this project commercially, consider adding an appropriate open-source license and reviewing the licensing requirements of all third-party dependencies.

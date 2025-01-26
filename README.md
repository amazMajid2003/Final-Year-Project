Here is a detailed `README.md` file for your Flask-based website project. It includes information about the folder structure, routes, template descriptions, and the video upload and download flow.

---

# Fall Detection System - Flask Web Application

This Flask web application provides a fall detection system, using YOLOv8 for object detection and a fine-tuned MoviNet model for fall prediction. The system processes videos uploaded by the user and performs fall detection, marking the occurrence of a fall in the video. After processing, the user can download the processed video.

## Table of Contents

1. [Folder Structure](#folder-structure)
2. [Setup and Installation](#setup-and-installation)
3. [Routes and Templates](#routes-and-templates)
4. [Video Upload and Download Process](#video-upload-and-download-process)
5. [How the Fall Detection Works](#how-the-fall-detection-works)

---

## Folder Structure

```
your_project/
│
├── static/
│   ├── uploads/               # Folder to store uploaded video files
│   └── processed/             # Folder to store processed video files
│
├── templates/                 
│   ├── index.html             # Home page
│   ├── FallDetection.html     # Fall detection page
│   ├── live-detection.html    # Live video detection page
│   ├── Login.html             # Login page
│   ├── Mental.html            # Mental health detection page
│   ├── ModulesPage.html       # Page for modules information
│   ├── Report.html            # Report generation page
│   ├── SignUp.html            # User sign-up page
│   └── upload-video.html      # Video upload page
│
├── app.py                     # Main Flask app file
└── requirements.txt           # Python dependencies file
```

---

## Setup and Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-repository.git
   ```

2. **Navigate to the project directory:**

   ```bash
   cd your_project
   ```

3. **Create a virtual environment:**

   ```bash
   python3 -m venv venv
   ```

4. **Activate the virtual environment:**

   - On Windows:
     ```bash
     venv\Scripts\activate
     ```

   - On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

5. **Install required dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

6. **Run the Flask app:**

   ```bash
   python app.py
   ```

7. **Visit the application in your browser:**

   Open `http://127.0.0.1:5000/` in your web browser.

---

## Routes and Templates

### 1. **`/` - Home Page**

   **Template:** `index.html`

   The home page provides an introduction to the application and a navigation bar to access other pages. Users can access the Fall Detection page, login, or sign up.

### 2. **`/FallDetection` - Fall Detection Page**

   **Template:** `FallDetection.html`

   This page explains how the fall detection system works. It may contain an introduction to the model, technology used, and examples of fall detection.

### 3. **`/live-detection` - Live Detection Page**

   **Template:** `live-detection.html`

   This page allows users to detect falls in a live video stream (optional feature).

### 4. **`/Login` - Login Page**

   **Template:** `Login.html`

   The login page allows users to log in to the system if they have an account. 

### 5. **`/Mental` - Mental Health Detection Page**

   **Template:** `Mental.html`

   This page provides information or tools related to mental health detection (this part can be developed in future versions of the project).

### 6. **`/ModulesPage` - Modules Information Page**

   **Template:** `ModulesPage.html`

   This page contains details about different modules in the fall detection system, such as the YOLO object detection model, MoviNet model, etc.

### 7. **`/Report` - Report Generation Page**

   **Template:** `Report.html`

   This page allows users to generate reports based on the analysis of fall detection or other relevant data.

### 8. **`/SignUp` - Sign Up Page**

   **Template:** `SignUp.html`

   The sign-up page allows users to create a new account for the application.

### 9. **`/upload-video` - Video Upload Page**

   **Template:** `upload-video.html`

   This page allows users to upload a video file to be processed for fall detection. It supports multiple video formats such as `.mp4`, `.avi`, `.mov`, and `.webm`.

---

## Video Upload and Download Process

### Video Upload

1. **Upload Video:** On the `/upload-video` page, users can select and upload a video file. 
   - Supported video formats: `.mp4`, `.avi`, `.mov`, `.webm`
   
2. **Processing Video:** After uploading, the server processes the video to detect falls using the YOLOv8 model and the MoviNet model for fall prediction. The processed video is saved in the `static/processed` folder.

### Video Download

Once the video is processed, the user can download the processed video from the `static/processed` folder.

1. **Download Processed Video:** The processed video is available for download by clicking a link, which triggers the download from the `/download/<filename>` route.
   
   - The processed video will be saved in the format `.mp4` or `.avi`.

---

## How the Fall Detection Works

### 1. **Video Processing**
   - The user uploads a video using the `/upload-video` route.
   - The video is then processed frame by frame.
   - For each frame:
     - **Object Detection:** YOLOv8 detects objects, specifically persons, in the frame.
     - **Fall Detection:** The MoviNet model processes the frame to predict whether a fall has occurred based on the detected person.
     - If a fall is detected, the bounding box around the person turns red, and the text "FALL DETECTED" is displayed.

### 2. **Tracking and Updates**
   - After a fall is detected, the system keeps track of the person using the OpenCV tracker. It adjusts the bounding box if the person moves or if the tracking fails.

### 3. **Processed Video**
   - After all frames are processed, the video is saved in the `static/processed` folder.
   - The processed video can then be downloaded by the user from the `/download/<filename>` route.

---

## Dependencies

- Flask
- OpenCV (`cv2`)
- TensorFlow
- NumPy
- Matplotlib
- YOLOv8 (Ultralytics)

You can install these dependencies using:

```bash
pip install -r requirements.txt
```

---

## Conclusion

This Flask web application provides a comprehensive fall detection system that processes videos uploaded by the user, detects falls, and allows the user to download the processed video. The use of YOLO for object detection and MoviNet for fall prediction ensures high accuracy in fall detection, making it suitable for various safety applications.


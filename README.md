# Face Recognition-Based Attendance System

## Overview
In modern workplaces and institutions, attendance tracking remains a manual or semi-automated process prone to inefficiencies and manipulation. This project introduces a smart, contactless attendance system leveraging facial recognition to automate check-in and check-out processes. Built using Python, OpenCV, and dlib, the system ensures secure and efficient attendance logging while significantly reducing fraud and administrative effort.

This system captures real-time facial data via webcam, compares it against a pre-stored dataset hosted on Google Drive, and automatically updates an Excel-based attendance log with check-in/out times and hours worked.
## Flow Diagram
<p align="center">
  <img width="400" src="https://github.com/user-attachments/assets/9309832c-82e7-40fd-8083-226de18feba6" alt="Flow Diagram" />
</p>

## Recognition Model Details

### 1. Face Detection and Encoding
- Utilizes dlib's HOG-based detector or CNN-based detector.
- Each face is encoded using `dlib.face_recognition_model_v1`, producing a 128-d vector per face.

### 2. Dataset Management
- Pre-encoded face vectors and image datasets are stored on Google Drive.
- The system syncs local data with the cloud periodically or on demand.

### 3. Face Matching
- Computes Euclidean distances between live face vectors and dataset encodings.
- If the distance is under a threshold (e.g., 0.6), the face is considered a match.

### 4. Attendance Logging
- On successful match:
  - If no entry today → logs check-in time.
  - If already checked in → logs check-out and calculates hours worked.
- Records are appended to an Excel sheet, also synced with Google Drive.

## Deployment and Portability

- Designed to work on Windows/Linux.
- Operates in offline mode for face matching and logs locally.
- Syncs with cloud when Wi-Fi is available.
- Requires only a webcam and basic computing resources.

## Results

<p align="center">
  <img src="https://github.com/user-attachments/assets/6c365a23-9fa3-4890-949f-c19fd5845339" width="600"/>
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/db2adfe5-108b-48a9-8098-88b561ffb5ef" width="600"/>
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/f17161f0-3c18-4ec5-bb67-936dd85b8947" width="600"/>
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/2d2ed13d-870f-4150-847b-39ae2ee2db58" width="600"/>
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/d2d5665c-59bf-4934-84d6-693a2c81eb7b" width="600"/>
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/1fc9afbd-9235-4cfe-97ad-f4e59ec0a3c4" width="600"/>
</p>

## How to run
Clone this repo, head to the root directory, and create a [Python Virtual Environment](https://www.geeksforgeeks.org/python-virtual-environment/).
Then,install the required dependencies
```
 pip install -r requirements.txt
```
Make sure your webcam is connected and working, then run:
```
python download.py
```
This will launch a GUI that captures the user's face using the webcam Compares it with the pre-encoded dataset stored locally or on Google Drive. 
On a successful match:

If it's the first entry today → logs check-in time

If already checked in → logs check-out time and calculates hours worked


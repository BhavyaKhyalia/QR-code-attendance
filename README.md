# QR Code Attendance System

This project is a **QR Code-based Attendance System** that scans QR codes to log attendance and access control. The system uses OpenCV, PyZbar, and Google Colab to capture and decode QR codes, checks for authorized users, and logs attendance in a text file.

## Features

- Capture QR codes using a webcam or uploaded images.
- Decode QR codes to retrieve user information.
- Grant or deny access based on the QR code data.
- Log attendance with timestamps for authorized users.
- Displays QR code boundaries and polygons for visual confirmation.

## Prerequisites

The following libraries are required to run the project:

- OpenCV 4.6.0.66
- Matplotlib 3.7.1
- Numpy 1.25.0
- PyZbar
- LibZbar (for decoding QR codes)

## Installation

To install the required dependencies, run the following commands:

```bash
!pip install opencv-python==4.6.0.66
!pip install matplotlib==3.7.1
!pip install numpy==1.25.0
!pip install pyzbar
!apt-get install libzbar0
```

## How It Works

1. **QR Code Scanning:**
   - Use the webcam or an image file to capture a QR code.
   - The system decodes the QR code using PyZbar and OpenCV.
   
2. **Access Control:**
   - It checks if the decoded QR data matches any of the authorized users.
   - If the user is authorized, access is granted and attendance is logged with a timestamp.
   - If the user is unauthorized, access is denied.

3. **Log System:**
   - Attendance is logged into a file named `log.txt`, with entries containing the user's name and the time of access.
   - The system prevents logging the same user within a defined threshold time (`time_between_logs_th`).

## Usage

### Webcam Photo Capture

This function allows you to take a photo using your webcam and save it as `photo.jpg`:

```python
from IPython.display import display, Javascript
from google.colab.output import eval_js
from base64 import b64decode

def take_photo(filename='photo.jpg', quality=0.8):
    # Code for capturing a photo using the webcam
```

### QR Code Detection

The following code detects and processes QR codes:

```python
import cv2
from pyzbar.pyzbar import decode

img = cv2.imread('path/to/your/image.png')
qr_info = decode(img)

for qr in qr_info:
    data = qr.data
    print(data)
    # Draw rectangles and polygons around the QR code
```

### Attendance Logging

The attendance of authorized users is logged in `log.txt`:

```python
log_path = './log.txt'
authorized_users = ['Bhavya', 'Rahul', 'Raj']
if data.decode() in authorized_users:
    with open(log_path, 'a') as f:
        f.write('{},{}\n'.format(data.decode(), datetime.datetime.now()))
```

## Running in Google Colab

This project is compatible with Google Colab. Upload your images or capture photos using your webcam in Colab, and the system will process them accordingly.

## Demo

You can try out the project by following the Colab notebook:
[QR Code Attendance System Colab](https://colab.research.google.com/drive/1vLfNORLv0bZEdrko7IpHA3dAxPJ_P1Jg)

## Acknowledgments

- PyZbar for QR code decoding.
- OpenCV for image processing.
- Google Colab for providing a free cloud-based development environment.

Feel free to contribute to this project and enhance its features!

README — Quick setup guide(Raspberry Pi 3 & Licence Plate Detection project)

Summary (what we do)

- Install heavy system packages with apt (fast, prebuilt): OpenCV, Tesseract, system libs.
- Create a Python virtual environment (venv) that can access system packages.
- Install small Python packages with pip inside the venv (from requirements.txt).
- Clone the project, run capture / extraction / OCR scripts.
Important: Don’t try to pip install OpenCV/Tesseract on a Pi3 , that often triggers a long source build. Use apt for those.

Step 1: Update your system
sudo apt update && sudo apt upgrade -y

Step 2: Install System Packages 
sudo apt install -y \
  python3 python3-venv python3-pip \
  python3-opencv \
  tesseract-ocr libtesseract-dev \
  python3-matplotlib

Step 3: Create a virtual environment (Choose the name of venv, here the name is 'Plate_Detection')
python3 -m venv ~/Plate_Detection --system-site-packages
source ~/Plate_Detection/bin/activate

Step 4: Clone the GitHub Repository
cd ~
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>

Setp 5: Verify the folder Structure 
Plate_Detection/
│── CarPictures/                 # Stores input images
│── Database/Database.txt        # List of registered license plates
│── PlateExtraction.py           # Extracts number plate from image
│── OpticalCharacterRecognition.py # OCR logic with Tesseract
│── Imagecap.py              # Test with single photo
│── requirements.txt              # Required packages
│── README.md                    # Documentation

Step 6: Upgrade pip and install Python packages
python -m pip install --upgrade pip setuptools wheel
pip install -r requirements.txt

If you face issues with system packages (like Send2Trash), use:
pip install --break-system-packages -r requirements.txt
(or) remove the specific package
sudo apt remove python3-send2trash
sudo pip uninstall Send2Trash


Step 7: Verify installation
python3 -c "import cv2; print('OpenCV:', cv2.__version__)"
python3 -c "import pytesseract; print('Tesseract:', pytesseract.get_tesseract_version())"

Step 8: Make sure your camera is connected and accessible
ls /dev/video*


Step 9: Run the application
python3 Imagecap.py
(Note: Place the camera in steady position and capture the licence plate, then it will be verifyting the captured palte registered or not then returned the result)




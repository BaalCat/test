## 📖 Setup Guides

- [Linux Setup Guide](./test.md)


# 🛠️ BachelorGUI2025 – SubSea GUI System

A cross-platform graphical interface and backend system for processing and streaming media in real time using Python, OpenCV, .NET, and Node.js.

---

## 📖 Table of Contents

- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
  - [🐧 Linux (Ubuntu/Debian) Setup](#linux-ubuntudebian-setup)
  - [🪟 Windows Setup](#windows-setup)
- [Usage](#-usage)
- [License](#-license)

---

## 📦 Prerequisites

- Python 3.7
- Node.js (v18 or later)
- .NET SDK (v8.0 or later)
- CMake with GUI
- GStreamer and FFmpeg

---

## 🧰 Installation

<details id="linux-ubuntudebian-setup">
<summary><strong>🐧 Linux (Ubuntu/Debian) Setup</strong></summary>

---

### 1. Clone the Repository

```bash
git clone https://github.com/UiS-SubSea/your-repo-name.git
cd your-repo-name
2. Install Python and System Dependencies
bash
Copy
Edit
sudo apt update
sudo apt install -y software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt-get install python3.7 python3.7-venv python3.7-distutils python3.7-dev python3.7-numpy
sudo apt-get install libsrtp2-dev gcc g++
3. Install GUI, Media & Codec Dependencies
bash
Copy
Edit
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev
sudo apt-get install libgtk-3-dev libpng-dev libjpeg-dev libopenexr-dev libtiff-dev libwebp-dev
4. Setup Python Virtual Environment
bash
Copy
Edit
cd Backend
python3.7 -m venv myenv
source myenv/bin/activate
cd PythonScripts
pip install -r requirements.txt
5. Install GStreamer & FFmpeg
bash
Copy
Edit
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-base gstreamer1.0-plugins-good \
gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav libgstreamer1.0-dev ffmpeg
6. Compile OpenCV 4.7.0 Manually
bash
Copy
Edit
sudo apt-get install cmake cmake-qt-gui
mkdir ~/opencv_build && cd ~/opencv_build
git clone -b 4.7.0 https://github.com/opencv/opencv.git
git clone -b 4.7.0 https://github.com/opencv/opencv_contrib.git
cd opencv && mkdir build && cd build
Launch cmake-gui

Set source to opencv and build directory to opencv/build

Add entry:

OPENCV_EXTRA_MODULES_PATH → ../opencv_contrib/modules

Configure, then Generate

Build:

bash
Copy
Edit
make -j4
sudo make install
Copy OpenCV bindings to your virtual environment:

bash
Copy
Edit
cp -r cv2 ~/BachelorGUI2025/Backend/myenv/lib/site-packages/
Verify:

bash
Copy
Edit
python -c "import cv2; print(cv2.__version__)"
7. Install Node.js and .NET SDK
bash
Copy
Edit
sudo apt install nodejs npm
sudo apt install dotnet-sdk-8.0
</details>
<details id="windows-setup"> <summary><strong>🪟 Windows Setup</strong></summary>
Coming soon or paste your existing setup guide here using the same format.

</details>
🚀 Usage
📦 Backend
bash
Copy
Edit
cd Backend
dotnet restore
dotnet build
dotnet run
🌐 Frontend
In a separate terminal:

bash
Copy
Edit
cd GUI-Frontend
npm install
npm start

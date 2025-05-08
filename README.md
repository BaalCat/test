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

## 🧰 Setup Guides

<details>
<summary><strong>🔧 Linux (Ubuntu/Debian) Setup Guide</strong></summary>

### Linux (Ubuntu/Debian) Setup

1. Download the GUI project from the repository.

2. Open a terminal and run the following commands (Skip any step you've already completed):

   ```bash
   sudo apt update
   sudo apt install -y software-properties-common
   sudo add-apt-repository ppa:deadsnakes/ppa
   sudo apt update
   sudo apt-get install python3.7 python3.7-venv python3.7-distutils python3.7-dev python3.7-numpy
   sudo apt-get install libsrtp2-dev
   sudo apt-get install gcc g++
   ```

3. Install GTK, camera, and media support:

   ```bash
   sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev
   sudo apt-get install libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev
   sudo apt-get install libgtk-3-dev
   sudo apt-get install libpng-dev
   sudo apt-get install libjpeg-dev
   sudo apt-get install libopenexr-dev
   sudo apt-get install libtiff-dev
   sudo apt-get install libwebp-dev
   ```

4. Verify Python version:

   ```bash
   python3.7 --version
   ```

5. Navigate to the project backend:

   ```bash
   cd BachelorGUI2025/Backend
   ```

6. Create and activate a virtual environment:

   ```bash
   python3.7 -m venv myenv
   source myenv/bin/activate
   ```

7. Navigate to the Python scripts:

   ```bash
   cd PythonScripts
   ```

8. Install Python dependencies:

   ```bash
   pip install -r requirements.txt
   ```

9. Install GStreamer:

   ```bash
   sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-base \
   gstreamer1.0-plugins-good gstreamer1.0-plugins-bad \
   gstreamer1.0-plugins-ugly gstreamer1.0-libav \
   libgstreamer1.0-dev
   ```

10. Install FFmpeg:

    ```bash
    sudo apt install ffmpeg
    ```

11. Manually compile OpenCV:

    - Install CMake and CMake GUI:

      ```bash
      sudo apt-get install cmake
      sudo apt-get install cmake-qt-gui
      ```

    - To open CMake later:

      ```bash
      cmake-gui
      ```

    - Download and set up OpenCV 4.7.0 and Contrib:

      ```bash
      mkdir ~/opencv_build && cd ~/opencv_build
      git clone -b 4.7.0 https://github.com/opencv/opencv.git
      git clone -b 4.7.0 https://github.com/opencv/opencv_contrib.git
      cd opencv
      mkdir build && cd build
      ```

    - Open CMake GUI **from a terminal where the virtual environment is active**.

    - In CMake GUI:
        - Set the source code path to the `opencv` folder.
        - Set the build path to the `opencv/build` folder.
        - Add `OPENCV_EXTRA_MODULES_PATH` pointing to `opencv_contrib/modules`.

    - Click **Configure** and verify the GStreamer and Python fields are set correctly.

    > 🖼️ *Insert image here: opencv_linux2.png* (Example of correct CMake configuration)

    - Choose the generator (e.g., `Unix Makefiles`).

    - Build OpenCV:

      ```bash
      make -j4
      ```

    - Install OpenCV:

      ```bash
      sudo make install
      ```

    - Copy the `cv2` folder to your virtual environment:

      ```bash
      cp -r cv2 ~/BachelorGUI2025/Backend/myenv/lib/site-packages
      ```

    - Verify installation:

      ```bash
      python -c "import cv2; print(cv2.__version__)"
      ```

12. Install Node.js, npm, and .NET 8:

    ```bash
    sudo apt install nodejs npm
    sudo apt install dotnet-sdk-8.0
    ```

13. Build and run the backend:

    ```bash
    cd Backend
    dotnet restore
    dotnet build
    dotnet run
    ```

14. Start the frontend:

    ```bash
    cd ../GUI-Frontend
    npm i
    npm start
    ```

</details>

<details>
<summary><strong>🔧 Windows Setup Guide</strong></summary>

### Windows Setup

1. **Download the GUI project from the UiS SubSea repo on Github:**
    - Link: [Your Repo Link Here](https://github.com/UiS-SubSea/your-repo-name)

2. **Download Python version 3.7.0**
    - Visit the [Python 3.7.0 Release Page](https://www.python.org/downloads/release/python-370/)
    - Download the installer for your Windows version (e.g., *Windows x86-64 executable installer*)
    - Run the installer and **make sure to check** the “Add Python to PATH” option during installation

3. **Install NumPy in Python 3.7** (required for compiling OpenCV)

4. **Open the folder `BachelorGUI2025\Backend` in a terminal**

5. **Create a virtual environment:**
    ```bash
    python3.7 -m venv myenv
    ```

6. **Activate the virtual environment:**
    ```bash
    .\myenv\Scripts\activate
    ```
    To deactivate later:
    ```bash
    deactivate
    ```

7. **Navigate to the `PythonScripts` folder:**
    ```bash
    cd PythonScripts
    ```

8. **Install dependencies from `requirements.txt`:**
    ```bash
    pip install -r requirements.txt
    ```

9. **Manually compile OpenCV to support GStreamer:**

    - **Download and install CMake v4.0.0:**
        - [CMake Download Page](https://cmake.org/download/)
        - Select the Windows x64 Installer: `cmake-4.0.0-windows-x86_64.msi`
        - During installation, check the box to add CMake to system PATH

    - **Download OpenCV v4.7.0 and OpenCV Contrib**
        - Place them anywhere on your system
        - Inside the OpenCV folder, create a new folder named `build`

    - **Install GStreamer v1.24.12:**
        - [GStreamer 1.24.12 (Windows, MSVC)](https://gstreamer.freedesktop.org/data/pkg/windows/1.24.12/msvc/)
        - Download and install:
            - `gstreamer-1.0-msvc-x86_64-1.24.12.msi`
            - `gstreamer-1.0-devel-msvc-x86_64-1.24.12.msi`
        - Add the `GStreamer\bin` directory to your system PATH

    - **Install FFmpeg** from [FFmpeg Builds](https://www.gyan.dev/ffmpeg/builds/)

    - **Install Visual Studio 17 2022** from [Visual Studio Website](https://visualstudio.microsoft.com/)

    - **Compile OpenCV with CMake GUI:**
        1. Open CMake GUI
        2. Set:
            - Source folder: OpenCV root
            - Build folder: `build` folder you created
        3. Click `Configure`
        4. Select compiler: **Visual Studio 17**, click `Finish`
        5. After initial configuration:
            - In the `WITH` section, enable relevant options (e.g., `WITH_GSTREAMER`, `WITH_PYTHON`)
            - If `WITH_PYTHON` is missing, add it manually via `Add Entry`
        6. In the `BUILD` section, enable required modules
        7. In the `ENABLE` section, disable `ENABLE_SOLUTION_FOLDERS`
        8. Ensure GStreamer fields are filled (edit manually if necessary)
        9. Ensure Python fields are correctly set (ignore `PYTHON_DEBUG_LIBRARY`)
        10. Add `OPENCV_EXTRA_MODULES_PATH` (point to `opencv_contrib/modules`)
        11. Click `Configure` again. Confirm:
            - GStreamer shows `YES`
            - Python paths are correct
        12. Click `Generate` to create `OpenCV.sln`
        13. Click `Open Project` to launch in Visual Studio
        14. Set build type to `Release`
        15. Right-click the solution → `Build`
        16. After that, right-click `INSTALL` → `Build` again

    - **Copy the compiled OpenCV to your virtual environment:**
        - Copy the `cv2` folder to:
            ```
            BachelorGUI2025\Backend\myenv\Lib\site-packages
            ```

    - **Verify the OpenCV installation:**
        ```bash
        python -c "import cv2; print(cv2.__version__)"
        ```
        - If you see a version number, it worked!

10. **Install Node.js (v18), npm, and .NET (v8 or newer):**
    ```bash
    sudo apt install nodejs npm
    sudo apt install dotnet-sdk-8.0
    ```

11. **Restore and build the backend:**
    ```bash
    cd Backend
    dotnet restore
    dotnet build
    ```

12. **Run the backend:**
    ```bash
    dotnet run
    ```

13. **Start the frontend:**
    - Navigate to the `GUI-Frontend` folder
    - Run:
        ```bash
        npm i
        npm start
        ```
</details>


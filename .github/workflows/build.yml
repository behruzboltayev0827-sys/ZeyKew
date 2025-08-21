name: Build APK

on:
  push:
    branches: [ main ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Install dependencies
      run: |
        sudo apt update
        sudo apt install -y python3-pip python3-dev build-essential \
          git openjdk-17-jdk unzip libffi-dev libssl-dev \
          liblzma-dev zlib1g-dev

        pip install --upgrade pip
        pip install buildozer cython

    - name: Build APK
      run: |
        buildozer -v android debug

    - name: Upload APK
      uses: actions/upload-artifact@v3
      with:
        name: ZeyKew-APK
        path: bin/*.apk

# ADB Ultimate Transfer Tool V1.0 🚀

A robust, batch-script wrapper for Android ADB (Android Debug Bridge). This tool allows for high-speed wired file transfers without the "freezing" or "estimating time" issues common with standard Windows MTP (File Explorer).

**Version:** 1.0
**Status:** Stable

## Why use this?
- **Speed:** Utilizes the maximum bandwidth of your USB cable.
- **Stability:** Does not hang on folders containing thousands of small files (e.g., WhatsApp backups, DCIM).
- **Metadata:** Preserves original file timestamps (`-a` flag enabled).
- **Safety:** Includes connection "pulse checks" to prevent errors if the device disconnects during use.

## Features
- [x] **Auto-Detection:** Automatically checks for device connection and ADB authorization.
- [x] **Smart Menus:** Lists phone directories to help you find paths easily.
- [x] **Quote Handling:** Automatically strips quotes from PC paths (fixing "copy as path" errors).
- [x] **SD Card Support:** Dedicated modes for pulling from external storage.

## Prerequisites
1. **Enable USB Debugging** on your Android phone (Developer Options).
2. Download **SDK Platform Tools** from Google.

## Installation & Usage
1. Download `ADB-Transfer-Tool.bat` from this repository.
2. Place the file **inside** your platform-tools folder (the same folder where `adb.exe` is located).
3. Connect your phone via USB.
4. Double click `ADB-Transfer-Tool.bat`.

> **Note on SD Cards:** Android 11+ restricts write access to the SD card via ADB. This tool allows you to READ (pull) from the SD card easily. If writing (pushing) to the SD card fails, push to Internal Storage first and move the file using a file manager on your phone.

## Troubleshooting
If the tool says **"NO ACTIVE DEVICE DETECTED"**:
1. Ensure your screen is unlocked.
2. Check your phone for the "Allow USB Debugging?" popup.
3. Ensure your USB mode is **NOT** set to "File Transfer" (MTP can conflict with ADB). Set it to "Charging Only" or "No Data Transfer".

## License
MIT License
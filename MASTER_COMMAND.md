# ⚡ The Master Command Cheat Sheet

This document contains the raw ADB commands used by the ADB Ultimate Transfer Tool. You can use these manually in any terminal (CMD, PowerShell) if you prefer manual control over the automated menu.

## 🔰 Quick Legend

Before you type any command, understand these placeholders:

| Variable | Description |
|---------|-------------|
| /sdcard/ | The main folder of your phone's Internal Storage. |
| -a | A special flag we use to preserve file dates (so your photos don't all say "Created Today"). |
| "." | A shortcut meaning "Current Folder" on your PC. |
| %userprofile% | A shortcut for your PC's home folder (e.g., C:\Users\Name). |

---

## 1. Connection & Navigation

**Check if your phone is connected:**
```
adb devices -l
```

**See what folders are on your phone:**
```
adb shell ls -F /sdcard/
```

**Find your SD Card ID (Required for SD Card transfers):**
```
adb shell ls /storage/
```
(Look for a code like **1234-5678** — that is your SD Card ID)

---

## 2. EXPORT (Phone ➔ PC)

Copying files FROM your phone TO your computer.

### Option A: Backup a Specific Folder  
(Example: Backing up your Camera folder to your Desktop)
```
adb pull -a "/sdcard/DCIM/Camera" "%userprofile%\Desktop\Camera_Backup"
```

### Option B: Backup EVERYTHING (Internal Storage)  
(This takes a long time!)
```
adb pull -a "/sdcard/" "%userprofile%\Desktop\Full_Phone_Backup"
```

### Option C: Backup from SD Card  
(Replace **XXXX-XXXX** with your actual SD Card ID)
```
adb pull -a "/storage/XXXX-XXXX/DCIM" "%userprofile%\Desktop\SD_Card_Backup"
```

---

## 3. IMPORT (PC ➔ Phone)

Copying files FROM your computer TO your phone.

**Copy a file to your Phone's Download folder:**
```
adb push "C:\MyFiles\Movie.mkv" "/sdcard/Download/"
```

**Copy a whole folder to your Phone:**
```
adb push "C:\MyFiles\Music_Album" "/sdcard/Music/"
```

---

## ⚠️ Important Note on SD Cards (Android 11+)

Modern Android versions use Scoped Storage, which often prevents ADB from writing (Pushing) directly to the SD Card to prevent malware.

If `adb push` to SD Card fails:

1. Push the file to Internal Storage first:
```
adb push "C:\File.zip" "/sdcard/Download/"
```

2. Open a File Manager on your phone (like Google Files).

3. Move the file from Internal/Download to your SD Card manually.

**Note:** READING/Pulling from SD Card usually works fine on all versions.

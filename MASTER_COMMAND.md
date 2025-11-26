The "Master Command" Cheat Sheet

You asked for the specific commands. Note that for ADB, Speed is constant. Whether you transfer 1 file, 100 mixed folders, or the full storage, the command is exactly the same because ADB is recursive (it automatically grabs everything inside the target).

Legend:

    /sdcard/ = Phone Internal Storage.

    /storage/XXXX-XXXX/ = Your SD Card ID (User must find this).

    -a = Preserves file timestamp (Crucial for photos).

A. Transfer Phone → PC (Backup)

i. Phone Main Storage → PC
adb pull -a "/sdcard/YourSourceFolder" "C:\Your\PC\Destination"
(To pull Entire Internal Storage, replace source with just /sdcard/)

ii. Phone SD Card → PC
adb pull -a "/storage/XXXX-XXXX/YourSourceFolder" "C:\Your\PC\Destination"

B. Transfer PC → Phone (Restore/Copy)

i. PC → Phone Main Storage
adb push "C:\Your\PC\SourceFolder" "/sdcard/DestinationFolder"

ii. PC → Phone SD Card Warning: Modern Android (Android 11+) restricts writing to SD cards via ADB for security. It often fails with "Permission Denied." If it works, the command is:
adb push "C:\Your\PC\SourceFolder" "/storage/XXXX-XXXX/DestinationFolder"
(If this fails, the workaround is pushing to Internal Storage first, then using a File Manager app on the phone to move it to the SD card).
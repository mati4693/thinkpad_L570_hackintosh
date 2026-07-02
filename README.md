# thinkpad_L570_hackintosh

A functional EFI for booting hackintosh on Kaby Lake i5-7200U CPU found on Thinkpad L570 laptop.

# Info
I wanted to run Hackintosh on my personal laptop, the Thinkpad L570, while dual booting with Windows 11.</br>
I have successfully been able to run macOS 10.15 (Catalina), which is also the only one i have tried. I think it surely can run newer OS'es, but the CPU would have a hard time catching up.</br>

# Files
In the EFI folder, i have three different EFI's with different purposes.</br>
In the "hackintosh" folder, i have included all the tools and files i used to create the EFI's.</br>

# EFI explanations
L570_EFI: only macOS 10.15</br>
L570_EFI_no_acpi: macOS 10.15 where ACPI files load later, so other os'es (such as Windows 11) aren't disturbed</br>
L570_DUAL_EFI: the compounded EFI of Windows 11 EFI and macOS 10.15 EFI</br>
(L570_DUAL_EFI: run this command on windows host: "bcdedit /set {bootmgr} path \efi\boot\bootx64.efi" to tell windows where to boot from)</br>

# BIOS settings
(if setting not mentioned then leave unchanged)</br>
Secure Boot -> OFF</br>
TPM 2 -> ACTIVE</br>
Advanced/Boot options/Fast Boot -> OFF</br>
Advanced/System options/VTd -> OFF</br>

# Functionalities
BATTERY STATUS: YES</br>
WIFI: YES</br>
ETHERNET: YES</br>
BLUETOOTH: YES</br>
VOLUME: YES (even with the volume keys FN + F1, F2, F3)</br>
SPEAKERS: YES</br>
MICROPHONE: YES</br>
USB 3 PORTS: YES</br>
AUDIO JACK: YES</br>
HDMI: NOT TESTED</br>
DRM: NOT TESTED</br>
APPLE ID SERVICES (imessage, facetime): YES</br>
CAMERA: YES</br>
KEYBOARD: YES</br>
TRACKPAD: YES (gestures such as scrolling aren't supported)</br>
RTC: YES</br>
LAPTOP CLOSED: NO (only turns screen off, but doesnt logs out and go to sleep, when closing laptop)</br>

# Trackpad
The trackpad is an ALPS V8, but there arent any kexts supporting gestures and clicking simultaneously, it's only one of the functions.</br>
I tried my best to fix the trackpad, but this guy has also had great difficulty.</br>
https://github.com/leomenrex/Hackintosh-ThinkPad-L570/tree/main (you can translate his repo)</br>
(my repo and his repo are unrelated)</br>

# Keyboard
The Windows key is the equivalent of the Command key.</br>
The Alt key is the equivalent of the Option key</br>

# Upgrading to a newer macOS
If you want to use a newer macOS, then you would have to grab a newer version of AirportItlwm.kext, which is required for Wifi, matching your macOS.</br>

# Dual Booting on the same disk
If you're just running macOS alone, then you have to pick L570_EFI.</br>

If you're trying to dual boot Windows 11 and macOS, then you would need to pick L570_DUAL_EFI, which is a compounded version of the Windows 11 EFI and the macOS EFI.</br>
To prepare the Windows 11 system, you would have to run this command as admin: "bcdedit /set {bootmgr} path \efi\boot\bootx64.efi" to tell Windows where to boot from.</br>

If you want to boot macOS and a different OS (Windows 10 or Linux), then you need to grab the L570_EFI_no_acpi and merge the EFI of the other OS.</br>
If you're using Windows 10, then you would also have to run the aforementioned command: "bcdedit /set {bootmgr} path \efi\boot\bootx64.efi".</br>

When done installing both OS'es, change the config.plist (using OpenCore configurator on Mac) in the EFI partition accordingly: </br>
Misc -> Boot -> LauncherOption: Full</br>
This ensures better stability between Windows and macOS.</br>

One important note: ONE EFI partition has to be present on the disk, not two, even though there are two OS'es.</br>

# Installing Windows
Just use BootCamp (if using earlier macOS where BootCamp is still present) to install Windows 10, and afterwards upgrade to Windows 11 if needed.</br>

# Merging the EFI's
First mount the Windows EFI partition your system, so you can access it.</br>
Afterwards copy and paste the L570_EFI_no_acpi into the EFI partition, and ensure that duplicate/existing files are overwritten.</br>
This is important to ensure the "bootx64.efi" isn't the Windows version, but rather the OpenCore version.</br>
Now can just unmount the EFI.

# Conclusion
Just to state it, you're free to modify and improve these EFI's (try to improve trackpad functionality). You're allowed use these EFI's to your own extent. I don't need to be credited, but it would be nice. I won't be maintaining this repository any further.</br></br>
Cheers, Mati


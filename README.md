Simple bash script to automatically uninstall bloatware on android

### WARNING
For any package you uninstall make sure you check what it does, do not run this script if you don't know what are you doing. Follow this tutorial at your own risk

## Requirements
- Gnu/Linux machine
- Android Debug Bridge (ADB)
- Fastboot
- Usb cable to connect your phone to pc/laptop
- Enabled usb debugging on your phone

## Installation
      sudo apt update -y
      sudo apt install android-tools-adb android-tools-fastboot -y

## Usb debugging
- Settings > About Phone > Build Number (x7)
- Settings > System > Advanced > Developer Options > Enable > USB Debugging > Enable

## Usage
Clone the repo:
      
      git clone https://github.com/privacy-codes/Degoogle.git

Make it executable:
     
     chmod +x debloat.sh

List packages and put them in a file:
      
     adb shell pm list package --user 0 | grep <package> | cut -d ":" -f2 > filename.txt

Example:

     adb shell pm list package --user 0 | grep google | cut -d ":" -f2 > bloatware.txt

Output of bloatware.txt

    com.google.android.ext.services
	com.google.android.onetimeinitializer
	com.google.android.ext.shared
	com.google.android.overlay.gmsgsaconfig
	com.google.android.configupdater
	com.google.android.overlay.modules.permissioncontroller
	com.google.ar.lens
	com.google.android.marvin.talkback
	com.google.android.permissioncontroller
	com.google.android.setupwizard
	com.google.android.overlay.modules.ext.services
	com.google.android.apps.wellbeing
	com.google.android.overlay.gmsconfig
	com.google.android.modulemetadata
	com.google.android.webview
	com.google.android.syncadapters.contacts
	com.google.android.packageinstaller
	com.google.android.gms
	com.google.android.gsf
	com.google.android.tts
	com.google.android.partnersetup
	com.google.android.overlay.modules.permissioncontroller.forframework
	com.google.android.feedback
	com.google.android.printservice.recommendation
	com.google.android.syncadapters.calendar
	com.google.android.documentsui
	com.google.android.projection.gearhead
	com.google.android.apps.turbo
	com.google.android.gms.location.history
	com.google.android.apps.restore

Put packages you want to delete in bloatware.txt in this format

 	package1
 	package2
 	package3
      
Example
      
 	com.google.android.inputmethod.latin        
 	com.android.vending 		             
 	com.google.android.videos 	             
 	com.google.android.youtube

Execute the script:

      ./debloat


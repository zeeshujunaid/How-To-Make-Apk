HOW TO BUILD AND GENERATE AN APK FOR YOUR REACT NATIVE PROJECT

Follow these step-by-step instructions to generate an APK for your React Native project:

----------------------------Step 1: Install EAS CLI--------------------------------------

COMMAND[npm install -g eas-cli]

----------------------Step 2: Sign Up for an Expo Account----------------------------------

Go to the Expo website and create an account if you don’t already have one.

After signing up, log in to your account in the terminal using:

COMMAND[eas login]

-------------------Step 3: Build the App Bundle (.aab File)------------------------

Run the following command in the terminal from your project’s root directory:

COMMAND[eas build --platform android]

Follow the prompts to configure your build (you may need to set up credentials if it’s your first time).

---------------------------Step 4: Download the .aab File-----------------------------

After the build is complete, go to the Expo build page and find your project.

Download the .aab file for your project.

Rename the file to app.aab for simplicity.

------------------------------Step 5: Prepare the Files-------------------------

Create a new folder on your desktop.

Move the app.aab file into this folder.

----------------------------Step 6: Download BundleTool---------------------------

Download the BundleTool JAR file from the official GitHub releases page.

[https://github.com/google/bundletool/releases]

Place the downloaded bundletool-all-<version>.jar file in the same folder as your app.aab file.

---------------------Step 7: Build the APK from the .aab File-------------------------

Open the Command Prompt (Windows) or Terminal (macOS/Linux).

Navigate to the folder containing your files:

cd desktop
cd foldername

Run the following command to build the APK:

java -jar bundletool-all-1.17.2.jar build-apks --bundle=app.aab --output=newapp.apks --mode=universal --ks newapp-release-key.jks --ks-key-alias newapp-key-alias --ks-pass pass:newapp --key-pass pass:newapp

NOTE:MAKE SURE TO CHANGE THE BUNDELTOOL VERSION TO WHICH YOU DOWNLOADED 

NOTE:MAKE SURE TO CHANGE THE OUTPUT= TO YOUR APP NAME .APKS 

NOTE:CHNAGE THE --KS NEWAPP ANME TO YOUR APP NAME SAME TO EVERY WHERE IN COMMAND CHANGE NEWAPP TO YOUR APP NAME


Note: Ensure the version of bundletool matches the one you downloaded. Replace bundletool-all-1.17.2.jar with the actual file name.

----------------------------------Step 8: Extract the APK----------------------------

To extract the APK from the .apks file, run:

java -jar bundletool-all-1.17.2.jar extract-apks --apks=newapp.apks --output=output_folder

NOTE:CHANGE NEWAPP TO YOUR APP NAME WHICH YOU ENTERED IN UPPER COMMAND 

This will create an output_folder containing the universal APK (universal.apk).

----------------------------Step 9: Install and Test the APK----------------------

You can install the APK on a device using:

adb install path_to_universal.apk

Replace path_to_universal.apk with the actual path to the universal.apk file.

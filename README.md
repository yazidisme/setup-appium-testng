## Setup Android Test Automation using **Appium** and **TestNG** with Java Language in MacOS

#### 1. Java Development Kit (JDK)
* [Download](https://www.oracle.com/technetwork/java/javase/downloads/index.html) and [install](https://docs.oracle.com/javase/10/install/installation-jdk-and-jre-macos.htm#JSJIG-GUID-F575EB4A-70D3-4AB4-A20E-DBE95171AB5F) *JDK*
* Type `java -version` in your *Terminal* to verify installation and find out your *java version*
* See the output of *[java version](https://prnt.sc/p8zd7s)*

#### 2. Android Studio
* Download and install *[Android Studio](https://developer.android.com/studio)*
* Create android emulator using *[AVD Manager](https://developer.android.com/studio/run/managing-avds#createavd)*
* [Run and stop](https://developer.android.com/studio/run/managing-avds#emulator) your emulator
* See [android emulator sample](https://prnt.sc/p8zeq8)

#### 3. Homebrew
* Install *[Homebrew](https://brew.sh/)* using *Terminal* and enter the following command
    ```sh
    $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    ```
* Follow the instructions until *Homebrew* installing success
* Type `brew --version` to find out your *homebrew version*
* See the output of *[homebrew version](https://prnt.sc/p8zgxb)*

#### 4. Node.js
* Install *[node.js](https://nodejs.org/)* using *brew*, type `brew install node` in your *Terminal*
* Wait until *node.js* installing success
* Type `node --version` to find out your *node version*
* Type `npm --version` to find out your *npm version*
* See the output of *[node and npm version](https://prnt.sc/p8zkyz)*

#### 5. Setting the system variables
* Create and open your *.bash_profile* using *Terminal*
    ```sh
    $ cd ~/
    $ touch .bash_profile
    $ open -e .bash_profile
    ```
* Set the *Java* and *Android SDK* paths in *bash_profile* file
    ```
    export JAVA_HOME=/Library/Java/JavaVirtualMachines/JDK_VERSION_FOLDER/Contents/Home
    export ANDROID_HOME=/Users/SOME_FOLDERS/Library/Android/sdk
    export PATH=$PATH:$ANDROID_HOME/tools
    export PATH=$PATH:$ANDROID_HOME/tools/bin
    export PATH=$PATH/:$ANDROID_HOME/platform-tools
    export PATH=$PATH:$JAVA_HOME/bin
    ```
* Save and exit your *bash_profile*
* Run emulator or connecting your real device
* Type `adb devices` in *Terminal* to find out name and connection of your devices
* See the output of [list of devices](https://prnt.sc/p8sfi7)

#### 6. Appium
* Install *[Appium](http://appium.io/)* with *npm* in your *Terminal* using the following command
    ```sh
    $ npm install -g appium
    ```
* To ensure that we are ready to use *Appium*, you can run the following command
    ```sh
    $ appium-doctor
    ```
* Minimum requirements for android testing from appium-doctor
    * HOME is set to: /Users/**some_folders** ✔ 
    * ANDROID_HOME is set to: /Users/**some_folders**/Library/Android/sdk ✔ 
    * JAVA_HOME is set to: /Library/Java/JavaVirtualMachines/**jdk_version_folder**/Contents/Home ✔
    * adb exists at: /Users/**some_folders**/Library/Android/sdk/platform-tools/adb ✔
    * android exists at: /Users/**some_folders**/Library/Android/sdk/tools/android ✔
    * emulator exists at: /Users/**some_folders**/Library/Android/sdk/tools/emulator ✔
    * Bin directory of $JAVA_HOME is set ✔ 

#### 7. JAR files
* Download *[Selenium](https://www.seleniumhq.org/)* library
    * Go to *[Selenium Standalone Server](https://prnt.sc/p8o4a3)* section
    * Go to *[Selenium Client and Webdriver Language Bindings](https://prnt.sc/p8o509)* section
* Download *[Appium Java Client](https://github.com/appium/java-client)*
    * Go to [releases](https://prnt.sc/p8o7kk) menu
    * Download [new version](https://prnt.sc/p8o7xw) of *Java Client*
* Download *[Gson](https://github.com/google/gson)*
    * Go to [releases](https://prnt.sc/p8oc4o) menu
    * Download [new version](https://prnt.sc/p8ocfo) of *Gson*
* Unzip all of them, then move to single folder like [this](https://prnt.sc/p8rtba)

#### 8. Eclipse
* [Download](https://www.eclipse.org/) and [install](https://www.eclipse.org/downloads/packages/installer) *Eclipse IDE* on your macOS
* Launch the *Eclipse IDE*
* Create a [new java project](https://www.wikihow.com/Create-a-New-Java-Project-in-Eclipse) in *Eclipse*
* In java setting (create new project), click [libraries tab](https://prnt.sc/p930k1)
* Add all [external jar](https://prnt.sc/p931ea) files
    * gson.jar
    * java-client.jar
    * selenium-server-standalone.jar
    * selenium-java.jar or client-combined.jar
    * [Add to attachment](https://prnt.sc/p8rzth) selenium-java-sources.jar or client-combined-sources.jar in selenium-java.jar
* Finish

#### 9. TestNG
* [Download](https://testng.org/doc/download.html) and install *[TestNG](https://testng.org/)* in *Eclipse IDE* plug-in section, see [install from update site](https://prnt.sc/p8s46r)
* After success installing *TestNG*, restart your *Eclipse IDE*



##### Finally...
##### We are ready to write **Appium** test code
* See the sample of [java project](https://prnt.sc/p93bpc)
* Before execute your android tests, device must be [connected with *adb devices*](https://prnt.sc/p8sfi7) and *Appium* must be [opened in your *Terminal*](https://prnt.sc/p8smzt).
* Find out the app package and app activity in Terminal using the following command
    ```sh
    $ adb shell "dumpsys window windows | grep -E 'mCurrentFocus|mFocusApp'"
    ```
* See the [output result](https://prnt.sc/p8stgo), there are `com.google.android.youtube` as app package and `com.google.android.apps.youtube.app.WatchWhileActivity` as app activity
* Finding locators using `uiautomatorviewer` from *Android Studio*, type the following command in *Terminal*
    ```sh
    $ uiautomatorviewer
    ```
* See the [uiautomatorviewer](https://prnt.sc/p9435x)

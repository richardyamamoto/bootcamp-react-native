# Briefing
This repository tends to be auxiliar material for consult, the application builded here points to be a studying case. So prepare a good coffee and here we go!

# React Native Installation
All this information was extracted from [Rockeseat](https://docs.rocketseat.dev/ambiente-react-native/android/linux), we are using Linux Mint 19.1 (Tessa).

### Installing cURL
Just check if you already have this dependencie

`sudo apt-get install curl`

### Installing NodeJS
Using cURL we are going to install NodeJS

`curl -sL https://deb.nodesource.com/setup_10.x | sudo bash -`

`sudo apt install nodejs`

### Installing React Native CLI
With this we will be abled to run react-native on Command Line

_If you are using npm_

`sudo npm install -g react-native-cli`

_or using yarn_

`yarn global add react-native-cli`

### Installing JDK (Java Development Kit)
It's indispensable that you install the 8.0 version of JDK

```bash
sudo apt-get repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-8-jdk
```

**Note:**
If you have already installed another version of JDK, run the following command on bash, and select the 8.0 version manually

`sudo update-alternatives --config java`

After that, to make sure that you choose the right version

`java -version`

### Installing Graphics Libraries
In most cases we have to install 32bit version libs for linux emulate our project

`sudo apt-get install gcc-multilib lib32z1 lib32stdc++6`

---

# Android Studio
If you reached through here, it means that you really want to study, so let's install the Android Studio Command line tools,

**Note:** 
We are going install only the Command Line Tools.

[Link to download](https://developer.android.com/studio/#downloads)

After download the `.zip` file, we have to unzip it inside a directory, we commonly use `~/Android/Sdk`

**Note:**
Extract the whole folder:`tools` inside `~/Android/Sdk`

### Setting Environments Variables
If you are using Linux Mint like me, go to your folder `~/home/<your_user>`

Usually there you can find the `.bash_profile`, `.profile`, `.zshrc` or `.bashrc`. If none of these files exists, just create a `.bash_profile` inside your user folder.

Now open the file with you favorite text editor (I'm using Visual Studio Code), and paste the following lines inside

```
export ANDROID_HOME=~/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/platform-tools
```
Now open your terminal and execute the command

`~/Android/Sdk/tools/bin/sdkmanager "platform-tools" "platforms;android-27" "build-tools;27.0.3"`

**Note:**
You will need to accept all the licences typing `y`

# Installing the Emulator Genymotion

First of all, we have to install the VirtualBox, because Geny uses it as backend. So let's get started.

### Installing Virtual Box
If you are using Linux like me, the easiest way that I found was installing from the Official Linux Repositories, but I'm leaving a guide for other alternatives for installation [Guide Link](https://computingforgeeks.com/install-virtualbox-on-kali-linux-linux-mint/)

If everythings went fine, you can procced to the next step

### Installing Genymotion
Genymotion is a simple and stable android emulator, there are another alternatives on market.
First things first,to download it you'll have to create an account, after that download and install the emulator.[Download Link](https://www.genymotion.com/fun-zone/).

**Note:**
The downloaded file is a binary, so you're going to take this procedure:

1.  Find the directory that you downloaded the binary file
2.  Open your terminal and run `sudo chmod +x ./<file_name>`
  - Don't forget to change the `<file_name.bin>` to the downloaded file name with extension
3.  Executing this code give the file the permission to execute, now to install run `sudo ./<file_name.bin>`
  - Don't forget again to change the `<file_name.bin>`...
4.  Uff!!! Now you can drink your Coffee.

From here you are able to open your new Emulator

### Setting up Genymotion
Drink a little more coffee and let's do it.

- Open Genymotion
- Go to Settings/Preferences
  - It will change between versions
- Inside Settings, search for Account and login with your creadentials. [Genymotion](https://www.genymotion.com/fun-zone/).
- Still in Setting, search for ADB, and go to the option `Use custom Android SDK tool`
  - Remember the directory that you extracted the Android Studio command line tools 
  [To refresh you memory](https://github.com/richardyamamoto/react-native/blob/master/README.md#android-studio)
- Close Settings and to the next step.

### Installing devices template
On Genymotion upper left side, there is a search bar, find the model device of you preference and install it.

After installed the device template, try to run it, if everthing works fine, you are a lucky guy, just jump the next step.

### Virtualization Error
If you are here, you are not so lucky like me.

The virtualization error occurs because of a BIOS configuration. Restart your computer, and inside your BIOS and find somethings like Virtualization, and enable it. Shutdown your computer and turn it on again. Try to run your device template on Genymotion again. If everything works, keep going, you're almost done.

### Connecting your device with ADB
Now as the tittle says, we are going to connect your emulated device with ADB (Android Debug Bridge). First of all, open you terminal and run 

`adb connect <emulated_device_ip>:5555`

**Note:**
To get your emulated device IP, just strech the window of the emulator and Voilà, there it is. Don't forget to replace the `<emulated_device_ip>` with your IP.

To make sure that your device is connected, run `adb devices`, your device must be there in the list.

[Annotations]()


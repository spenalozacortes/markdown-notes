# Introduction to Appium and course plan

## Course agenda

**What is Appium?**
Appium is open-source mobile automation tool for testing native apps (Android & iOS) and mobile browsers.

Appium internally uses WebDriver Json Wire (which Selenium does) to test the apps. So it is just like Selenium but for mobile.

## Appium features

- Open source mobile automation tool
- The only cross platform test supporting tool
- Works for native, hybrid and mobile web apps
- Supports WebDriver API - Selenium family!

**Supported platforms**

- iOS
- Android
- Firefox OS

You can write the code in any language supported by WebDriver.

Java, C#, JavaScript, Python, Ruby

## Appium internal architecture

![[Pasted image 20240305111124.png]]

# Appium installation instructions for Windows & Mac

## Download Java, Android Studio & Node softwares for Appium setup

Install JDK, Android Studio, Node.js

## Set environment variable paths of all softwares in Windows

`ANDROID_HOME`

```
C:\Users\Stephan\AppData\Local\Android\Sdk
```

Android Studio -> Tools -> SDK Manager -> SDK Tools -> Hide Obsolete Packages -> Android SDK Tools (Obsolete)

`PATH`

```
C:\Users\Stephan\AppData\Local\Android\Sdk\tools
```

```
C:\Users\Stephan\AppData\Local\Android\Sdk\tools\bin
```

```
C:\Users\Stephan\AppData\Local\Android\Sdk\platform-tools
```

`NODE_HOME`

```
C:\Program Files\nodejs
```

`PATH`

```
C:\Program Files\nodejs\node_modules\npm\bin
```

## Set environment variable paths of all softwares in Mac

```zsh
vi ~/.bash_profile
```

```
export JAVA_HOME=$(/usr/libexec/java_home)
export ANDROID_HOME=/users/Stephan/Library/Android/sdk
export PATH=$PATH:/usr/local/bin:
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/emulator
```

```zsh
source ~/.bash_profile
```

## Configure Android virtual device/emulator and install Appium Server

Android Studio -> Device Manager

```shell
npm install -g appium@next
```

```shell
appium
```

## Setting up Appium Maven project with Java client dependencies

Maven Repository -> Appium -> Java Client

# Getting started with mobile testing using Appium code

## What is UIAutomator and creating UIAutomator object to define capabilities

UIAutomator is a UI testing framework introduced by Google to facilitate automation on an Android device or emulator.

Appium leverages this UIAutomator with its own wrapper and came up with UIAutomator2 driver to automate Android apps.

```shell
appium driver list
```

```
appium driver install uiautomator2
```

## How to start and stop Appium server programmatically using AppiumServiceBuilder




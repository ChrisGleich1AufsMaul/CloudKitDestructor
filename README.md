# ☁️ CloudKitDestructor

**CloudKitDestructor** is a jailbreak tweak for iOS that lets users control whether `ADCCloudKitManager` is initialized when an app launches.  
It offers the ability to block CloudKit/iCloud behavior at runtime, without modifying the app itself.

---

## 🔧 Features
  - The `-init` method of `ADCCloudKitManager` is blocked
  - The manager is **not initialized**, effectively disabling CloudKit
---

## 🧠 Purpose

Many iOS apps (especially internal or Apple apps) automatically load `ADCCloudKitManager` to enable CloudKit or iCloud syncing.  
This tweak allows you to prevent this from happening — useful for:

- Privacy testing
- Installing App with private developer account
- Debugging app behavior without iCloud  
- Preventing crashes or unwanted cloud access

---

## ⚙️ Installation

1. Build the tweak using [Theos](https://theos.dev):

   ```bash
   make clean package
Transfer and install the .deb package on your jailbroken device:

2. bash
- scp ./packages/*.deb root@<device-ip>:/var/mobile/
- ssh root@<device-ip>
- dpkg -i /var/mobile/*.deb
- killall -9 SpringBoard
- 
🧩 Sample Code
%hook ADCCloudKitManager

   ```objc
  - (id)init {
          NSLog(@"ADCCloudKitManager blocked.");
          return nil;
  }

  %end
   
## 📋 Requirements
- Jailbroken iOS device (iOS 13 or later recommended)
- Theos installed on your development machine
- The target app uses ADCCloudKitManager

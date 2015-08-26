---
layout: post
title: Android Studio
type: note
excerpt: 下午搞了Android Studio頗久，就是沒辦法將手機連接上我的ubuntu...
---

Android Studio安裝於Ubuntu上之紀錄
======================

　　剛開始在<a href="www.udacity.com">Udacity</a>學習Android，課程名稱為Android Development for Beginners，一整個下午課程到了安裝Android studio的步驟...

1. 開啟terminal -> `$ java -version` -> 若1.x.y.z的x大於等於7 -> 跳至步驟3
2. 安裝<a href="http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html">Java Development Kit (JDK)</a>
3. 安裝Android Studio   **若為Ubuntu系統，則需先進行預處理**

　　來自<a href="http://stackoverflow.com/questions/17033726/android-studio-error-after-studio-sh">Stackoverflow</a>的支援

> * Install JDK -- sudo apt-get install openjdk-7-jdk
> * Environment Variable -- sudo nano /etc/environment adding the following line:
> * JAVA\_HOME=/usr/lib/jvm/java-... ( 可以ls看看Java是哪個版本 )
> * <del>Reboot</del>, and Android Studio starts up. (I had added also a link to studio.sh to the main menu).

　　　　註：關於main menu的使用方法可以參照<a href="http://stepinto-ubuntu.blogspot.tw/2014/05/ubuntugoogle-android-studio.html">這裡</a>

--------------------------
　　看似安裝上去了！但...
　　連接完後，便搞了個Hello world的程式，想run到sony手機上，卻發現...在名單裡找不到自己的手機，只會出現一個包含NULL的手機代碼QQ找了老半天，原來是需要做這兩件事：

+ 按照<a href="http://developer.android.com/tools/device.html">Android Developer</a>上的指示

> 1. Log in as root and create this file: /etc/udev/rules.d/51-android.rules. And use this format to add each vendor to the file: `SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", MODE="0666", GROUP="plugdev" `　　　("0bb4"需換成網頁下方的手機廠商代碼)
> 2. Now execute:
>   `chmod a+r /etc/udev/rules.d/51-android.rules`

+ 如果到這裡，你可以在名單中發現自己的手機，那麼恭喜你！！如果不行，很可能是沒有做個步驟 => 將自己手機上的**「USB連線」**修改成**媒體裝置(MTP)**

  (來源網頁：<a href="https://stackoverflow.com/questions/25614067/android-studio-recognizes-physical-device-as-null/25628891#25628891">Stackoverflow</a>)

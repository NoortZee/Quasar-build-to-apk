# Quasar-build-to-apk


# Windows

### Run the following commands in the root folder of your app

Install the latest cordova release
```batch
npm install -g cordova
```
Install cordova dependencies in your app
```batch
quasar mode add cordova
```
Change to cordova folder
```batch
cd src-cordova
```
Install Android platform
```batch
cordova platform add android
```
Go back to the root folder
```batch
cd..
```
Build your app
```batch
quasar build -m cordova -T android
```
Change to cordova folder again
```batch
cd src-cordova
```
Build the apk
```batch
cordova build android
```

Дальше берём и скачиваем Android studio чтобы не ебаться с андроид сдк

После чего открываем проект в андройд студио и пытаемся выполнить следущую команду:

```batch
quasar build -m android -- "--" --packageType=bundle
```

На что ide говорит нам: "Сосааать! Нет переменных"

"Checking Java JDK and Android SDK versions
ANDROID_HOME=undefined (recommended setting)
ANDROID_SDK_ROOT=undefined (DEPRECATED)
Using Android SDK: ______________
Could not find an installed version of Gradle either in Android Studio,
or on your system to install the gradle wrapper. Please include gradle
in your path, or install Android Studio
"

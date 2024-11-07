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

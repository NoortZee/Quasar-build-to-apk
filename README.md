# Quasar-build-to-apk


## For Windows (скоро и на линукс запилю)

### Run the following commands in the root folder of your app


```batch
npm install -g cordova
```

```batch
quasar mode add cordova
```

```batch
cd src-cordova
```

```batch
cordova platform add android
```

```batch
cd..
```

```batch
quasar build -m cordova -T android
```

```batch
cd src-cordova
```

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

Дальше ставим Java JDK (в основном нас интересует как раз эта переменная ибо мы скачали Android studio и не надо докачивать отдельно андроид сдк, как делают в прикрепленном ниже гайде) и ебемся с путями в переменных
 так как без этого никуда (https://www.tutorials24x7.com/android/how-to-install-android-sdk-tools-on-windows)

Не забываем юзать -v для проверки установки а также переменные можно задать в консоли используя например
```bash
setx PATH "%PATH%;%GRADLE_HOME%\bin"
```

После этого нужно будет скачать ебаный Gradle через cmd от имени админа
Но поскольку это какая то залупа нам придется сначала поставить choco


```batch
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```
```batch
choco install gradle
```

```batch
gradle -v
```

После этого заходим в терминал андроид студио и вводим такие команды.
Это нужно потому что ебаные переменные окружения установлены неправильно для текущей сессии.

 ```batch
$env:GRADLE_HOME = "C:\Gradle\gradle-8.10.2"
$env:PATH += ";$env:GRADLE_HOME\bin"
```
 ```batch
gradle -v
```

После того как версия показалась пересоздаем мусор:

```bash
cordova platform rm android
cordova platform add android
```

Дальше билдим и молимся

```bash
 quasar build -m cordova -T android -- --debug --packageType=apk
```

И если апк сгенерировался по указанному пути, например:  C:\Users\SystemX\Downloads\quasar-project\quasar-project\dist
Идем пить пивас или что покрепче (после тестирования само собой)


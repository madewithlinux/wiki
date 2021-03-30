# phonk

https://github.com/victordiaz/phonk

a great app for playing around with peripherals and stuff on an android device

## TODO: add a send bytes function for BLE devices

first: get a build environment setup

- [x] setup phonk build env [ref](https://github.com/victordiaz/phonk#compile-it-yourself)
```bash
mkdir phonk_project
cd phonk_project
git clone git@github.com:victordiaz/PHONK.git          phonk
git clone git@github.com:victordiaz/PHONK-editor.git   phonk-editor
git clone git@github.com:victordiaz/PHONK-examples.git phonk-examples

(cd phonk-examples/ && npm run cleanAndDeploy)

(cd phonk-editor/ && npm install)
(cd phonk-editor/ && npm run buildAndDeploy)
```

- [x] install android studio (using jetbrains toolbox, apparently)
- [x] make a signing.properties file (or, rather, just ignore it)
  * [ref](https://developer.android.com/studio/publish/app-signing#generate-key)
  - [x] comment out the contents of signingConfigs releaseConfig in build.gradle (temporarily)
  - [x] build the project
  - [x] Build > Generate Signed Bundle/APK
    - [x] install and accept license agreements for: `build-tools;29.0.2 Android SDK Build-Tools 29.0.2`
    - [x] also, install sdk 28, because my phone is android version 9

- [x] add `writeBytes()` method to `PBluetoothLEClient`
- [ ] build: `assembleRelease` in gradle in android studio?





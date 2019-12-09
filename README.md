#README

Tutorial from this site
https://medium.com/@t1tan1um/fcm-integration-for-cordova-hybrid-apps-c679f5fc1988

Steps:
1. cordova create pushSample
2. cd pushSample
3. cordova platform add android
4. cordova plugin add cordova-plugin-fcm

bug:
The "chunk" argument must be one of type string or Buffer

Solution:
There is a bug in the plugin, to solve this: go to:

plugins/cordova-plugin-fcm/scripts/fcm_config_files_process.js

Now change the file like this:

// change
var strings = fs.readFileSync("platforms/android/res/values/strings.xml").toString();
// to
var strings = fs.readFileSync("platforms/android/app/src/main/res/values/strings.xml").toString();

// AND

//change
fs.writeFileSync("platforms/android/res/values/strings.xml", strings);

//to
fs.writeFileSync("platforms/android/app/src/main/res/values/strings.xml", strings);
After that, copy the google-services.json file to the following directories:

platforms/android/google-services.json
platforms/android/app/google-services.json
For more information, you can check this bug here

Final Notes:
Extremely buggy.
Can't get it to work. Will try other methods

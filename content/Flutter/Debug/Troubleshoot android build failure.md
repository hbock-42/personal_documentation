---
creation date: 2023-12-15 15:23
tags:
  - flutter
  - android
  - documentation
---
# Hard clean
Due to caching, gradle may be using an older dependency before you updated. 
To start clean:

1. delete the ~/.gradle/cache directory
2. delete the android/.gradle directory (in flutter project)
3. delete the project_dir/build dir (in flutter project)
4. ensure the `android/gradle/gradle-wrapper.properies` has the correct `distributionUrl` (currently `distributionUrl=https\://services.gradle.org/distributions/gradle-7.4-bin.zip`)
5. from project_dir do `flutter build apk`

NOTE: your dependencies may need to be updated if their `com.android.tools.build:gradle` version is too old. Alternatively, both the kotlin and `tools:gradle` versions can be downgraded to compatible version that match metadata (although Android Studio will warn for that not matching the IDE Kotlin version)

explanations: https://stackoverflow.com/a/74425347/9798865
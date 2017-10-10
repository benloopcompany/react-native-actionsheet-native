# React Native ActionSheet

React Native ActionSheet is a JavaScript library for [React Native](https://facebook.github.io/react-native/) that implements AcionSheet for Android. Its equivalent of ActionSheetIOS which is part of React Native.

For implementation the Android version I used [android-ActionSheet](https://github.com/baoyongzhang/android-ActionSheet).

## Requirements

- React Native >= 0.40.0
- Android

## Installing React Native ActionSheet

```bash
npm install react-native-actionsheet-native --save
# OR
yarn add react-native-actionsheet-native
```

## Preparing

### React native >= 0.40.0

You can run inside of your project folder the next command:

```bash
react-native link react-native-actionsheet-native
```

### React native >= 0.33.0 AND < 0.40.0

- In `android/setting.gradle`

```gradle
...
include ':react-native-actionsheet-native', ':app'
project(':react-native-actionsheet-native').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-actionsheet-native/android')
```

- In `android/app/build.gradle`

```gradle
apply plugin: "com.android.application"
...
dependencies {
  ...
  compile project(":react-native-actionsheet") // <--- add this
  ...
}
```

- Register Module (in MainActivity.java)

```java
import com.slowpath.actionsheet.ActionSheetPackage;  // <--- import and this

public class MyApplication extends Application implements ReactApplication {

  ......

  @Override
  protected List<ReactPackage> getPackages() {
    return Arrays.asList(
      new ActionSheetPackage(), // <------ add this line to you application
      new MainReactPackage());
  }

  ......

}
```

### Updated your MainActivity

Now, you need to update your MainActivity. The MainActivity should extends `ReactFragmentActivity` for working with this library.

```java
public class MainActivity extends ReactFragmentActivity {
  ...
}
```

# Usage

From your JS files for both iOS and Android:

```javascript
import ActionSheet from 'react-native-actionsheet-native';

ActionSheet.showActionSheetWithOptions({
  options: ['Disconnect', 'Cancel'],
  cancelButtonIndex: 1
},
(buttonIndex) => {
  const { dispatch } = this.props;
  if (buttonIndex === 0) {
    // Do something.
  }
});
```

# Customization of Android action sheet

If you want to customize view of Android ActionSheet, you will need to read [this article](https://github.com/baoyongzhang/android-ActionSheet#style)

## License

React Native ActionSheet is BSD-licensed.

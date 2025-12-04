# React Native CLI Guide (No Expo)

## Quick Start Commands

```bash
# Create new app
npx react-native init MyApp

# Run on Android
cd MyApp && npx react-native run-android

# Run on iOS
cd MyApp && npx react-native run-ios
```

## Dependencies for Navigation

```bash
npm install @react-navigation/native @react-navigation/native-stack react-native-screens react-native-safe-area-context

# iOS: Install pods after adding navigation
cd ios && pod install && cd ..
```

## App Structure with 2 Screens

### App.js
```jsx
import React from 'react';
import {NavigationContainer} from '@react-navigation/native';
import {createNativeStackNavigator} from '@react-navigation/native-stack';
import HomeScreen from './src/screens/HomeScreen';
import DetailsScreen from './src/screens/DetailsScreen';

const Stack = createNativeStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Home">
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="Details" component={DetailsScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

### src/screens/HomeScreen.js
```jsx
import React from 'react';
import {View, Text, Button, StyleSheet} from 'react-native';

export default function HomeScreen({navigation}) {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>Home Screen</Text>
      <Button
        title="Go to Details"
        onPress={() => navigation.navigate('Details')}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {flex: 1, alignItems: 'center', justifyContent: 'center'},
  title: {fontSize: 24, marginBottom: 20},
});
```

### src/screens/DetailsScreen.js
```jsx
import React from 'react';
import {View, Text, Button, StyleSheet} from 'react-native';

export default function DetailsScreen({navigation}) {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>Details Screen</Text>
      <Button title="Go Back" onPress={() => navigation.goBack()} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {flex: 1, alignItems: 'center', justifyContent: 'center'},
  title: {fontSize: 24, marginBottom: 20},
});
```

## Project Structure
```
MyApp/
├── App.js
├── src/
│   └── screens/
│       ├── HomeScreen.js
│       └── DetailsScreen.js
├── android/
├── ios/
└── package.json
```

## Prerequisites
- Node.js 18+
- JDK 11 or 17 (Android)
- Android Studio + SDK
- Xcode (iOS/macOS only)
- CocoaPods (`sudo gem install cocoapods`)

## iOS Setup
```bash
cd ios && pod install && cd ..
```
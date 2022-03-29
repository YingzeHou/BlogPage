# ReactNative

## Installation

Install Expo: `npm install expo-cli --global`

Create & Run:&#x20;

`expo init my-new-project`

`cd my-new-project`

`expo start`

## Difference

#### Core component:

1. div --> View
2. p --> Text
3. img --> Image
4. onClick --> onPress

#### Styling

Can't use CSS style sheet --> use stylesheet in JS

```javascript
const styles = StyleSheet.create({
    container: {
        flex: 
        justifyContent: 'center',
        backgroundColor: '#ecf0f1',
        padding: 40,  
    },    
...});
```

Getting screen dimension: Use Dimension Class in React Native

```javascript
getScreenSize = () => {  
    const screenWidth = Math.round(Dimensions.get('window').width);  
    const screenHeight = Math.round(Dimensions.get('window').height);  
    this.setState({ screenWidth: screenWidth, screenHeight: screenHeight 
})  }
```

#### Platform specific component

Android and IOS has unique component: TouchableNativeFeedback on Android; TouchableHighlight on IOS

Method 1: Selectively render component based on OS: `if (Platform.OS === 'android')...`      &#x20;

Method 2: Create two version of components: MyButton.ios.js / MyButton.android.js

#### Animation & Gesture

{% embed url="https://facebook.github.io/react-native/docs/animated.html" %}

{% embed url="https://facebook.github.io/react-native/docs/layoutanimation.html" %}

{% embed url="https://facebook.github.io/react-native/docs/panresponder.html" %}

#### Navigation

Mobile device involves several screens --> use react-navigation

```javascript
import {createAppContainer} from'react-navigation';
import {createStackNavigator} from'react-navigation-stack';
const MainNavigator = createStackNavigator({
    Home: {screen: HomeScreen},
    Profile: {screen: ProfileScreen},
});

const App = createAppContainer(MainNavigator);
exportdefault App;
```

## Communicating with Server API

Identify user from authentication: Authentication identifying a user in the process of providing access to system data or services based on the user's identity

#### Common Authentication Method:

1. Basic HTTP: username/password for each request
2. Session-based: Client receive session id after authentication --> store in Cookies --> attach it to every subsequent request
3. JWT-based: Client send encrypted user info --> receive a token --> token included in every request & decrypted by the server

#### JWT-based:

The client authenticates with a usernameand a password once, receives a token, and only sends the token for subsequent requests, until the token times out — works like an all inclusive resort!

#### RESTful API:

REpresentational State Transfer (REST) is an architectural style for distributed hypermedia systems.

1. GET: Retrieve info from server that doesn't change the server (safe method) --> Return same info everytime if no PUT or POST request issued --> 200(OK) / 404(Not Found)
2. POST: HTTP method that creates new subordinate resources, e.g., a new user in a collection of users. POST is not safe or idempotent --> 201 (Created) with info on new resource / 200 (OK) / 204 (No Content)
3. PUT: HTTP method to update existing information on the server --> 200 (OK) / 204 (No Content) --> If resource not exist, create one with code 201 (same as POST)
4. DELETE: HTTP method that deletes resources from the server --> idempotent (Calling DELETE multiple times doesn't change) --> 200 (OK) if resp include an entity with status --> 202 (Accepted) if request queued / 204 (No Content) if performed but entity not included

![](<../.gitbook/assets/Screen Shot 2022-03-22 at 10.35.11 AM.png>)![](<../.gitbook/assets/Screen Shot 2022-03-22 at 10.35.17 AM.png>)

Password encode and decode: NPM base-64 package:

`import base64 from'base-64';`

`base64.encode(username + ":" + password);`

#### Passing Authentication Info

Pass user credential example:

&#x20;`'Authorization', 'Basic ' + base64.encode(username + ":" + password)`



Pass token example:

`'x-access-token', result.token`

``![](<../.gitbook/assets/Screen Shot 2022-03-22 at 10.38.31 AM.png>)``![](<../.gitbook/assets/Screen Shot 2022-03-22 at 10.38.36 AM.png>)``

## Mobile Navigation with React Native

1. react-navigation
2. react-native-navigation: More Advanced --> Change Native Component

#### Setup

`npm install @react-navigation/native`

`npm install react-native-reanimated react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view`

History API provides a Window object to stack pages user previously vistited:

Press back button: `window.history.back()`

Press forward button: `window.history.forward()`

Navigate in stack: `window.history.go(3)`

#### Type of Navigation&#x20;

1. Switch navigator: Show one screen at a time, no back action (Authentication flow)
2. Stack navigator: Enable transition between screens, where each screen is in stack. Navigator automatically implement native transition animation (list & view detail back and forth)
3. Tab Navigation: Tabs at bottom or tob of the screen (Main menu and sub sections)
4. Drawer Navigation: Tab-like, but can be hidden and exposed like a drawer (Options & setting)

#### Navigation Props

Each screen is automatically provided with a _navigation_ props, no need to specify in constructor (navigate, goBack, state)

![](<../.gitbook/assets/Screen Shot 2022-03-24 at 9.44.34 AM.png>)![](<../.gitbook/assets/Screen Shot 2022-03-24 at 9.44.49 AM.png>)

## Mobile Input via Gesture React Native

{% embed url="https://facebook.github.io/react-native/docs/gesture-responder-system" %}

{% embed url="https://facebook.github.io/react-native/docs/panresponder" %}

{% embed url="https://kmagiera.github.io/react-native-gesture-handler" %}

{% embed url="https://www.npmjs.com/package/react-native-swipe-gestures" %}

{% embed url="https://github.com/dancormier/react-native-swipeout" %}

### PanResponder

Uses the core gesture responder system to reconcile several touches into a single gesture that can be used to recognize multi-touch gestures.

1. Initialize PanResponder obejct with event handlers

![](<../.gitbook/assets/Screen Shot 2022-03-24 at 9.59.22 AM.png>)

2\. provide \_panResponder as props into component

![](<../.gitbook/assets/Screen Shot 2022-03-24 at 10.03.23 AM.png>)

#### Animated

Create time-based animation:

![](<../.gitbook/assets/Screen Shot 2022-03-24 at 10.05.03 AM.png>)![](<../.gitbook/assets/Screen Shot 2022-03-24 at 10.05.33 AM.png>)

#### LayoutAnimation

Animate entire screen when there's change in layout (remove a component)

LayoutAnimation is used before setState is called

![](<../.gitbook/assets/Screen Shot 2022-03-24 at 10.06.47 AM.png>)

## Date Object in JS

Date object represent a single moment in time with a platform-independent format, both be used by server and user

For user: Thu Nov 07201911:53:47 GMT-0600 (Central Standard Time)

For server: 2019-11-07T11:53:47-06:00

#### Serialize date into ISO 8601 format:

```javascript
var date = new Date();
console.log(date); // Thu Nov 07 2019 11:58:58 GMT-0600 (Central Standard Time)

var json = JSON.stringfy(date);
console.log(json); // "2019-11-07T17:58:58.487Z"
```

BUT, cannot deserialize back to date format

SO, use trick:

![](<../.gitbook/assets/Screen Shot 2022-03-24 at 10.11.14 AM.png>)

## Accessibility Building

#### Accessible Rich Internet Application (ARIA)

aria is a set of HTML attributes that make web components available to assistive technologies.

```html
<div id="percent-loaded" 
role="progressbar" 
aria-valuenow="75" 
aria-valuemin="0" 
aria-valuemax="100"></div>
```

#### In React Native

RN provides us with access to assistive technologies that mobile platforms provide (e.g., VoiceOver on iOS or TalkBack on Android) through component attributes.

```jsx
<View accessible={true}>
    <Text>List item one</Text>
    <Text>List item two</Text>
</View>
```

#### RN accessibility Properties:

1. `accessible`: attribute to indicate if the element is an accessible element; If so, group its childern in a single selectable component
2. `accessibilityLabel`: attribute defines screen reader descriptions of components
3. `accesssibilityHint`: tell the user what will be performed on this accessible element

#### RN accessibility Actions:

Standard, e.g., magicTap, escape, activate, increment, decrement, longpress, or custom actions, handled by onAccessibilityAction.

```jsx
onAccessibilityAction={(event) => {
    switch (event.nativeEvent.actionName) {
        case'longpress':
        // take action      ...    
    }  
}}
```

## AsyncStorage

1. Simple: Core functionality set/get
2. Unencrpyted: Access controll by location access
3. Persistent: Data saved until explicitily deleted
4. Global: Saved data is global to the app

#### Setup: Async, so return a Promise

`npm install @react-native-async-storage/async-storage`

`import AsyncStorage from'@react-native-async-storage/async-storage';`

Store accordingly: Dictionary or File in IOS and databsase in Android

#### Save Data

```jsx
storeData = async () => {
    try {
        await AsyncStorage.setItem('@storage_Key', 'stored value')  
    } 
    catch (e) {
    // saving error  
    }
}
```

#### Retrieve Data

```tsx
getData = async () => {
    try {
        const value = await AsyncStorage.getItem('@storage_Key')
        if(value !== null) {
            // value previously stored    
        } 
    } 
    catch(e) {
    // error reading value  
    }
}
```

![](<../.gitbook/assets/Screen Shot 2022-03-29 at 11.02.07 AM.png>)

{% embed url="https://github.com/react-native-community/async-storage" %}

#### Theming in RN

{% embed url="https://nativebase.io" %}

{% embed url="https://react-native-elements.github.io/react-native-elements" %}

#### NativeBase

Enable theming using NativeBaseProvider

{% embed url="https://docs.nativebase.io/setup-provider" %}

#### extendTheme():

![](<../.gitbook/assets/Screen Shot 2022-03-29 at 11.06.34 AM.png>)

## Sensor

1. React Native Library: react-native-sensors
2. Expo Library: expo-sensors

![](<../.gitbook/assets/Screen Shot 2022-03-29 at 11.08.44 AM.png>)![](<../.gitbook/assets/Screen Shot 2022-03-29 at 11.10.07 AM.png>)

## App LifeCycle Using AppState

Everything we have been doing so far assumes that our app is loaded on the screen and is running as a foreground process.

We need to be able to perform background processes or safely save the user's data in case the OS suspends it or the user quits it.

AppState:

* active: foreground activity
* background: background activity
* inactive: transitioning between foreground and background

![](<../.gitbook/assets/Screen Shot 2022-03-29 at 11.13.04 AM.png>)

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

dd

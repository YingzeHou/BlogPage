---
description: 'GitHub Repo: https://github.com/YingzeHou/portfolio.git'
---

# React.js

## Installation

1. Download Node.js
2. Run VScode as admin role in the target directory
3. `npm install -g create-react-app`
4. `npx create-react-app <your-app-name>.`
5. `cd <your-app-name>`
6. Delete unneccesary files like icon, css, etc. (Keep App.js & index.js)
7. `npm start` to start the development server

## StartUp

1. Create components and sub-components folders under src (Use .jsx and .scss files)
2. `yarn add node-sass` to enable use of scss file
3. Delete pre-exist package-lock.json and run `npm install` to download all required dependencies on local machine

## Syntax

* Control scroll type and scroll alignment

```scss
.section{
            scroll-behavior: smooth;
            scroll-snap-type: y mandatory;
            scrollbar-width: none; //for firefox
            &::-webkit-scrollbar{
                    display: none;
            }
}

>*{
            width: 100vw;
            height: calc(100vh - 60px);
            scroll-snap-align: start;
}
```

* Built-in boolean function to change state

```jsx
import { useState } from "react";
const [QRopen, setQRopen] = useState(false)

(Cover is a pre-designed sub component)
<Cover QRopen={QRopen} setQRopen={setQRopen}/>

(Cover, pass the boolean variable and corresponding boolean set func in)
export default function Cover({QRopen, setQRopen}) {
    return (
        ...
        <div className="wechatcode">
            // Use the value of QRopen to determine to display WechatCode component or not
            {QRopen ? <WechatCode QRopen={QRopen} setQRopen={setQRopen}/> : null}
        </div>
        ...
        <div className="itemContainer">
            <Wechat className="icon"/>
                <span>
                     // When click on, lambda expression to setQRopen to change QRopen to opposite value
                     // Therefore, after click, QRopen change from false->true, and above WechatCode component is shown
                    <div onClick={()=>setQRopen(!QRopen)}>&nbsp;Wechat</div>
                </span>
        </div>
}
```

* Animation in Scss (use @keyframes to define the action name and behavior)

```scss
.name{
        font-size: 50px;
        font-weight: 900;
        color: darkgray;
        text-align: center;
        margin-top: calc(80vh / 2);

        animation-name: floating;
        animation-duration: 3s;
        animation-iteration-count: infinite;
        animation-timing-function: ease-in-out;
    }
    @keyframes floating {
        0% { transform: translate(0,  0px); }
        50%  { transform: translate(0, 15px); }
        100%   { transform: translate(0, -0px); }   
    }
```

## Deployment

1. In the project folder, use npm `install gh-pages --save-dev` / `yarn add gh-pages --save-dev` to apply github pages dependencies
2. Go to package.json and add "homepage" at the very beginning and "predeploy", "deploy" at npm script:

```json
"homepage": "http://YingzeHou.github.io/portfolio",
"name": "portfolio",
"version": "0.1.0",
"private": true,
....
"scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  }
```

&#x20;  3\. Create a github repo and push local project to remote repo

&#x20;  4\. Run `npm run deploy` to deploy the website, thus website is available at homepage url

{% embed url="https://reactjs.org/docs/getting-started.html" %}

{% embed url="https://www.w3schools.com/react" %}

{% embed url="https://buildwithreact.com" %}

{% embed url="https://www.taniarascia.com/getting-started-with-react" %}

## History & Overview

WHY: JS library for building user interfaces

DOM for single-page applications (SPAs) can be huge

Large number of updates on DOM elements

#### Virtual DOM

Virtual representation of the user-facing elements that are kept in memeory and synced with the real DOM when DOM elements are updated.

#### Reconciliation

The process to diffing and syncing the virtual and real DOM to render changes for the user.

#### Declaritive

Express logic of a computation without describing its flow: What we want the outcome to be

![](<../.gitbook/assets/Screen Shot 2022-02-15 at 11.26.26 AM.png>)

ReactDOM library takes care of reconciliation and updating user-facing content under the hood

## Building Block

Elements: Light, stateless, immutable, virtual representation of a DOM element

Generate **new element** to update the page

```jsx
var root = React.createElement('div');
ReactDOM.render(root, document.getElementById('example'));
```

Components: A function or class that accepts an input and returns a React element

Works like JS functions; Accept props; Each component is encapsulated (one component per file) and can operate independently, affording modularity.

```jsx
class Welcome extends React.Component {
    render(){
        return <h1>Hello, {this.props.name}</h1>;
    }
}
```

#### render()

Returns a React element to be displayed on the page. WHAT to see on screen-->into render()

* ReactDOM.render(): Mounts the declared element as a child to the specified container in the DOM.
* Component.render(): Creates the virtual DOM representation of the contents of the React component. Then, we call ReactDOM.render() to mount it to the real DOM

#### props:

Properties, the arbitrary input provided into React component that utilize them to render content.

Component never modify props; Read-only & Immutable;

```jsx
function Welcome(props){
    return <h1>Hello, {this.props.name}</h1>
}
const element = <Welcome name = "Professor" />;
ReactDOM.render(element, document.getElementById('root'));
```

#### states

Fully private and controlled by the component

Keep track of changes in data.

```jsx
class Welcome extends React.Component{
    constructor(props){
        super(props);
        this.state = {date: new Date()};
    }
}
```

#### JSX

Syntax extension to JavaScript, that adds XML syntax to JavaScript. JSX declarations produce React elements.

Makes React programming extremely effective

#### Naming Convention

camelCase involves writing phrases such that each word begins capitalized with no spaces. (ReactDOM & JSX)

hyphen-case involves writing phrases in lower case and using a hyphen as a seperator.&#x20;

PascalCase capitalizes all words with no spaces (React Components)

### Component Library

Abstract away the low-level CSS implementation of user-facing elements.

* Bootstrap: (1) CDN=JS (2) Bootstrap dependency (3) React Bootstrap package
* Foundation
* Semantic UI
* Pure
* UIkit

### Component Development & Reuse

1. Mock-up design: Sketch out the design
2. Break the UI into component hierarchy: Structure of the component->tree layout
3. Build static version: HTML component layout: div->child DOM structure
4. Identify the minimal set of mutable state: Check elements to see if changeable
5. Identify where your state should live: (1) App track state; (2) TACard keep track; (3) TAContactButton keep track: Scope of the state, #3 most aligned with React way (Bestly, state need to be as close/low level as possible (component))
6. Add inverse data flow: Parent->Child: props; Child->Parent: callback returns

![](<../.gitbook/assets/Screen Shot 2022-02-17 at 11.58.23 AM.png>)

### Fragment

React constructs that can group child components without adding extra nodes to the DOM

\<React.Fragment> can be automatically removed when groupping, simplify DOM structure

### Controlled vs Uncontrolled Components

States of controlled components are managed by React. User input element (input, textsarea, select...) uncontrolled. Use refs to give React access to DOM elements

![](<../.gitbook/assets/Screen Shot 2022-02-17 at 12.08.50 PM.png>)

#### this.bind()

this.\<functionName>.bind(this), clarifies that the scope of the function that is passed to children component is within the parent component.

Calling(top): function()-->Call directly

Passing(bottom): function-->Pass as pointer

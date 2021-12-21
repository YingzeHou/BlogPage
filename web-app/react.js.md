---
description: 'GitHub Repo: https://github.com/YingzeHou/portfolio.git'
---

# React.js

## Installation

1. Download Node.js
2. Run VScode as admin role in the target directory
3. Comman line: `npx create-react-app .`
4. Delete unneccesary files like icon, css, etc. (Keep App.js & index.js)
5. `npm start` to start the development server

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

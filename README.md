# Using Stack.Js libraries with different framework and bundlers

Basic Installation steps to use stack.js library with different framework and bundlers.

Make sure you have [Node.js](https://nodejs.org/en/) ( Node 16.7.0 ) and Npm installed in your machine.

# Frameworks

## Create React App
### [Installation](https://create-react-app.dev/docs/getting-started/)
```
npx create-react-app hello-world
```

#### Available Scripts
First go to the create react app project directory
```
cd hello-world
```
To run app in development mode
```
npm start 
```
To launch test runner in interactive watch mode 
```
npm test
```
To build the app for production to the build folder
```
npm run build
```
### Create Project 
To test Stacks.js library with Create-React-App
```
npm install @stacks/wallet-sdk --save
```
Open ```src/App.js``` . Update the file to make changes to the React component. 
```
import logo from './logo.svg';
import './App.css';
import { generateSecretKey } from '@stacks/wallet-sdk';

function App() {
  const secretKey = generateSecretKey();
  const secretKey128 = generateSecretKey(128);

  return (

    <div className="App">
      <img src={logo} className="App-logo" alt="logo" />

      <p>
        <b>Generate 24-word Secret Key</b>: {secretKey}
      </p>

      <p>
        <b>Generate 12-word Secret Key</b>: {secretKey128}
      </p>

    </div>
  );
}

export default App;

```
Run ```npm start``` command and then head over to your browser to see the newly generated keys. 
## Vue CLI
### [Installation](https://cli.vuejs.org/guide/installation.html)

```
npm install -g @vue/cli
```
To verify Vue has been properly installed
```
vue 
```
### Create Project 
```
vue create hello-world
```
In the terminal, you will be asked to choose a preset and after choosing the appropriate one, the project will be created

To run Vue App
```
cd hello-world
npm run serve
```
To use Vue GUI
```
vue ui
```
To test Stacks.js library with Vue
```
npm install @stacks/wallet-sdk --save
```
 ```
 cd src/components
 touch StacksWallet.vue
 ```
 This will create a new vue file in the ```src/component``` directory. To try out Stacks.js wallet-sdk package copy the following code in the newly created file.
 ```
 <template>

<div> <b>Generate Secret Key</b>: {{ secretKey }}</div>

</template>

<script>
 import { generateSecretKey } from '@stacks/wallet-sdk';
  export default {
   data() {
  const secretKey = generateSecretKey();
    return {
      secretKey
    }
  }
  }
</script>
```
Go to ```src/App.vue``` file and import the newly created vue file. The App.vue will be modified to look like this.
```
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld  msg="Welcome to Your Vue.js App"/>
    <StacksWallet msg=""/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import StacksWallet from './components/StacksWallet.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    StacksWallet
  }
}
</script>
```
Now if you run ```npm run serve``` command you will see a newly generated secret key at the bottom of the page.

## Angular CLI
### [Installation](https://angular.io/cli)
```
npm install -g @angular/cli
```
To verify angular cli has been installed properly
```
ng help
```
### Create Project 
To build an application and serve it locally
```
ng new hello-world
cd hello-world
ng serve
```
In your browser, open http://localhost:4200/ to see the new application run

To test Stacks.js library with Angular CLI
```
npm install @stacks/transactions
```
In case you get the ```Angular default import error```, add the following flag in the compilerOptions section of tsconfig.json
```
"allowSyntheticDefaultImports": true
```

To avoid ```Uncaught ReferenceError: global is not defined when adding package``` add the following to your ```src/pollyfills.ts```
```
(window as any).global = window;
```

Angular allows you to bind application state defined inside of your ```src/app/app.component.ts``` file to its HTML template at ```src/app/app.component.html```.

Modify the AppComponent as
```
import { Component } from '@angular/core';
import { getPublicKey, makeRandomPrivKey } from '@stacks/transactions';


@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Stacks Transaction Package';
  privateKey=makeRandomPrivKey()
  publicKey = getPublicKey(this.privateKey).data;
}
```
Update ```src/app/app.component.html``` to connect the data defined in ```src/app/app.component.ts```
```
<h1> {{title}}</h1>
<div> <b>Generate Public Key</b>: {{ publicKey  }}</div>
```

# Bundlers

## Vitejs
### [Installation](https://vitejs.dev/guide/#scaffolding-your-first-vite-project)
```
npm init vite@latest
```
You will then be prompted to choose the project name, framework and variant or can specify directly through extra command line options
```
npm init vite@latest hello-world --template vue
```
A folder will be created in the project directory with the project name specified. Now run the following commands 
```
cd hello-world
npm install 
npm run dev 
```
In your browser, open http://localhost:3000/ to see the application run

## Webpack
### [Installation](https://webpack.js.org/guides/getting-started/)
```
npm install webpack webpack-cli --save-dev
```
Check package.json file where webpack and webpack-cli will be listed as dependencies near the bottom
The project is ready to start using webpack as its bundler

### Setting up a project to Bundle 
The project has nothing to bundle yet. The following instructions explain how a simple bundle process happens.

In the same location as package.json file, add the following:

* A folder called src
* An index.js file inside src
* A dist folder

The “source” code is the code that will be written and edited. The “distribution” code is the minimized and optimized output of the build process that the browser will display.

The default entry point is ./src/index.js file. To build the bundle with webpack run the following command
```
npx webpack
```
### Configuring webpack to generate HTML
To populate the dist folder, execute the following command so an HTML file can be generated in the dist folder
```
npm install html-webpack-plugin --save-dev
```

## Parcel
### [Installation](https://parceljs.org/getting-started/webapp/)
```
npm install --save-dev parcel
```
Check package.json file where Parcel will be listed as dependencies near the bottom.

### Setting up a project to Bundle 
In the same location as package.json file, add the following:

* A folder called src
* An index.ts file inside src
* A dist folder
* A main.js file inside dist

In package.json file, add the following lines 
```
  "source": "src/index.ts",
  "main": "dist/main.js",
```
The "source" field will be used to reference the source files and the "main" field will be used as the output file of the build.

Add your code in the src/index.js file and to build use the following command:
```
npx parcel build
```
Parcel will build the source code and output a JavaScript file in dist/main.js as referenced by the main field.

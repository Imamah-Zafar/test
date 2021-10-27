# Using Stack.Js libraries with different framework and bundlers

Basic Installation steps to use stack.js library with different framework and bundlers.

Make sure you have [Node.js](https://nodejs.org/en/) ( Node 16.7.0 ) and Npm installed in your machine.

## Create React App
### [Installation](https://create-react-app.dev/docs/getting-started/)
```
npx create-react-app hello-world
```
Create-React-App requires the following dependencies:

"jest": "26.6.0"

"webpack": "4.44.2"

However, Stack.js uses a different version of the above mentioned packages. 
By running the following command, you will see that the version of Jest installed by stack.js is "26.6.3"
```
grep version node_modules/jest/package.json
```
By running the following command, you will see that the version of webpack installed by stack.js is "5.50.0"
```
grep version node_modules/webpack/package.json
```
To avoid the issue of incompatible version, execute the following steps:

#### Installing compatible version of Jest
```
npm uninstall jest
npm install jest@26.6.0
```
#### Installing compatible version of Webpack
```
npm uninstall webpack
npm install webpack@4.44.2
```
This will solve issue of incompatible versions.

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

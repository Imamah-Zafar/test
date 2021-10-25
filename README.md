# Using Stack.Js libraries with different framework and bundlers

Basic Installation steps to use stack.js library with different framework and bundlers

## Create React App
### Installation 
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
### Installation

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
### Installation
```
npm install -g @angular/cli
```
To veryify angular cli has been installed properly
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
### Installation
```
npm init vite@latest
```
You will then be promted to choose the project name, framework and variant or can specify directly through extra command line options
```
npm init vite@latest hello-world --template vue
```
A folder will be created in the project directory with the project name specified. Now run the following commands 
```
cd hello-world
npm install 
npm run dev 
```
In your browser, open http://localhost:3000/ to see the new application run

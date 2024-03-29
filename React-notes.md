
### Using npm:

1. **Check Current Version:**
   Determine the current version of React in your project. You can find this information in your `package.json` file under the `dependencies` section.

2. **Update React:**
   Run the following command in your project directory to update React to the latest version:

   ```bash
   npm install react@latest react-dom@latest
   ```

   Replace `latest` with the desired version number if you want to update to a specific version.

3. **Update Other Dependencies:**
   After updating React, it's a good idea to check if there are any other dependencies that need updating. You can do this by running:

   ```bash
   npm outdated
   ```

   If other packages are outdated, you can update them using:

   ```bash
   npm update
   ```

### Using Yarn:

If you are using Yarn, you can follow a similar process:

1. **Check Current Version:**
   Determine the current version of React in your project by checking your `package.json` file.

2. **Update React:**
   Run the following command to update React to the latest version:

   ```bash
   yarn add react@latest react-dom@latest
   ```

   Replace `latest` with the desired version number if you want to update to a specific version.

3. **Update Other Dependencies:**
   Check for outdated packages:

   ```bash
   yarn outdated
   ```

   Update other packages:

   ```bash
   yarn upgrade
   ```


Npx vs Npm : tool to set up project 
Npm : node package  Manager : need to install on  local system :
Npx : node package Runner : not need to install global dependency :  npx create-recat-app ./  : npm start

DOM : Docunmenst Object Model:  https://developer.mozilla.org/en-US/docs/Web/API/Document
componennt : ex header , footer etc

functional component : create component an dthen call i from app component after craeting export anmd them import at APp.js : rendering UI only, 
ex:
welcome.jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

export default Welcome;


App.js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

export default Welcome;

class component : need to extand Reeact.Component and then render it. data management 
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
Different from functional components, class components must have an additional render( ) method for returning JSX.


DIffrance : 
We used to use class components because of "state". In the older versions of React (version < 16.8), it was not possible to use state inside functional components.

Therefore, we needed functional components for rendering UI only, whereas we'd use class components for data management and some additional operations (like life-cycle methods). 




props :prop (stands for property) which we use to transport data from one component to another.
https://www.freecodecamp.org/news/how-to-use-props-in-react/
note : props only transport data in a one-way flow (only from parent to child components). It is not possible with props to pass data from child to parent, or to components at the same level.
for class component 
ex: Welocme.jsx

function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

App.js
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
for fucntional component 
tools.jsx:
function Tool(props) {
  const name = props.name;
  const tool = props.tool;
    return (
      <div>
        <h1>My name is {name}.</h1>
        <p>My favorite design tool is {tool}.</p>
      </div>
    );
}

export default Tool

App.js
import Tool from "./Tool"

function App() {
  return (
    <div className="App">
      <Tool/>
    </div>
  )
}

export default App

cannot cnages value of props & componenst always capital 


State : 



1.hello with

----functional component 
/App.js
import React from 'react';
import './App.css';
import Hello from './components/hello';


function App() {
  return (
    <div className="App">
        <Hello/>
    </div>
  );
}

export default App;

/hello.js
import React from "react";

const Hello = () =>  <h1>Hello</h1>

export default Hello;


---class component 

```markdown
# README 

## Common Issues and Solutions

### Insufficient Permissions in VS Code

If you are facing permission issues with your repository in VS Code, try changing the permissions of your repository using the following command:

```bash
sudo chmod -R 777 Repo_name
```

### npm WARN Using --force Recommended Protections Disabled

This kind of error can occur due to several reasons, such as improperly installed dependencies, a corrupted `node_modules` folder, or incorrect installation of dependencies (globally instead of locally, or vice versa). 

To troubleshoot this issue:

1. Delete the `node_modules` directory and the `package-lock.json` file:

```bash
rm -rf node_modules
rm package-lock.json
```

2. Clear your npm cache:

```bash
npm cache clean --force
```

3. Reinstall the dependencies:

```bash
npm install
```

4. Try to start your application again:

```bash
npm run start
```

### npm-watch

npm-watch can run scripts from package.json when there are any changes in your app folders or files. It’s useful when you want to automate your build in the server when there are any changes.

To install:

```bash
npm install npm-watch
```

Then, add the following scripts to your `package.json` file:

```json
"watch": "npm-watch",

"watch": {
  "build": {
    "patterns": [
      "src"
    ],
    "extensions": "js,jsx"
  }
},
```

To start watching:

```bash
npm run watch
```

For more details, visit [this link](https://medium.com/how-to-react/use-npm-watch-to-auto-build-your-reactjs-app-6ed0e5d6cb00).

### Error: Cannot find module '@nestjs/core'

This error can be caused by missing dependencies. Ensure you've installed all the necessary dependencies for your project. For more details about handling CORS with NestJS, visit [this link](https://bipinparajuli.com.np/blog/how-to-use-cors-with-nestjs).
```

 here are some common errors you might encounter when working with React and TypeScript, along with some potential solutions:

**1. 'Property does not exist on type' Error:**

This error occurs when you try to access a property that TypeScript doesn't know exists on a particular type. 

Solution: If you're sure that the property exists, you can extend the existing type with an interface.

```typescript
interface EnhancedWindow extends Window {
  myCustomProp: string;
}

declare let window: EnhancedWindow;

console.log(window.myCustomProp); // TypeScript won't complain now.
```

**2. 'React is not defined' Error:**

This error happens when you're using JSX syntax without importing React in your component.

Solution: Always import React in your component files.

```jsx
import React from 'react';

// Your component code here.
```

With React 17 and onwards, you can use JSX without importing React, but you need to adjust your JSX transform in your Babel or TypeScript configuration.

**3. 'Property 'props' is missing in type but required in type 'Readonly' Error:**

This error occurs when you try to create a React component without passing in the required props.

Solution: Always pass in required props when creating a component, or make the props optional in your component type definition.

```jsx
type MyComponentProps = {
  name: string; // This prop is required.
  age?: number; // This prop is optional.
};

const MyComponent: React.FC<MyComponentProps> = (props) => {
  // Your component code here.
};

<MyComponent name="John" />; // This is fine.
<MyComponent />; // TypeScript will complain here because 'name' is missing.
```

**4. Unhandled Rejection (Error): Network Error**

This error occurs when an Axios request is made and the request is rejected.

Solution: Always add a catch block to handle rejected promises when making requests with Axios.

```jsx
axios.get('/api/data')
  .then((response) => {
    // Handle the response.
  })
  .catch((error) => {
    console.error('An error occurred:', error);
  });
```

Here are some common errors that occur when working with React:

**1. 'Element type is invalid':**

This error is often caused by trying to render or import a component that does not exist or is not a valid React component.

Solution: Ensure that the component you're trying to use is properly exported and imported.

**2. 'Cannot read property 'setState' of undefined':**

This error occurs when the context of 'this' is not available inside a function in a React component.

Solution: Make sure to bind your methods in the constructor of your component, or use arrow functions which auto-bind 'this'.

**3. 'Each child in a list should have a unique "key" prop':**

React needs the 'key' prop when you create components dynamically (for instance, when you're mapping an array to multiple components). 

Solution: Always add a unique 'key' prop to your dynamically created components.

**4. 'Cannot update during an existing state transition (such as within `render`)':**

This error occurs when you try to change state during the rendering phase of a component. 

Solution: Do not use `setState` in the `render` method. State updates should go in lifecycle methods or event handlers.

**5. 'Maximum update depth exceeded':**

This error occurs when a component keeps rendering itself causing an infinite loop.

Solution: Ensure that there are no infinite loops caused by state updates that trigger a re-render.

**6. 'Failed prop type':**

This warning shows up when the type of a prop passed to a component doesn't match the type expected by the component.

Solution: Always ensure you're passing props of the correct type as expected by your components.

These are some common errors that occur while working with React. Always check your console for any error messages when your application doesn't work as expected, as these messages can help guide you to the solution.

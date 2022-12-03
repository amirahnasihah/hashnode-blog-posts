# Changing Button's Text using React

In this tutorial, I am going to give you a step-by-step guide how to change the button text from `On` to `Off` while understanding the concepts of conditional rendering in React application.

# Conditional Rendering

In React, you often need to display different things depending on different conditions. You can conditionally render JSX using JavaScript syntax like `if` statements, `&&`, and `? :` operators.

# To Start

To begin, you can create react app using the command line or any code editor (e.g., VSCode). You can also directly use the [CodeSandbox](https://codesandbox.io/) for an online code editor that is simple to use and allows to deploy your code.

# Code Output

This is the result that you will achieve once you have finished the tutorial. When you clicked the button, the text `On` will change to `Off`.

The best practice is to read through this tutorial and follow along several times to have a better knowledge of what you're doing with this concept in React.

<iframe src="https://codesandbox.io/embed/button-on-to-off-grqgsz?fontsize=14&hidenavigation=1&module=%2Fsrc%2FApp.js&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="button-ON-to-OFF"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

[![Edit button-ON-to-OFF](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/button-on-to-off-grqgsz?fontsize=14&hidenavigation=1&module=%2Fsrc%2FApp.js&theme=dark)

# Update the Button Text (On to Off)

So, we know that in React, we can create multiple components and we can render the components based on the state of the application.

So, what I'm going to do is to create a new folder named 'components'. And inside the folder, let us have a component file named `ButtonControl.js`.

Then, we go to that component file and I will have the function `ButtonControl`. Then, I'm going to export default the ButtonControl component. Like this:

**_ButtonControl.js_**

```JSX
function ButtonControl() {}

export default ButtonControl;
```

Now, inside the ButtonControl component, I'm going to create two arrow functions.

The first function will be the `handleOnClick()` function and the second function which will be the `handleOffClick()` function. We will have it like this:

**_ButtonControl.js_**

```JSX
function ButtonControl() {
 const handleOnClick = () => {};

 const handleOffClick = () => {};
}

export default ButtonControl;
```

# `handleOnClick` And `handleOffClick` Explained

First, let's create a state. So, we have a state and need to import the `useState` because we want to use the state.

So, I'm going to have the `useState`, and this `useState` will be coming from `'react'`.

Alright, and now what we are going to do is, in this React state array `[]`, I'm going create a state variable and the name of the state variable will be `isClickedOn`.

Then, if we want to update this state variable, we will have a function which will be `setIsClickedOn`. The initial value of this state will be `false`.

**_ButtonControl.js_**

```JSX
import { useState } from "react";

function ButtonControl() {
 const [isClickedOn, setIsClickedOn] = useState(false);

 const handleOnClick = () => {};
 const handleOffClick = () => {};
}

export default ButtonControl;
```

Alright, we are done.

And this is what going to happen when you have the `handleOnClick` and `handleOffClick`.

What I want is for whenever a user clicked the `On` button, it will show the `Off` button. If a user clicked `Off`, it will show the `On` button.

And what the `ButtonControl` component is going to return here is a JSX.

I'm going to create a `<div>` tag, and inside the `<div>`. I'm going to have a `button` function so it will display a button based on the condition of `isClickedOn`:

- if it's clicked On, then it will show the Off button.
- if it's clicked Off, then it will show the On button.

**_ButtonControl.js_**

```JSX
return <div>{button}</div>;
```

So, that is where we need to create a condition and now, we need to define what this button is.
What I will do is that I am going to have a `let button`. Like this:

```JSX
let button;
return <div>{button}</div>;
```

And this `let button`, what we will do is we will check that if we have `isClickedOn`, if it is `true`, then we have a button that is going to show `Off`. So. let's have a component of that `<OffButton />`.

**_ButtonControl.js_**

```JSX
let button;
if (isClickedOn) {
  button = <OffButton />;
}
return <div>{button}</div>;
```

At this point, we will have it like this:

**_ButtonControl.js_**

```JSX
import { useState } from "react";

function ButtonControl() {
 const [isClickedOn, setIsClickedOn] = useState(false);

 const handleOnClick = () => {};
 const handleOffClick = () => {};

let button;
if (isClickedOn) {
  button = <OffButton />;
}
return <div>{button}</div>;
}

export default ButtonControl;
```

# OnButton and OffButton Components

Before continuing doing this, let's create two more components which will be the `OffButton` component and the `OnButton` component.

What we can do is instead of creating a component in a separate file, we are going to create in the same file here at `ButtonControl.js` a `OnButton` component as well as the `OffButton` component.

So, I will have the `OnButton()` function and this `OnButton()` is going to take some `props`. And when it has a prop it is going to return a JSX.

So, what it is going to return is that it will return a `<button>` tag and on that button, we are going to have an `onClick` event. 

Alright, here we are going to have the **On** text. Like this:

```JSX
function OnButton(props) {
 return <button onClick={}>On</button>
}
```

Now similarly, we will also have that `OffButton()` function, so we can just copy the `OnButton()` function and it will have that function called `OffButton()` with the **Off** text. Like this:

```JSX
function OffButton(props) {
 return <button onClick={}>Off</button>;
}
```

Next, there is a prop in both components of the `OnButton(props)` and `OffButton(props)` we are passing.

So, we have to pass some prop in here `<OffButton />` in the ButtonControl component.

I am going to pass a prop as `onClick` property and our `onClick` will have a handler which will be a `handleOffClick` arrow function. It will be like this:

**_ButtonControl.js_**

```JSX
let button;
if (isClickedOn) {
  button = <OffButton onClick={handleOffClick} />;
}

return <div>{button}</div>;
```

But if it is not the case then else, what I have to show is I going to have to show a `OnButton`. Like this: 

```JSX
let button;
if (isClickedOn) {
  button = <OffButton onClick={handleOffClick} />;
} else {
  button = <OnButton onClick={handleOnClick} />;
}
```

We will save it.

# Experimenting with The State As `true`

And then, we need to do something that whenever we click on the handle events, where whenever we click on the Off, we have to change the state.

So this state of `useState(false)` will get changed to **'the false one'**.

And I'm going to change the state `setIsClickedOn()` as `true`.

Alright, now this `setIsClickedOn(true)` will become false whenever you click the `handleOffClick` function.

So, let's have this on `handleOffClick` too.

```JSX
const [isClickedOn, setIsClickedOn] = useState(false);

const handleOnClick = () => {
 setIsClickedOn(true);
};
const handleOffClick = () => {
 setIsClickedOn(true);
};
```

After we are done doing this, let's call the component.

We go to the `App.js` to call this `ButtonControl` component. Let's import the ButtonControl from the components folder to use the component.

**_App.js_**

```JSX
import ButtonControl from "./components/ButtonControl";
import "./styles.css";

export default function App() {
	return (
		<div className="App">
			<ButtonControl />
		</div>
	);
}
```
 
So, we know that in React, we create multiple components and we can render the components based on the state of the application.
 
# Button On Not Changing to Off

Let's import the ButtonControl component and have the `<ButtonControl />`

Then, we will save it.

And now, we see that we have a parsing error and that error is in the `ButtonControl` states that parsing JSX attributes must only be assigned a non-empty expression.

So, let's go back to the `ButtonControl.js` and let see the line number where the error occurred.

Here, we have to specify what prop we have passed in the prop is `props.onClick`.

Let's pass the `onClick` here in `OnButton()` function and similarly with `OffButton()` function. In the end it will look like the below:

**_ButtonControl.js_**

```JSX
function OnButton(props) {
 return <button onClick={props.onClick}>ON</button>;
}

function OffButton(props) {
 return <button onClick={props.onClick}>OFF</button>;
}
```

Alright, and save it. 

Now, if we refresh we will see on the screen we have that `On` button.

So, whenever I click on this On button on the screen, it will change to Off.

However, when I click the button again, it is **NOT** changing to On again.

That means we have made a mistake and this mistake you will see here on `handleOffClick()` function that we have to change the value back to `false`.

```JSX
const handleOffClick = () => {
 setIsClickedOn(false);
};
```

Now, if I click on the button, then you will see that we have a toggle like ON and OFF button.

So, in our case the state was `isClickedOn`  and based on the `isClickedOn`, we are showing different components like the `OffButton` component or the `OnButton` component.

This way you can actually do the conditional rendering in React where you can show the components based on the state of the application.
 
# Full Code

**_App.js_**

```JSX
import ButtonControl from "./components/ButtonControl";
import "./styles.css";

export default function App() {
	return (
		<div className="App">
			<ButtonControl />
		</div>
	);
}
```

**_ButtonControl.js_**

```JSX
import { useState } from "react";

function ButtonControl() {
	const [isClickedOn, setIsClickedOn] = useState(false);

	const handleOnClick = () => {
		setIsClickedOn(true);
	};
	const handleOffClick = () => {
		setIsClickedOn(false);
	};

	let button;
	if (isClickedOn) {
		button = <OffButton onClick={handleOffClick} />;
	} else {
		button = <OnButton onClick={handleOnClick} />;
	}

	return <div>{button}</div>;
}

export default ButtonControl;

// BUTTON TEXT
function OnButton(props) {
	return <button onClick={props.onClick}>ON</button>;
}

function OffButton(props) {
	return <button onClick={props.onClick}>OFF</button>;
}
```

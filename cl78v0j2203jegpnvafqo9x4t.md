# React Tutorial Beginner - `useState` and `useEffect` with Example Code

In this tutorial, I'm going to give you a step-by-step guide on understanding the main concepts of React which introduce the concept of state and lifecycle in a React component.

# State is Memory of a Component

Let's have a brief on what `State` is.

As a result of an interaction, components frequently need to update what's on the screen. Typing into the form updates the input box, clicking "next" on an image carousel changes the picture displayed and clicking "purchase" adds a product to the shopping cart. Components must "remember" information such as the current input value, the current picture, and the shopping cart. This type of component-specific memory is referred to as a state in React.

# Full Tutorial Code

These are the code that you will achieve once you are done with the tutorial. My advice is, to read it until finished and start doing again using the code editor.

```js
import React, { useState, useEffect } from "react";

function Clock() {
  const [time, setTime] = useState(new Date().toString());

  useEffect(() => {
    console.log("component mounted or updated");
    const interval = setInterval(showDate, 1000);

    return () => {
      console.log("cleanup of Interval");
      clearInterval(interval);
    };
  }, [time]);

  function showDate() {
    console.log(new Date().toString('en-GB'));
    setTime(new Date().toString());
  }

  return <h1>{time}</h1>;
}

export default Clock;
```

# First Step

To begin, you can start creating your own react app using the command line or can directly go to [CodeSandbox](https://codesandbox.io/) if you want to skip using the command line which is faster. CodeSandbox is an online code editor and prototype tool that speeds up the creation and sharing of web apps where you can directly deploy your app without any hustle.

First, create a new folder inside the `src` folder named `components`. Then, create a JavaScript file called `Clock.js` which in React is the component of `Clock`.

Create a function `Clock` Component.

Export this component by typing `export default Clock` below the function.

```js
function Clock() {}

export default Clock;
```

Let's create another function in this component, which will be the `showDate()` function.

After have `showDate()`, we'll have a `<h1>` tag to make it large or other tags you prefer and this `<h1>` will have the date of `{new Date().toString()}`.

```js
return <h1>{new Date().toString()}</h1>;
```

Then we call this function with the `setInterval()`. And have the `setInterval` as in every one second. Let's call the function first.

```js
function showDate() {
 return <h1>{new Date().toString()}</h1>;
}

setInterval(showDate, 1000);
```

And this `showDate()` function will be called in every one second.

Alright, and another thing going do is to have also `console.log()` above the return method. We `console.log()` the `Date` function to see whether its running or not in our console. Like below:

```js
function showDate() {
 console.log(new Date().toString());
 return <h1>{new Date().toString()}</h1>;
}

setInterval(showDate, 1000);
```

And have to also return a JSX because every component returns a JSX.

Return a JSX below the `setInterval()` method.

Type `return (<div> </div>)` as below and let's call the `showDate()` function inside the `<div>` JSX.

```js
function Clock() {
 return (
   <div>
     <h1>Hello from Clock component!</h1>
     <div>{showDate()}</div>
   </div>
 );
}
```

You can also use an empty fragments `<> </>` to display the JSX like this:

```js
function Clock() {
 return (
  // empty fragment
   <>
     <h1>Hello from Clock component!</h1>
     <div>{showDate()}</div>
   </>
  // empty fragment
 );
}
```

If you are not seeing anything happen on your screen, go to `App.js` and import our Clock Component, then use the Clock Component by adding the `<Clock />`. Like this:

App.js

```js
import Clock from "./components/Clock";

function App() {
  return (
    <>
      <Clock /> {*to use the Clock Component*}
      <p>Hello from App.js</p>
    </>
  );
}

export default App;
```

Now we will see what is actually happening when we use the Clock component. We see the time and here in the Clock component, you will see that we have a `setInterval` which is being called every one second.

So, if I go to the inspect element (`F12` hotkey) and if I go to console, then in the console you will see that the time is getting updated every second. This is what we will achieve so far:

```javascript
function Clock() {
  return (
    <div>
      <h1>Hello from Clock component!</h1>
      <div>{showDate()}</div>
    </div>
  )
}

function showDate() {
 console.log(new Date().toString());
 return <h1>{new Date().toString()}</h1>;
}
setInterval(showDate, 1000);

export default Clock;
```

# Time not updated on the screen

But then, on the screen this time not getting updated every second. Only inside the console does it get updated every second.

And that is where we have to use the `State`.

A state will be a local state of a component. So, whenever a State is changed, a component will re-render and it will render the updated `JSX`.

So, what we can do is, we need to import a State.

What to do is in the `Clock.js` Component. Let's have an `import React from 'react';` at the top of the `Clock()` function.

And in order to use a State, there is a hook called `useState`. To use the `useState` hook, you need to import the state variable from 'react'. Like below:

```js
import React, { useState } from "react";
```

Alright, now let's create a `constant`. To use a State in a function component, you need to create a constant and you have to use an array `[]` like structure, and then you will have a `useState()`. Like this:

```js
const [] = useState();
```

And here you need to give the initial value of your state =&gt; `useState(initial value)`. So, my initial value will be the same which is the `Date()` function.

```js
const [] = useState(new Date().toString())
```

Put inside `useState()`, and here I will have the `time` and I will have a `setTime`. Whenever you use a `useState()`, it actually gives you a time variable and it also gives a function to update that variable.

```js
const [time, setTime] = useState(new Date().toString())
```

So now, we are going to change line `return <div>{showDate()}</div>;` and have a `{time}` here and save it. Then start seeing a time on the screen and this is the time.

```js
function Clock() {
 return (
   <div>
     <h1>Hello from Clock component!</h1>
     <div>{time}</div>
   </div>
 );
}
```

Now, what I'm going to do is I need to update that time.

So whenever this `setInterval` makes a call to the `showDate()` in every one second instead of, returning this `return <h1>{new Date().toString()}</h1>;`

Next, I'm going to update my state.

# To Update the State

So want to update my state, I'm going to do a `setTime()` and this `setTime()` is going to update the state.

So, let's type `setTime(new Date().toString())` and save it.

So, every second my `showDate()` function is being called `function showDate() {` and whenever it is called I changed the state variable.

So, you change the state variable with the help of `set` function; `[setTime] = ..`. This is a set function `setTime(new Date().toString());` and as soon as I do a `setTime()` with a new updated time `new Date().toString()`, so my state `useState()` gets changed and whenever the states get change, the component is re-rendered and that's where we will see that the screen is now updating.

We can see now on the screen the time is running every second and also from the console.

If error occurs, make sure that the `showDate()` is inside the `Clock()` function. Like below:

```js
import React, { useState } from "react";
 
function Clock() {
 const [tick, setTick] = useState(new Date().toString());
 setInterval(showDate, 1000);
 
 return (
   <>
     <h1>Hello from Clock component!</h1>
     <div>{tick}</div>
   </>
 );
 
 function showDate() {
   console.log(new Date().toString());
   setTick(new Date().toString());
 }
}
 
export default Clock;
```

This `showDate()` function works as updating in every one second, and we use `showDate()` function inside the `Clock` function to update the time every one second, to do that, we use state variable which is `setTime(new Date().toString())`. Earlier in `showDate()` function we put `return <h6>{date}</h6>;` because whenever you use a `useState()`, it actually gives you a time Variable and it also gives a function to update that variable which using `set`.

Thats why we change from `return <h6>{date}</h6>;` to `setTime(new Date().toString())`.

Now on the screen, the time is running every one second and also from the console.

```js
import React, { useState } from "react";
 
function Clock() {
 const [time, setTime] = useState(new Date().toLocaleTimeString("en-GB"));
 setInterval(updateTime, 1000);
 
 return (
   <>
     <h2>{time}</h2>
   </>
 );
 
 // this function used to update the time every one second
 function updateTime() {
   console.log(new Date().toLocaleTimeString("en-GB"));
   setTime(new Date().toLocaleTimeString("en-GB"));
 }
}
 
export default Clock;
```

## `useState` Hook

Now, what is this `useState()` is and what is this `[time]` and `[setTime]` is.

Let's have a state, I'm gonna have a constant and now I'm going to create a state variable of `name`.

So, you will give it as a `name`, and then whenever you want to update this name, you will update it with the help of a `setName` function.

```js
const [name, setName]
```

For example, you can also do the same thing whenever you want to have a flag. Alright, and now you want to update this flag value so you will have a `setFlag`

```js
const [flag, setFlag]
```

Alright, so you will use the `useState()` as `const [flag, setFlag] = useState()` and then you will set the initial value.

So, my initial value of the flag is `true`. so let's have a `useState(true)`.

In this way, you will create and use the State.

# Lifecycle using the `useEffect`

Now, what is the lifecycle?

So whenever you have a component, the component also has lifecycles.

So the lifecycles will be that you want to execute something whenever your component is *mounted* or whenever your component is first time rendered or you want to do something whenever your component is getting updated or whenever your component is destroyed.

> 💡 Mounting is the phase in which our React component mounts on the DOM (i.e., is created and inserted into the DOM). This method is called just before a component mounts on the DOM or the render method is called. After this method, the component gets mounted.

For example, the Clock component is inserted into the `DOM`.

We use lifecycle because we want the clock keeps updating. So, need to use the `useEffect()` function

So, in those cases, you will use a lifecycle.

To use a life cycle method in the function component, we make use of a `useEffect` hook.

```js
import React, { useState, useEffect } from "react";
```

So, this way I will use an `useEffect` hook. And now what I'm going to do here is that I'm going to write a `useEffect` and this `useEffect` will have two arguments, `useEffect(args1, args2)`

The first argument will be a `function` or a side effect that you want to run and the second argument will be a dependency array. I will use an arrow function as the first argument.

```js
useEffect(() => {})
```

And the second argument will be the dependency array. So this dependency array will depend on these State variables.

So, now what I'm going to do here is that let's have a `console.log()` and I'm going to have here a string of `"component mounted or updated"`.

Alright, and remove the dependency array and save it.

```js
 useEffect(() => {
   console.log("component mounted or updated");
 });
```

I'll save it and now let's go to the inspect element and I will go to the console and here I will just remove this function because we don't want and it's polluting our console. Let's comment out `console.log(new Date().toString());`

Alright, now I will refresh my page. And you will see that as soon as I refresh my page, My component is mounted and my state is also getting updated.

So, the state is getting updated because this state variable is getting updated.

So, if I don't want that this gets updated every time, what I can do here is that I have a dependency array `[]`

```js
 useEffect(() => {
   console.log("component mounted or updated");
 }, []);
```

And if I give it a dependency in this array of a state where able then in that case the `useEffect()` will run only if the state variable changes.

So, what I'm going to do is I'm going to have a flag here:

```js
useEffect( ... ;}, [flag]);
```

Then, save it, and now will refresh the page.

So, you now will see that even though your time is getting changed in every one second, your `useEffect()` `useEffect( ... ;}, [time]);` is not running because your `useEffect()` is now dependent on another state variable which is a `time`.

So, that means whenever a `time` is changed in that case, the `useEffect()` will run.

So, if the flag is changing from `true` to `false`, then you will see that the `useEffect` will run if I change this flag to `true` again, then you will see that the `useEffect` will run.

So this way this is a lifecycle of a component, whenever a component is mounted or whenever a component is updated. you want to run some side effects.

Now, there is a scenario that whenever a component is destroyed you want to run effect of unmounting that whenever the component is unmounted you want to do something.

So, in that case, what we can do is that let's have a constant and gonna have an interval and I will remove/cut the `setInterval()`

So now I have the interval here and this interval depends on the time.

So, I'm gonna copy this {time} and gonna have the {time} here at `useEffect` dependency array:

```js
useEffect( ... ;}, [time]);
```

So, you can see that every time this `showDate()` function is running my component is getting updated.

So, that's why we see a lot components updated on console logs.

Now, let's assume that you have a subscription to this interval.

Now, you want to clear this subscription whenever your component is unmounted or whenever your component is not visible on your screen.

So what we can do here, inside this `useEffect()` function is that we can have a clean function. Which will have a return and this will be an arrow function. Alright and here, inside this arrow function, you can do your cleanup.

So, let me have a `console.log("cleanup of Interval")` and below gonna have the `clearInterval` method. And let gonna clear this interval. I'm going to add the constant interval into the `clearInterval(interval)`. Like below:

```js
() => {
     console.log("cleanup every one second");
     clearInterval(setInterval(showDate, 1000));
   };
```

Now see that whenever a component is mounted. the first thing that will happen is the `cleanup function` will run whenever this component is mounted or whenever a component is unmounted.

```js
useEffect(() => {
  console.log("component keep mounted or updated");
 
  return () => {
    console.log("cleanup of Interval");
    clearInterval(setInterval(updateTime, 1000));
  };
}, [time]);
```

# Dependency Array

If we remove the dependency, which is \[time\], in the console will look like this, not update the interval.

```markdown
component keep mounted or updated
cleanup of Interval
component keep mounted or updated
```

It is not running because the `useEffect()` is now dependent on another state variable which is a `time`.

But if we put dependency array \[time\], then the console will look like this:

```markdown
cleanup of Interval
component keep mounted or updated
cleanup of Interval
component keep mounted or updated
cleanup of Interval
component keep mounted or updated
cleanup of Interval
component keep mounted or updated
cleanup of Interval
```

Then, in that case, the `useEffect()` will run only if the state variable changes. The second argument is will be the dependency array. So, this dependency array will depend on these State variables.

So, this is how you will do the State and the lifecycle in the React components.

# CodeSandbox

<iframe src="https://codesandbox.io/embed/state-and-lifecycle-ticking-clock-57yhrb?autoresize=1&fontsize=14&hidenavigation=1&theme=dark" style="width:100%;height:500px;border:0;border-radius:4px;overflow:hidden" sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"></iframe>

![Edit state-and-lifecycle-ticking-clock](https://codesandbox.io/static/img/play-codesandbox.svg align="left")

* * *

# Share This Tutorial

👉 Please share my posts with the community at [**daily.dev**](http://daily.dev) / social media by adding the article's URL to the feed. By adding my article's URL to the feed, I can share my insights and knowledge with other tech enthusiasts and contribute to the passionate community.

`Cheers✨`
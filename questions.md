# React Questions

>## 1. What is the difference between Component and PureComponent? give an example where it might break my app.


* **React.PureComponent and React.Component** is having similar functionality except rendering mecahism
	* PureComponent uses `shouldComponentUpdate` only shallowly compares the objects. which will help component to not rerender if parent rerenders unless the pure component's props (or state) have changed.
	* Component rerenders every time if parent rerenders, irrespective of whether the component's props and state have changed.
    >```purecomponent considered harmful in cases such as when we use PureComponents for components that take primatives as props, like a counter, but when dev tries to add non-primative props, it is not recommendable practice.```

>## 2. Context + ShouldComponentUpdate might be dangerous. Can think of why is that?
* After fetching the new  data, components using `shouldComponentUpdate` may block the update of the components, since they are not aware of the changed context for all their possible descendants.

>## 3. Describe 3 ways to pass information from a component to its PARENT.

* We can just create a method inside the parent component itself and we can just call it from the child component and do all that updation necessary stuff 
* As Version 16.3 introduces a new context API, so by usinf Context API we can create menthod and will behave as a contet provider. With the help of context provider different component of the Application can communicate with each other seemlessly.
* In React v16.8+, we can take advantage of `useState()` that will help to  update the parent state by using function state and then pass it on to child as a prop attribute.

>## 4. Give 2 ways to prevent components from re-rendering.
* Convert the component to a class if it is a Pure component and prevent the re-render in shouldComponentUpdate() by returning false.
* By Using React.memo (HOC) will help to validate the rendering only if props change.

>## 5. What is a fragment and why do we need it? Give an example where it might break my app.
* A common pattern in react is for a component to return multiple elements, usually these elements are wrapped for example
inside of the div. In most cases the wrapper div is irrelevant and is only added because react components require you to return only one element. we should use fragments, react fragments let you group a list of children without adding any extra node to the dom because fragments are not rendered to the dom so basically we'll use react fragments wherever we would normally use a wrapper div we can use react fragments with the `react.fragment` syntax.

>## 6. Give 3 examples of the HOC pattern.
* A HOC will allow to reuse and help to enhace the capabilities. Some of the real-time examples are:

	* Logging functionality like keeping up the history of naviagtion throughout the application session.
	* Sorting functionality
    * Loader component

>## 7. what's the difference in handling exceptions in promises, callbacks and async...await.
* Handling exception in promise is quite easy as Promise has inbuilt `try and catch`, if any exception occurs during promsise call, it gets caught and considered as rejection.
* In case of error handling in callback will help to throw an error asynchronously means that an error is thrown in the JavaScript code of an asynchronously executed callback.
* async keyword implicitly creates a Promise for its function which has invisble try and catch and execute reject on error.

>## 8. How many arguments does setState take and why is it async.
* `setState(updater[, funcationCallback])`
	* First argument is an updater function with previous state reference and props.
	* second parameter is an optional callback which gets called immediately after the setState is completed.
```
this.setState((prevState, props) => {
  return {counter: prevState.counter + props.step};
})
```

>## 9. List the steps needed to migrate a Class to Function Component.
* Change the class to function keyword and remove the extension of React.Component as it is not supported.
* Remove the render method, keep the contents of the render() method in the function body.
* Convert all other methods on the class to functions as a closures.
* Remove the constructor function and all the references of `this` keyword.
* `useState` in place of this.setState as it is not exist in functional components and `useEffect` for state update.
* Replace lifecycle methods

>## 10. List a few ways styles can be used with components.
* Using Extenal stylesheets using import, where we can have seperate styles for each component.
* Inline styles for elements in form of objects.
* using styled-components library will help to have component specific styles and contains user-interactivity as well using JS.
>## 11. How to render an HTML string coming from the server.
* Using `html-react-parser` library.
* Using `dangerouslySetInnerHTML` method of React.

    

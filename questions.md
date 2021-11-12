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
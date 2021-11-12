# React Questions

>## 1. What is the difference between Component and PureComponent? give an example where it might break my app.


* **React.PureComponent and React.Component** is having similar functionality except rendering mecahism
	* PureComponent uses `shouldComponentUpdate` only shallowly compares the objects. which will help component to not rerender if parent rerenders unless the pure component's props (or state) have changed.
	* Component rerenders every time if parent rerenders, irrespective of whether the component's props and state have changed.
    >```purecomponent considered harmful in cases such as when we use PureComponents for components that take primatives as props, like a counter, but when dev tries to add non-primative props, it is not recommendable practice.```

    >## 2. Context + ShouldComponentUpdate might be dangerous. Can think of why is that?
* After fetching the new  data, components using `shouldComponentUpdate` may block the update of the components, since they are not aware of the changed context for all their possible descendants.

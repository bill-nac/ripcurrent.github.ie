## React
Tips on using the React framework

- [Arrow functions](#arrowfunctions)
- [Destructing](#desctructing)


# Arrow functions <a href="#arrowfunctions"></a>
if only returning a value, use arrow function expressions with **concise** body  
```
const Search = () => (  
  <div>  
    <p>Hello</p>  
  </div>  
);  
```

arrow function expressions can also be used with **block** body if need logic and return value
```
const Search = () => {  
  /* other logic */
  
  return (
  <div>  
    <p>Hello</p>  
  </div>
  );  
};  
```

# Events
React synthetic event is a wrapper for the browsers native event

# Destructing <a href="#desctructing"/></a>
```
const user = {
  firstName: 'Bill',
  lastName: 'Tierney'
}; 

//Instead of 
const firstName = user.firstName;
const lastName = user.lastName;

//can use
const {firstName, lastName} = user;
```
so we can changes components from
```
const List(props) => {
  //use props.list
}
```
to
```
const List({list}) => {
  //use list
}
```







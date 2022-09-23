## React
Tips on using the React framework

# Arrow functions
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

# descructing
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

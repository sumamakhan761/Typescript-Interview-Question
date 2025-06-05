# Typescript-Interview-Question

<ul>
  <li>
  Can you write some code to demonstrate the difference between explicit and implicit types and which one to use?
  </li><br/>
  Ans :
  
  ``` 
  
    // This is explicit typing -> where you need to give type to variable
    let firstName: string = 'sumama';
    const user: { id: number; name: string } = {
      id: 1,
      name: 'Jon doe',
    };
  
    // This is implicit typing -> where you don't need to give type to variable
    let firstName = 'sumama';
    const user = {
      id: 1,
      name: 'Jon doe',
    };
    
  ```

</ul>

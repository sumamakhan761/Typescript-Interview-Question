# Typescript-Interview-Question

<ul>
  <li>
  Can you write some code to demonstrate the difference between explicit and implicit types and which one to use?
  </li><br/>
  Ans :


  ```ts
  
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

<li>
  Explain type in TypeScript by writing some code
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>
  Ans :
  
```ts
type jobRole = string; // build you'r own type;

type Profile = {
  profileId: number;
  firstName: string;
  lastName: string;
  jobRole: jobRole;
};

const employeeProfile: Profile = {
  profileId: 1,
  firstName: 'Sumama',
  lastName: 'Khan',
  jobRole: 'SDE',
};

const getEmployeerProfileId = (profile: Profile) => profile.profileId;

```

<li>
  Explain interface in TypeScript by writing some code
 <br/>
 Level: Easy, Duration: 5 minutes
</li>
  <br/>

  Ans :

  ```ts
  // An interface is a way to define the shape of an object — what properties it has, and their types.
 
    interface Profile = {
      profileId: number;
      firstName: string;
      lastName: string;
    };
    
    const employeeProfile: Profile = {
      profileId: 1,
      firstName: 'Sumama',
      lastName: 'Khan',
    };
    
    const getEmployeerProfileId = (profile: Profile) => profile.profileId;
        
  ```

<li>
 Explain difference between interface and type in TypeScript by writing some code
 <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>

  Ans :

  ```ts
  // Interface and type are very similar and both can be used interchangeably.

   // Similar:
   // Using interface
    interface Person {
      name: string;
      age: number;
    }
    
    // Using type
    type PersonType = {
      name: string;
      age: number;
    };
    
    const p1: Person = { name: "Alice", age: 30 };
    const p2: PersonType = { name: "Bob", age: 25 };

  // Diff-1:

    // interface supports extends
    interface Employee extends Person {
      jobRole: string;
    }
    
    // type uses intersection
    type EmployeeType = PersonType & { jobRole: string };
    
    const e1: Employee = { name: "Sumama", age: 21, jobRole: "SDE" };
    const e2: EmployeeType = { name: "Ali", age: 22, jobRole: "Designer" };

    // Diff-2:

    Declaration Merging (Only for Interface) means when you difine name of interface and use other replace or create interface same name so it will merge;
    interface Book {
    title: string;
  }
  
  interface Book {
    author: string;
  }
  
  const b: Book = {
    title: "TS Handbook",
    author: "Microsoft"
  };

 // This will NOT work with type, only interface allows merging definitions.
        
 // Diff-3:

  Utility Types (Works with type)

  type Point = { x: number; y: number };
  type ReadOnlyPoint = Readonly<Point>; // Makes all props readonly


  ```

<li>
  Write a function `getAddress` which adds city, state and country and returns a comma separated full address
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>

  Ans :

  ```ts

  type props = {
    city?: string;
    state?: string;
    country?: string;
  };

  function getAddress (p : props) : string{
    return [p.city, p.state, p.country].filter(Boolean).join(',');
  };

  ```


<li>
  
  Explain How to Narrow Union in TS with some code
  (Union narrowing is the process TypeScript uses to figure out the specific type from a union of multiple possible types at runtime.)
  <br/>
  Level: Easy, Duration: 5 minutes

</li>

  <br/>

  ```ts

    type Pending = {
    category: 'Pending';
  };
  
  type Process = {
    category: 'Process';
  };
  
  type Success = {
    category: 'Success';
  };

  type Task = Pending | Process | Success;

   const getTask = (T: Task) => {
      if (T.category === 'Pending') {
          console.log(`you'r task in ${T.category}`)
        return T.category;
      } else if (T.category === 'Process') {
          console.log(`you'r task in ${T.category}`)
        return T.category;
      } else if (T.category === 'Success') {
          console.log(`you'r task is ${T.category}`)
        return T.category;
      }
    };


  ```
<li>
  
  Explain void in TS with some code
  <br/>
Level: Easy, Duration: 5 minutes

</li>
  <br/>

  ```ts

// void is used to define function return types when function does not return any thing
const Message = (message: string): void => {
  console.log(message);
};
  
  ```

<li>
  Why never as function return type in ts?
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>
  
  ```
   never represents a type that never occurs. If a function has never as its return type, it does not return anything — not even undefined.

    const errorHandler = (message: string): never => {
      throw new Error(message);
    };
    
    // this also works with void
    const errorHandler2 = (message: string): void => {
      throw new Error(message);
    };
    
    // here implicitly the return type will be string
    const errorHandler3 = (message: string) => {
      if (message === 'server-error') {
        return message;
      } else {
        throw new Error(message);
      }
    };

  ```
  

</ul>

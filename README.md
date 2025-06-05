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
  
  

</ul>

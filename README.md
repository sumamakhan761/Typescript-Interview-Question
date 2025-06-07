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
  Why never as function return type in TS?
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>

  Ans :
  
  ```ts
   // never represents a type that never occurs. If a function has never as its return type, it does not return anything — not even undefined.

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

<li>
  Explain any type in TS and write some code ?
  <br/>
  Level: Easy, Duration: 5 minutes
</li>

  <br/>

  Ans :
  
  ```ts
   // any is a type that tells TypeScript to turn off type checking for that variable.
   // It means the value can be anything — a string, number, object, function, etc.

    const Name = (firstName: any, lastName: any) => {
      return firstName + lastName;
    };

```

<li>
  Explain unknown type in TS with some code
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>
  Ans :

  ```ts
// unknown is a type-safe alternative to any means this value can be anything, but you must check its type before using it.

  let's take first any type
  
  function handleResponse(data: any) {
    // You can do anything — even dangerous operations
    console.log(data.toUpperCase()); // No error, but may crash at runtime if data is not a string
  }

  now, Unknown

  function handleResponse(data: unknown) {
    // TypeScript forces you to check the type
    if (typeof data === "string") {
      console.log(data.toUpperCase()); // Safe
    } else {
      console.log("Not a string, cannot convert to uppercase.");
    }
  }

  ```
  
<li>
  How will you add type for a DOM input element
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>
  Ans :

```ts

// When working with DOM elements (like <input>), TypeScript needs to know what kind of element
// you're working with so it can give you proper type safety and autocomplete.

// HTML (assume this exists in your page)
/*
<input id="username" type="text" />
<button id="submitBtn">Submit</button>
*/

document.getElementById("submitBtn")?.addEventListener("click", () => {
  const input = document.getElementById("username") as HTMLInputElement;

  // Now we can safely access input.value
  console.log("Username:", input.value);
});

```

<li>
  Give an example on how will you add type or interface for class
  <br/>
  Level: Medium, Duration: 15 minutes
</li>

  <br/>
  
  Ans :

```ts

interface ProfileInterface {
  getProfileName(): string;
  getSecurityPin(): string;
  optionalFunction?(): void;
}

class Profile {
  firstName: string;
  lastName: string;
  private securityPin: string;
  readonly email: string;
  static readonly maxBuyingCredit = 10000;
}

class Profile implements ProfileInterface {
  constructor(
      firstName: string,
      lastName: string,
      securityPin: string,
      email: string
    ) {
      this.firstName = firstName;
      this.lastName = lastName;
      this.securityPin = securityPin;
      this.email = email;
    }
  
      getProfileName(): string {
        return [this.firstName, this.lastName].join(' ');
      }
    
      getSecurityPin(): string {
        return this.securityPin;
      }
      updateSecurtyPin(pin: string): void {
      this.securityPin = pin;
     }
  
      getEmail(): string {
        return this.email;
      }
  
    // changeEmail(): void {
    //   not allowed since email is readonly
    //   this.email = 'xyz@gmail.com';
    // }
  }

  const buyerProfile = new Profile(
    'Sumama',
    'Khan',
    '2160',
    'xyz@gmail.com'
  );

  console.log(buyerProfile.getProfileName());
  console.log(buyerProfile.firstName, buyerProfile.lastName);
  buyerProfile.updateSecurtyPin('1234');

  // This is not allowed since this is a private property
  // console.log(buyerProfile.securityPin);

  console.log(buyerProfile.getSecurityPin()); // 1234

  console.log(buyerProfile.getEmail()); // email

  // static property does not exist on the instance but on the main class itself
  console.log(Profile.maxBuyingCredit);

  // now interviewer say extend class more

 class PremiumProfile extends Profile {
    private customUsername: string | undefined;
  
    setUsername(username: string): void {
      this.customUsername = username;
    }
  
    getUsername(): string | undefined {
      return this.customUsername;
    }
  }

const vipCustomer = new PremiumProfile(
  'Senzo',
  'Yomi',
  '1233',
  'xyz@gmail.com'
);
vipCustomer.setUsername('Senzoyami');
console.log(vipCustomer.getUsername());
console.log(vipCustomer.getProfileName());

```

<li>
  Explain enum in ts with some code
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>
  Ans :

```ts
// in js
const profile = {
  buyer: 0,
  seller: 1,
  admin: 2,
};

// in TS
// Note that by default the values will be 0,1,2...
enum ProfileEnum {
  buyer,
  seller,
  admin,
}

let myProfile: ProfileEnum = ProfileEnum.buyer;
console.log(profile.buyer, myProfile); // profile -> 0 , ProfileEnum -> 0

// This is a much recommended way of defining enums with strings rather than numbers
enum TaskEnum {
  Pnding = 'pending',
  Progess = 'progess',
  Success = 'success',
}

interface TaskInterface {
  id: number;
  task: TaskEnum;
}

const tasks : TaskInterface =  {
  id: 1,
  // this will throw error because type for profile is an enum and not string. Hence enum is a better way of using constant strings in your project to avoid any error
  // task: 'pending'

  task: TaskEnum.Prending, // right way
};

```

<li>
  explain generics in ts with some code
  <br/>
  Level: Hard, Duration: 15 minutes
</li>
  <br/>

  Ans:

  ```ts
  // Generics allow you to write reusable, type-safe functions, classes, and components that work with any data type — while still keeping type safety.

// basic Ex-1:
  function identity<T>(value:T):T {
    return value;
  }
  const num = identity<number>(5);       // type: number
  const str = identity<string>("Hello"); // type: string

// Ex-2 on arrray function

  function firstElement<T>(arr: T[]): T {
    return arr[0];
  }

const first = firstElement<string>(["a", "b", "c"]); // type: string

// EX-3 interface

  interface ApiResponse<T> {
    data: T;
    success: boolean;
  }
  
  const response: ApiResponse<string> = {
    data: "User created",
    success: true
  };

// EX-4 Class

  class Box<T> {
    contents: T;
  
    constructor(value: T) {
      this.contents = value;
    }
  
    getContents(): T {
      return this.contents;
    }
  }
  
  const numberBox = new Box<number>(123);
  const stringBox = new Box<string>("hello");

  ```

<li>
  explain tuple in ts with some code and how is it different from array?
  <br/>
  Level: Medium, Duration: 10 minutes
</li>
  <br/>

  Ans :
  // A tuple in TypeScript is a special type of array with two main characteristics: Fixed length , Tye Positions (Each element in the tuple has a specific type, and the order of types is enforced)
  
  ```ts
Ex-1:

// with Right Tuple Synctex
  let person: [string, number] = ["Alice", 30]; // string at index 0, number at index 1
  let point: [number, number] = [10, 20];      // both numbers
  let status: [number, string] = [200, "OK"];  // number and string

  // If you try to assign values in the wrong order or with the wrong types, ts       will throw an error

  let wrong: [number, string] = ["hello", 42]; // Error: Type 'string' is not assignable to type 'number'

Ex-2:
// Tuples can also be labeled for better readability (TypeScript 4.0+):

type UserTuple = [id: number, name: string];
const user: UserTuple = [1, "Jon doe"];
console.log(user[0]);
console.log(user[1]);

// tuple can be immutable when using a readonly
  
  ```

<li>
  explain what is an index signature in TS
  <br/>
  Level: Medium, Duration: 5 minutes
</li>
  <br/>

  Ans :

  ```
  // An index signature allows you to specify the type for all keys (of a certain type) and their corresponding values.

// structue
  type MyType = {
  [key : string] : valueType
}

// implementation

type Scores = {
  [studentName: string]: number;
};

const mathScores: Scores = {
  Alice: 90,
  Bob: 85,
  Charlie: 92,
};

  ```

</ul>

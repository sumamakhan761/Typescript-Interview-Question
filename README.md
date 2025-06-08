# Typescript Interview Questions

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

  ```ts
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


<li>
  explain what is an reocrd helper in TS with code
  <br/>
  Level: Medium, Duration: 5 minutes
</li>
  <br/>

  Ans :

  ```ts
  // TypeScript’s built-in Record utility type is a shorthand for the above index signature. The syntax is:

// structure
type MyType = Record<KeyType, ValueType>;

// implementation 
type student = Record <string , number>;
const Students : student = {
  Sumama : 18,
  usama : 19,
  kazama : 20,
}

// added also Dynamic Keys;
type student = Record <string , string | number>;
const Students : student = {
  Sumama : 18,
  usama : "19",
  kazama : 20,
}

console.log(Students)

  ```

<li>
  explain what is Omit utility in TS
  explain what is Pick utility in TS
  <br/>
 Level: Easy, Duration: 5 minutes
</li>
  <br/>

  Ans :

  ```ts
  // The Omit utility type in TypeScript allows you to create a new type by removing one or more properties from an existing type.

// syntax:

Omit<Type , Keys>
Interface Person {
  name : string;
  age : number;
  email: stsring;
}

type PersonWithoutEmail = Omit<Person , 'email'>;
// resulting type : {name : string; age:number;}
// you can omit multiple propertis by providing a union of keys;
type PersonWithoutEmail = Omit<Person , 'email' | 'age'>;
// resulting type : {name : string;}

// The Pick utility type is the inverse of Omit. It constructs a new type by selecting only the specified properties from an existing type.

// syntax :
Pick<Type, Keys>

interface Person {
  name: string;
  age: number;
  email: string;
}

type PersonNameAndEmail = Pick<Person, 'name' | 'email'>;
// Resulting type: { name: string; email: string; }

  ```

<li>
  explain what is Readonly helper in TS
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>

  Ans :
  
  ```ts

  interface Person {
    name: string;
    age: number;
    email: string;
  }

  const person: Readonly<Person> = {
    name : "Jon doe",
    age : 18,
    email : xyz@gmail.com,
  }

  // person.age = 19; // mutation will not be allowed bcz you can only read not write

  ```

<li>
  explain what is Partial helper in TS
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>

  Ans :
  
  ```ts

// The Partial utility type in TypeScript is a built-in helper that takes an existing type (interface or type alias) and returns a new type where all properties are set to optional.

// syntax

type PartialType = Partial<OriginalType>;

  interface Person {
    name: string;
    age: number;
    email: string;
  }

type PartialPerson = Partial<Person>; // now all are optional

const userA: PartialUser = {}; // valid: all properties are optional
const userB: PartialUser = { id: 1 }; // valid: only 'id' is provided
const userC: PartialUser = { name: "Alice", email: "alice@example.com" }; // valid: 'name' and 'email' provided

// This is equivalent to writing:
type PartialUser = {
  id?: number;
  name?: string;
  email?: string;
}

// commom use case for partial is in update functions, where you may want to update only some properties of an object:

function updateUser(user: User, updates: Partial<User>): User {
  return { ...user, ...updates };
}

const user: User = { id: 1, name: "Jon doe", email: "jondoe@example.com" };
const updatedUser = updateUser(user, { email: "newjondoe@example.com" });
// Only the email is updated, other properties remain unchanged[1][6].

  ```

<li>
  explain what is Required helper in TS
  <br/>
  Level: Easy, Duration: 5 minutes
</li>
  <br/>

  Ans :

  ```ts
    // Required helper will help us create a new type with all properties marked as required (rarely used)

  interface Person {
    name: string;
    age: number;
    email: string;
  }

function updateUser(user: Person, updates: Required<Person>): Person {
  return { ...user, ...updates };
}

const user: Person = { name: "Jon doe", age : 19, email: "jondoe@example.com" };
console.log(user);
const updatedUser = updateUser(user, { name: "Alice", age : 20 , email: "alice@example.com"});

console.log(updatedUser);

  ```

<li>
  explain literal type in TS
  <br/>
  Level: Medium, Duration: 5 minutes
</li>
  <br/>

  Ans :

  ```ts

// A literal type in TypeScript is a type that represents a specific, exact value rather than a broad category of values.

Ex-1:
   // literal type number
  const age = 32;
  // literal type string
  const apiStatus = 'failed';

Ex-2:
  type Direction = "up" | "down" | "left" | "right";
  let move: Direction = "up"; // Only these four strings are allowed

EX-3:
  type DiceRoll = 1 | 2 | 3 | 4 | 5 | 6;
    function rollDice(): DiceRoll {
      return (Math.floor(Math.random() * 6) + 1) as DiceRoll;
    }

  ```

<li>
  what is TSC and TSLS
  <br/>
  Level: Medium, Duration: 5 minutes
</li>
  <br/>

  Ans : 

  ```ts

  // rarely ask but you have some idea of it.
  three buliding blocks
  1. TS Programming Language
  ans : Language: syntax, keywords and type annotations
  2. TS compiler (TSC)
  ans : TSC: converts TS into JS
  3. TS Language service
  ans : TSLS: additional layer ex: autocompletion, autoimport, code formatting, signature help, colorization etc.

  ```

<li>
  Explain how you will use extends keyword for conditional types in ts
  <br/>
  Level: Medium, Duration: 5 minutes
</li>
  <br/>

  Ans :

  ```ts
  Ex-1:
  type IsString<T> = T extends string ? "Yes" : "No";
  type A = IsString<string>; // "Yes"
  type B = IsString<number>; // "No"

  Ex-2:
    type ToStringArray<T> = T extends string ? T[] : never;
    type Res = ToStringArray<string | number>; // string[] | never => string[];

    const arr: Res = ["hello", "world"];
    console.log(arr); // Output: ['hello', 'world']

    const invalidArr: Res = [1, 2, 3]; // Error: Type 'number' is not assignable to type 'string'

  ```

<li>
  Explain function overloading in ts
  <br/>
  Level: Medium, Duration: 15 minutes
</li>
  <br/>

  Ans :

  ```ts
  // Function overloading in TypeScript allows you to define multiple signatures for a single function, providing different parameter types and return types based on the input. This is particularly useful for libraries where you want to offer flexible functionality without requiring users to understand the underlying implementation details.

// Multiple definitions with type definitions
function getMessage(name: string): string;
function getMessage(name: string[]): string[];

// Note that we have not used arrow function since with arrow function we can not redeclare the function

// One Implementation
function getMessage(name: unknown): unknown {
  if (typeof name === 'string') {
    return `Hello, ${name}`;
  } else if (Array.isArray(name)) {
    return name.map((i) => `Hello, ${i}`);
  }
  throw new Error('name not provided');
}

// Usage
console.log(getMessage('Kiran')); // Hello Kiran
console.log(getMessage(['Kiran', 'John'])); // ['Hello, Kiran', 'Hello John']

  ```

<li> 
  Explain how you will use infer keyword in ts and Explain how will you use infer with four examples: create your own ReturnType helper, Get type of first arg in a function, get promise return type and get array item types
  <br/>
  Level: Hard, Duration: 15 minutes
</li>
  <br/>

  Ans :

  ```ts

  // The infer keyword in TypeScript is a powerful feature used within conditional types to extract and name a type from a complex structure.

  // 1. Creating Your Own ReturnType Helper

  type MyReturnType<T> = T extends (...args: any[]) => infer R ? R : never;
  // R is the magic part
  // If T is a function, the type becomes R (the return type).
  // If T is not a function, the type becomes never (which means "no possible value").

  function greet(name: string): string {
    return `Hello, ${name}!`;
  }
  type GreetReturn = MyReturnType<typeof greet>; // string

  // 2. Get Type of First Argument in a Function

  type FirstArg<T> = T extends (first: infer A, ...args: any[]) => any ? A : never;

  function logMessage(message: string, level: number): void {}
  type MessageType = FirstArg<typeof logMessage>; // string

  function noArgs(): void {}
  type NoArgType = FirstArg<typeof noArgs>; // never

  // 3. Get Promise Return Type

  type PromiseValue<T> = T extends Promise<infer U> ? U : never;
  // Is T a Promise? If yes, grab the type inside the promise and call it U and If yes, the type becomes U (the resolved value) or If not, it becomes never.

  type MyPromise = Promise<number[]>;
  type ValueType = PromiseValue<MyPromise>; // number[]
  
  type NotAPromise = PromiseValue<string>; // never

  // 4. Get Array Item Types

  type ArrayElement<T> = T extends (infer U)[] ? U : never;

  type StringArray = string[];
  type ElementType = ArrayElement<StringArray>; // string
  type NotAnArray = ArrayElement<number>; // never

  ```

<li>
  create custom Readonly helper in ts
  <br/>
  Level: Medium, Duration: 10 minutes
</li>
  <br/>

Ans :

```ts
  type CustomReadonly<T> = {
    readonly [U in keyof T] : T[U];
    // For each property name U in the set of all keys of T.
    // So, it loops over every property in T
    // readonly makes the properly in T.
  }
  
  interface Task {
    id: number;
    title: string;
    description: string;
  }
  
  const task: CustomReadonly<Task> = {
    id: 1,
    title: 'first task',
    description: 'This is the first task',
  };
  
  // task.id = 5; // get an error bcz can't update value only can read

```


</ul>

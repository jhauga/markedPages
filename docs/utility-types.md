## TYPESCRIPT TYPES

## Utility Types

<details>
 <summary><b>Section Code - src/code/utilityTypes.ts</b></summary>

 [src/code/utilityTypes](src/code/utilityTypes.ts)

```ts
// utilityTypes
// Example code for utilityTypes.

import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

// one
interface Point {
  x: number;
  y: number;
}

export let pointPart: Partial<Point> = {}; // `Partial` allows x and y to be optional
pointPart.x = 10;

// two
interface Car {
  make: string;
  model: string;
  mileage?: number;
}

export let myCar: Required<Car> = {
  make: 'Ford',
  model: 'Focus',
  mileage: 12000 // `Required` forces mileage to be defined
};

// three
export const nameAgeMap: Record<string, number> = {
  'Alice': 21,
  'Bob': 25
};

// four
interface Person {
  name: string;
  age: number;
  location?: string;
}

export const bob: Omit<Person, 'age' | 'location'> = {
  name: 'Bob'
  // `Omit` has removed age and location from the type and they can't be defined here
};

// five
interface PersonB {
  name: string;
  age: number;
  location?: string;
}

export const bobB: Pick<PersonB, 'name'> = {
  name: 'Bob'
  // `Pick` has only kept name, so age and location were removed from the type and they can't be defined here
};

// six
type Primitive = string | number | boolean
export const value: Exclude<Primitive, string> = true; // a string cannot be used here since Exclude removed it from the type.

// seven
type PointGenerator = () => { x: number; y: number; };
export const point: ReturnType<PointGenerator> = {
  x: 10,
  y: 20
};

// eight
type PointPrinter = (p: { x: number; y: number; }) => void;
export const pointB: Parameters<PointPrinter>[0] = {
  x: 10,
  y: 20
};

// nine
interface PersonC {
  name: string;
  age: number;
}
export const personC: Readonly<PersonC> = {
  name: "Dylan",
  age: 35,
};
// Would cause a compile error.
// personC.name = 'Israel'; 

// utility type takeaway
export var utilityTypesTakeAway = new takeAway("Utility Types");
utilityTypesTakeAway.setTakeAway(
 "`Partial` keyword makes all object properties optional.", 
 "`Required` keyword makes all object properties required.",
 "`Record` gives a unique key type and value type.",
 "`Omit` removes key types from object.",
 "`Pick` keeps only specified key type in object.",
 "`Exclude` removes types from union.",
 "`ReturnType` gets function type.",
 "`Parameter` gets parameter type.",
 "`Readonly` makes all properties unable to bemodified."
);
```

</details>

<details>
 <summary><b>Section Code - src/progress/utilityTypes.ts</b></summary>

 [src/progress/utilityTypes](src/progress/utilityTypes.ts)

```ts
// utilityTypes
// Output code for utilityTypes.

import { log } from "../support/format";
import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { sideNote } from "../support/sideNotes";
import { utilityTypesTakeAway, pointPart, myCar, nameAgeMap, bob, value, point, pointB, personC } from "../code/utilityTypes";

var pageName = "utilityTypes.ts";

export function runUtilityTypes(): void {
 sectionHeader("Types", "new");
 log("Utility Types", 2);
 cl();
 cl("src/code/utilityTypes");
 cl();
 cl("src/progress/utilityTypes");
 cl();
 // one
 log("Partial Utility Type", 3);
 cl();
 log(`The keyword \`Partial\` changes all properties to be optional. Example

  \`\`\`ts
interface Point {
  x: number;
  y: number;
}

let pointPart: Partial<Point> = {}; // \`Partial\` allows x and y to be optional
pointPart.x = 10;

console.log(pointPart);
// returns
/*`)
 log(pointPart);
 log(`*/
\`\`\``);

// two
log("Required Utility Type", 3);
cl();
log("Using `required` makes all properties required.");
cl();
log(`Example:

 \`\`\`ts
interface Car {
  make: string;
  model: string;
  mileage?: number;
}

let myCar: Required<Car> = {
  make: 'Ford',
  model: 'Focus',
  mileage: 12000 // \`Required\` forces mileage to be defined
};

console.log(myCar);
// returns
/*`);
 log(myCar);
 log(`*/
\`\`\`
`);
 cl();
 // three
 log("Record Utility Type", 3);
 cl();
 log("`Record` keyword defines an object type with a specific key type and value type.");
 cl();
 log(`Example:

\`\`\`ts
const nameAgeMap: Record<string, number> = {
  'Alice': 21,
  'Bob': 25
};

console.log(nameAgeMap);
// returns
/*`);
 log(nameAgeMap);
 log(`*/
\`\`\`
`);
 cl();
 log(sideNote("Record<string, number> is equivalent to { [key: string]: number }"));
 cl();
 // four
 log("Omit Utility Type", 3);
 cl();
 log("`Omit` keyword removes keys from object type.");
 cl();
 log(`Example:

\`\`\`ts
interface Person {
  name: string;
  age: number;
  location?: string;
}

const bob: Omit<Person, 'age' | 'location'> = {
  name: 'Bob'
  //\`Omit\` has removed age and location from the type and they can't be defined here
};

console.log(bob);
// returns
/*`);
 log(bob);
 log(`*/
\`\`\`
`);
 cl();
 // five
 log("Pick Utility Type", 3);
 cl();
 log("`Pick` keyword keeps only the object key specified.");
 cl();
 log(`Example:

\`\`\`ts
interface Person {
  name: string;
  age: number;
  location?: string;
}

const bob: Pick<Person, 'name'> = {
  name: 'Bob'
  // \`Pick\` has only kept name, so age and location were removed from the type and they can't be defined here
};

console.log(bob);
// returns
/*`);
 log(bob);
 log(`*/
\`\`\`
`);
 cl();
 // six
 log("Exclude Utility Type", 3);
 cl();
 log("`Exclude` keyword removes types from union.");
 cl();
 log(`Example:

\`\`\`ts
type Primitive = string | number | boolean
const value: Exclude<Primitive, string> = true; // a string cannot be used here since Exclude removed it from the type.

console.log(value);
// returns
/*`);
 log(value);
 log(`*/
\`\`\`
`);
 cl();

 // seven
 log("ReturnType Utility Type", 3);
 cl();
 log("`ReturnType` keyword gets function return type.");
 cl();
 log(`Example:

\`\`\`ts
type PointGenerator = () => { x: number; y: number; };
const point: ReturnType<PointGenerator> = {
  x: 10,
  y: 20
};

console.log(point);
// returns
/*`);
 log(point);
 log(`*/
\`\`\`
`); 
 cl();

 // eight
 log("Parameters Utility Type", 3);
 cl();
 log("`Parameter` keyword gets parameter types from function as an array.");
 cl();
 log(`Example:

\`\`\`ts
type PointPrinter = (p: { x: number; y: number; }) => void;
const point: Parameters<PointPrinter>[0] = {
  x: 10,
  y: 20
};

console.log(point);
// returns
/*`);
log(pointB);
log(`*/
\`\`\`
`);
 cl();

 // nine
 log("Readonly Utility Type", 3);
 cl();
 log("`Readonly` keyword makes all properties readonly and not modifiable.");
 cl();
 log(`Example:

\`\`\`ts
interface Person {
  name: string;
  age: number;
}
const person: Readonly<Person> = {
  name: "Dylan",
  age: 35,
};
person.name = 'Israel';

// compile error
// prog.ts(11,8): error TS2540: Cannot assign to 'name' because it is a read-only property.
\`\`\`
`);
 cl();

 // utility type takeaway
 log(utilityTypesTakeAway.outTakeAway());
}

```

</details>

### Partial Utility Type

The keyword `Partial` changes all properties to be optional. Example

  ```ts
interface Point {
  x: number;
  y: number;
}

let pointPart: Partial<Point> = {}; // `Partial` allows x and y to be optional
pointPart.x = 10;

console.log(pointPart);
// returns
/*
[object Object]
*/
```

### Required Utility Type

Using `required` makes all properties required.

Example:

 ```ts
interface Car {
  make: string;
  model: string;
  mileage?: number;
}

let myCar: Required<Car> = {
  make: 'Ford',
  model: 'Focus',
  mileage: 12000 // `Required` forces mileage to be defined
};

console.log(myCar);
// returns
/*
[object Object]
*/
```

### Record Utility Type

`Record` keyword defines an object type with a specific key type and value type.

Example:

```ts
const nameAgeMap: Record<string, number> = {
  'Alice': 21,
  'Bob': 25
};

console.log(nameAgeMap);
// returns
/*
[object Object]
*/
```

> [!NOTE]
> Record<string, number> is equivalent to { [key: string]: number }

### Omit Utility Type

`Omit` keyword removes keys from object type.

Example:

```ts
interface Person {
  name: string;
  age: number;
  location?: string;
}

const bob: Omit<Person, 'age' | 'location'> = {
  name: 'Bob'
  //`Omit` has removed age and location from the type and they can't be defined here
};

console.log(bob);
// returns
/*
[object Object]
*/
```

### Pick Utility Type

`Pick` keyword keeps only the object key specified.

Example:

```ts
interface Person {
  name: string;
  age: number;
  location?: string;
}

const bob: Pick<Person, 'name'> = {
  name: 'Bob'
  // `Pick` has only kept name, so age and location were removed from the type and they can't be defined here
};

console.log(bob);
// returns
/*
[object Object]
*/
```

### Exclude Utility Type

`Exclude` keyword removes types from union.

Example:

```ts
type Primitive = string | number | boolean
const value: Exclude<Primitive, string> = true; // a string cannot be used here since Exclude removed it from the type.

console.log(value);
// returns
/*
true
*/
```

### ReturnType Utility Type

`ReturnType` keyword gets function return type.

Example:

```ts
type PointGenerator = () => { x: number; y: number; };
const point: ReturnType<PointGenerator> = {
  x: 10,
  y: 20
};

console.log(point);
// returns
/*
[object Object]
*/
```

### Parameters Utility Type

`Parameter` keyword gets parameter types from function as an array.

Example:

```ts
type PointPrinter = (p: { x: number; y: number; }) => void;
const point: Parameters<PointPrinter>[0] = {
  x: 10,
  y: 20
};

console.log(point);
// returns
/*
[object Object]
*/
```

### Readonly Utility Type

`Readonly` keyword makes all properties readonly and not modifiable.

Example:

```ts
interface Person {
  name: string;
  age: number;
}
const person: Readonly<Person> = {
  name: "Dylan",
  age: 35,
};
person.name = 'Israel';

// compile error
// prog.ts(11,8): error TS2540: Cannot assign to 'name' because it is a read-only property.
```

************************************************

### TAKEAWAY - Utility Types

* `Partial` keyword makes all object properties optional.
* `Required` keyword makes all object properties required.
* `Record` gives a unique key type and value type.
* `Omit` removes key types from object.
* `Pick` keeps only specified key type in object.
* `Exclude` removes types from union.
* `ReturnType` gets function type.
* `Parameter` gets parameter type.
* `Readonly` makes all properties unable to bemodified.

KEYOF

<details>
 <summary><b>Section Code - src/code/keyof.ts</b></summary>

 [src/code/keyof](src/code/keyof.ts)

```ts
// keyof
// Example code for keyof.

import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

//one
interface Person {
 name: string,
 age: number
}

export function printPerson(person: Person, property: keyof Person) {
 log(`Using \`keyof Person\` to print ${property}: ${person[property]}`);
}

export let person = {
 name: "John",
 age: 40
};

// two
type StringMap = { [key: string]: unknown };

export function printStringMap(property: keyof StringMap, value: string) {
 return { [property]: value };
}

// keyof takeaway
export var keyofTakeAway = new takeAway("keyof");
keyofTakeAway.setTakeAway(
 "`keyof` keyword sets a union type when used with function type.",
 "`keyof` can be used with index signatures to get index type.");

```

</details>

<details>
 <summary><b>Section Code - src/progress/keyof.ts</b></summary>

 [src/progress/keyof](src/progress/keyof.ts)

```ts
// keyof
// Output code for keyof.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { log } from "../support/format";
import { keyofTakeAway } from "../code/keyof";
import { printPerson, person, printStringMap } from "../code/keyof";

export function runKeyof(): void {
 log("KEYOF");
 cl();
 cl("src/code/keyof");
 cl();
 cl("src/progress/keyof");
 cl();
 // one
 log("Using `keyof` keyword creates a union type on an object type with explicit keys.");
 cl();
 log(`Example:

\`\`\`ts
interface Person {
 name: string,
 age: number
}

function printPerson(person: Person, property: keyof Person) {
 console.log(\`Using \\\`keyof Person\\\` to print \${property}: \${person[property]}\`);
}

let person = {
 name: "John",
 age: 40
};

printPerson(person, "name");
// returns
/*`);
 printPerson(person, "name");
 log(`*/
 \`\`\`
 `);

 // two
 cl();
 log("When `keyof` keyword is used with index signatures it can get index type.");
 cl();
 log(`Example:

\`\`\`ts
type StringMap = { [key: string]: unknown };

function printStringMap(property: keyof StringMap, value: string) {
 return { [property]: value };
}

console.log(JSON.stringify(printStringMap("name", "John"));
// returns
/*`);
 log(JSON.stringify(printStringMap("name", "John")));
 log(`*/
\`\`\`
`);

 // output takeaway
 log(keyofTakeAway.outTakeAway());
}

```

</details>

Using `keyof` keyword creates a union type on an object type with explicit keys.

Example:

```ts
interface Person {
 name: string,
 age: number
}

function printPerson(person: Person, property: keyof Person) {
 console.log(`Using \`keyof Person\` to print ${property}: ${person[property]}`);
}

let person = {
 name: "John",
 age: 40
};

printPerson(person, "name");
// returns
/*
Using `keyof Person` to print name: John
*/
 ```

When `keyof` keyword is used with index signatures it can get index type.

Example:

```ts
type StringMap = { [key: string]: unknown };

function printStringMap(property: keyof StringMap, value: string) {
 return { [property]: value };
}

console.log(JSON.stringify(printStringMap("name", "John"));
// returns
/*
{"name":"John"}
*/
```

************************************************

### TAKEAWAY - keyof

* `keyof` keyword sets a union type when used with function type.
* `keyof` can be used with index signatures to get index type.

NULL

<details>
 <summary><b>Section Code - src/code/null.ts</b></summary>

 [src/code/null](src/code/null.ts)

```ts
// null
// Example code for null.

import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

// one
export let value: string | undefined | null = null;
export function setValue(val: string | undefined): void {
 value = val;
}
// two
interface House {
  sqft: number,
  yard?: {
    sqft: number,
  }
}
            
export function printYardSize(house: House) {
  const yardSize = house.yard?.sqft;

  if (yardSize === undefined) {
    console.log('No yard');
  } else {
    console.log(`Yard is ${yardSize} sqft`);
  }
}
            
export let home: House = {
  sqft: 500
};

export function setYardSize(val: number): void {
 home.yard = {
   sqft: val
 };
}

// three
export function printMileage(mileage: number | null | undefined) {
  console.log(`Mileage: ${mileage ?? 'Not Available'}`);
}

// four
function getValue(): string | undefined {
  return 'hello';
}
export let valueB = getValue();

// five
let array: number[] = [1, 2, 3];
export let valueC = array[3];

// set takeaways
export var nullTakeAway = new takeAway("null");
nullTakeAway.setTakeAway(
 "`null` and `undefined` by default are not handled, but can be set with `strictNullChecks = true`",
 `Set \`strictNullChecks\` in \`tsconfig.json\` like: 
'''json
{
  "compilerOptions": {
    "strictNullChecks": true,
    // other compiler options
  },
  // other tsconfig options
}
'''`,
 "`null` and `undefined` are primitive types.",
 "When `strucNullChecks` is set, values are required unless `undefined` is added to type.",
 "Use `??` in expression when handling `null` and `undefined` types.",
 "Use `!` after set value to ignore possible `null` and`undefined` values.",
 "By default TypeScript expects an arrays to not be `undefined`, but change with `noUncheckedIndexedAccess`.",
 `Set \`noUncheckedIndexedAccess\` in \`tsconfig.json\` like:
'''json
{
   "compilerOptions": {
     // ... other compiler options
     "noUncheckedIndexedAccess": true
   }
   // ... other tsconfig options
 }
'''
`
);
```

</details>

<details>
 <summary><b>Section Code - src/progress/null.ts</b></summary>

 [src/progress/null](src/progress/null.ts)

```ts
// null
// Output code for null.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { sideNote } from "../support/sideNotes";
import { log } from "../support/format";
import { nullTakeAway, value, setValue, setYardSize, printYardSize, home, printMileage, valueB, valueC } from "../code/null";

export function runNull(): void {
 log("NULL");
 cl();
 cl("src/code/null");
 cl();
 cl("src/progress/null");
 cl();
 
 // one
 log("`null` and `undefined` are primitives and can be used as such.");
 cl();
 log(`Example:

\`\`\`ts
let value: string | undefined | null = null;
console.log(typeof value);
// returns 
/*`);
 log(value);
 log(`*/

value = 'hello';
console.log(typeof value);
// returns
/*`);
 setValue("hello");
 log(value);
 log(`*/

value = undefined;
console.log(typeof value);
// returns
/*`);
 setValue(undefined);
 log(value);
 log(`*/
\`\`\`
`);
 
 // two
 cl();
 log("**Optional Chaining** can be used with `?` after property, and is useful when property may or may not be defined.");
 cl();
 log(`Example:

\`\`\`ts
interface House {
  sqft: number,
  yard?: {
    sqft: number,
  }
}
            
function printYardSize(house: House) {
  const yardSize = house.yard?.sqft;

  if (yardSize === undefined) {
    console.log('No yard');
  } else {
    console.log(\`Yard is \${yardSize} sqft\`);
  }
}
            
let home: House = {
  sqft: 500
};

printYardSize(home);
// returns
/*`);
 printYardSize(home);
 log(`*/
home.yard = {
  sqft: 100
};

printYardSize(home);
// returns
/*`);
 setYardSize(100);
 printYardSize(home);
 log(`*/
\`\`\`
`);

 // three
 cl();
 log("**Nullish coalescing** allows for expressiong that have fallback for `null`or `undefined` types. It is used with the `??` operator.");
 cl();
 log(`Example:

\`\`\`ts
function printMileage(mileage: number | null | undefined) {
  console.log(\`Mileage: \${mileage ?? 'Not Available'}\`);
}

printMileage(null);
// returns
/*`);
 printMileage(null);
 log(`*/
printMileage(0);
// returns
/*`);
 printMileage(0);
 log(`*/
\`\`\`
`);
 
 // four
 cl();
 log("**Null assertion** can be used with `!` after the set value, and is good for when checking `null` and `undefined` is not necessary.");
 cl();
 log(`Example:

\`\`\`ts
function getValue(): string | undefined {
  return 'hello';
}
let value = getValue();
console.log('value length: ' + value!.length);
// returns
/*`);
 log('value length: ' + valueB!.length);
 log(`*/
\`\`\`
`);
 cl();
 log(sideNote("Using **Null assertion** can be unsafe, and should be used sparingly and with care."));

 // five
 cl();
 log("By default TypeScript assumes arrays will not be `undefined` (*even with `strictNullChecks`*), but use `noUncheckedIndexedAccess` to change this.");
 cl();
 log(`Example:

\`\`\`ts
let array: number[] = [1, 2, 3];
let value = array[0];

console.log(value);
// returns
/*`)
 log(valueC);
 log(`*/
\`\`\`
`);
 cl();

 // output takeaway
 log(nullTakeAway.outTakeAway());
}

```

</details>

`null` and `undefined` are primitives and can be used as such.

Example:

```ts
let value: string | undefined | null = null;
console.log(typeof value);
// returns 
/*
null
*/

value = 'hello';
console.log(typeof value);
// returns
/*
hello
*/

value = undefined;
console.log(typeof value);
// returns
/*
undefined
*/
```

**Optional Chaining** can be used with `?` after property, and is useful when property may or may not be defined.

Example:

```ts
interface House {
  sqft: number,
  yard?: {
    sqft: number,
  }
}
            
function printYardSize(house: House) {
  const yardSize = house.yard?.sqft;

  if (yardSize === undefined) {
    console.log('No yard');
  } else {
    console.log(`Yard is ${yardSize} sqft`);
  }
}
            
let home: House = {
  sqft: 500
};

printYardSize(home);
// returns
/*
No yard
*/
home.yard = {
  sqft: 100
};

printYardSize(home);
// returns
/*
Yard is 100 sqft
*/
```

**Nullish coalescing** allows for expressiong that have fallback for `null`or `undefined` types. It is used with the `??` operator.

Example:

```ts
function printMileage(mileage: number | null | undefined) {
  console.log(`Mileage: ${mileage ?? 'Not Available'}`);
}

printMileage(null);
// returns
/*
Mileage: Not Available
*/
printMileage(0);
// returns
/*
Mileage: 0
*/
```

**Null assertion** can be used with `!` after the set value, and is good for when checking `null` and `undefined` is not necessary.

Example:

```ts
function getValue(): string | undefined {
  return 'hello';
}
let value = getValue();
console.log('value length: ' + value!.length);
// returns
/*
value length: 5
*/
```

> [!NOTE]
> Using **Null assertion** can be unsafe, and should be used sparingly and with care.

By default TypeScript assumes arrays will not be `undefined` (*even with `strictNullChecks`*), but use `noUncheckedIndexedAccess` to change this.

Example:

```ts
let array: number[] = [1, 2, 3];
let value = array[0];

console.log(value);
// returns
/*
undefined
*/
```

************************************************

### TAKEAWAY - null

* `null` and `undefined` by default are not handled, but can be set with `strictNullChecks = true`
* Set `strictNullChecks` in `tsconfig.json` like:

```json
{
  "compilerOptions": {
    "strictNullChecks": true,
    // other compiler options
  },
  // other tsconfig options
}
```

* `null` and `undefined` are primitive types.
* When `strucNullChecks` is set, values are required unless `undefined` is added to type.
* Use `??` in expression when handling `null` and `undefined` types.
* Use `!` after set value to ignore possible `null` and`undefined` values.
* By default TypeScript expects an arrays to not be `undefined`, but change with `noUncheckedIndexedAccess`.
* Set `noUncheckedIndexedAccess` in `tsconfig.json` like:

```json
{
   "compilerOptions": {
     // ... other compiler options
     "noUncheckedIndexedAccess": true
   }
   // ... other tsconfig options
 }
```

DEFINITELY TYPED

<details>
 <summary><b>Section Code - src/code/definitelyTyped.ts</b></summary>

 [src/code/definitelyTyped](src/code/definitelyTyped.ts)

```ts
// definitelyTyped
// Example code for definitelyTyped.

import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

export function outDownload():void {
 log("npm install --save-dev @types/jquery");
}

export var definitelyTypedTakeAway = new takeAway("Definitely Typed");
definitelyTypedTakeAway.setTakeAway(
 "Not all `npm` packages are safe to use with TypeScript.",
 "Install **Definitely Typed** with `npm install --save-dev @types/jquery`."
);
```

</details>

<details>
 <summary><b>Section Code - src/progress/definitelyTyped.ts</b></summary>

 [src/progress/definitelyTyped](src/progress/definitelyTyped.ts)

```ts
// definitelyTyped
// Output code for definitelyTyped.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { log } from "../support/format";
import { definitelyTypedTakeAway, outDownload } from "../code/definitelyTyped";

export function runDefinitelyTyped(): void {
 log("DEFINITELY TYPED");
 cl();
 cl("src/code/definitelyTyped");
 cl();
 cl("src/progress/definitelyTyped");
 cl();

 // one
 log("Some `npm` projects are not `type` safe, but using the package **Definitely Typed** can be used to compensate for this.");
 cl();
 log(`Download:

\`\`\`bash
`);
 outDownload();
log(`\`\`\`
`);
 cl();

 // output takeaway
 log(definitelyTypedTakeAway.outTakeAway()); 
}

```

</details>

Some `npm` projects are not `type` safe, but using the package **Definitely Typed** can be used to compensate for this.

Download:

```bash

npm install --save-dev @types/jquery
```

************************************************

### TAKEAWAY - Definitely Typed

* Not all `npm` packages are safe to use with TypeScript.
* Install **Definitely Typed** with `npm install --save-dev @types/jquery`.

## TYPESCRIPT UPDATES, CONFIGURATION, AND FRAMEWORKS

*****************************************

<details>
 <summary><b>Section Code - src/code/updates.ts</b></summary>

 [src/code/updates](src/code/updates.ts)

```ts
// updates
// Example code for updates.

import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

// one
type Color = "red" | "green" | "blue";
type HexColor<T extends Color> = `#${string}`;

// two
type DynamicObject = { [key: `dynamic_${string}`]: string };

// using
export let obj: DynamicObject ={ dynamic_key: "value" };

// using
export let theColor: HexColor<"blue"> = "#0000FF";

export var updatesTakeAway = new takeAway("Updates");
updatesTakeAway.setTakeAway(
 "**Template Literal Types** allow for more precise types.",
 "**Index Signature Labels** allow labeling index signatures using computed property names."
);
```

</details>

<details>
 <summary><b>Section Code - src/progress/updates.ts</b></summary>

 [src/progress/updates](src/progress/updates.ts)

```ts
// updates
// Output code for updates.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { log } from "../support/format";
import { updatesTakeAway, theColor, obj } from "../code/updates";

export function runUpdates(): void {
 sectionHeader("Updates, Configuration, and Frameworks", "new", "src/code/updates"); 
 cl();
 cl("src/progress/updates");
 cl();

 // one
 log(`In TypeScript version 5.x+ there are two main updates:

1. **Template Literal Types** - more specific types.
2. **Index Signature Labels** - label index signatures with computed property names.
`);
 cl();
 log(`Template Literal Types:

\`\`\`ts
type Color = "red" | "green" | "blue";
type HexColor<T extends Color> = \`#\${string}\`;

// using
let theColor: HexColor<"blue"> = "#0000FF";

console.log(theColor);
// returns
/*`);
 log(theColor);
 log(`*/
\`\`\`
`);

 // two
 cl();
 log(`Index Signature Labels:

\`\`\`ts
type DynamicObject = { [key: \`dynamic_\${string}\`]: string };

// using
let obj: DynamicObject ={ dynamic_key: "value" };

console.log(obj);
// returns
/*`);
 log(obj);
 log(`*/
\`\`\`
`);
 cl();

 // output takeaway
 log(updatesTakeAway.outTakeAway()); 
}

```

</details>

In TypeScript version 5.x+ there are two main updates:

1. **Template Literal Types** - more specific types.
2. **Index Signature Labels** - label index signatures with computed property names.

Template Literal Types:

```ts
type Color = "red" | "green" | "blue";
type HexColor<T extends Color> = `#${string}`;

// using
let theColor: HexColor<"blue"> = "#0000FF";

console.log(theColor);
// returns
/*
#0000FF
*/
```

Index Signature Labels:

```ts
type DynamicObject = { [key: `dynamic_${string}`]: string };

// using
let obj: DynamicObject ={ dynamic_key: "value" };

console.log(obj);
// returns
/*
[object Object]
*/
```

************************************************

### TAKEAWAY - Updates

* **Template Literal Types** allow for more precise types.
* **Index Signature Labels** allow labeling index signatures using computed property names.

CONFIGURATION

<details>
 <summary><b>Section Code - src/code/configuration.ts</b></summary>

 [src/code/configuration](src/code/configuration.ts)

```ts
// configuration
// Example code for configuration.

import { blankLine as cl } from "../support/sectionHeader";
import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

// one, three to six
interface Config {
 generate?: string,
 concepts?: {
  compilerOptions: string,
  include: string,
  exclude: string,
  files: string,
  extends: string,
  references: string
 },
 useCase?: {
  monorepo: string,
  library: string,
  app: string
 },
 troubleshoot?: {
  misconf: string,
  path: string,
  typeError: string
 },
 bestPractice?: {
  safe: string,
  extends: string,
  commits: string
 }
}

export var configTypeScript: Config = {
 concepts: {
  compilerOptions: "Controls how TypeScript compiles your code (e.g., target, module, strictness).",
  include: "Files or folders to include in the compilation.",
  exclude: "Files or folders to exclude.",
  files: "Explicit list of files to include (rarely used with include).",
  extends: "Inherit options from another config file.",
  references: "Enable project references for monorepos or multi-package setups."
 }
};

export function setConfigTypeScript(prop: keyof Config, val: any): void {
 (configTypeScript as any)[prop] = val;
}

export function outConfig(config: Config): void {
 cl();
 log("```text");
 cl();
 for (const prop in config) {
  const value = config[prop as keyof Config];
  if (value && typeof value === "object") {
   log(prop + ":");
   for (const subProp in value) {
    log("  " + subProp + " : " + (value as any)[subProp]);
   }
  } else if (value !== undefined) {
   log(prop + " : " + value);
  }
 }
 cl();
 log("```");
 cl();
}

export function outConfigProperty(obj: any): void {
 if (!obj) return;
 cl();
 log("```text");
 cl();
 if (typeof obj === "object") {
  for (const prop in obj) {
   log("  " + prop + " : " + obj[prop]);
  }
 } else {
  log(obj);
 }
 cl();
 log("```");
 cl();
}

// two
export function outConfigExample(cur: number): void {
 if (cur == 1) {
  log(`
**Basic Example**:

\`\`\`\json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs"
  },
  "include": ["src/**/*"]
}
\`\`\`
`);
 } else if (cur == 2) {
  log(`  
**Verbose Example**:

\`\`\`json
{
  "compilerOptions": {
    "target": "es2020",
    "module": "esnext",
    "strict": true,
    "baseUrl": ".",
    "paths": {
      "@app/*": ["src/app/*"]
    },
    "outDir": "dist",
    "esModuleInterop": true
  },
  "include": ["src"],
  "exclude": ["node_modules", "dist"]
}
\`\`\`
  `);
  }
}

export var configurationTakeAway = new takeAway("Configuration");
configurationTakeAway.setTakeAway(
 `Key concepts:

   - compilerOptions
   - include
   - exclude
   - files
   - extends
   - references
`,
 `Getting Started:

'''json
{
  "compilerOptions": {
    "target": "es2020",
    "module": "esnext",
    "strict": true,
    "baseUrl": ".",
    "paths": {
      "@app/*": ["src/app/*"]
    },
    "outDir": "dist",
    "esModuleInterop": true
  },
  "include": ["src"],
  "exclude": ["node_modules", "dist"]
}
'''
`, 
"To generate use `tsc --init`",
`Case uses: 

   1. \`monorepo\` use \`reference\` and \`extends\`.
   2. \`Library\` set \`declarations\` and \`outDir\` for type definitions.
   3. \`App\` use \`strict\` and \`esModuleInterop\` for compatibility.`,
`Common Erros:

   - Misuse of \`include / exclude\`.
   - Misconfigure \`baseUrl\` and \`paths\` cause path errors.
   - Type errors when changing \`strict\`.
`,
`Best Practices:

   - Use \`strict\` for safe code
   - Use \`extends\` avoids duplicating config in monorepo or other projects.
   - Do not include folders like \`dist\` in commits for version control.
`
);
```

</details>

<details>
 <summary><b>Section Code - src/progress/configuration.ts</b></summary>

 [src/progress/configuration](src/progress/configuration.ts)

```ts
// configuration
// Output code for configuration.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { log } from "../support/format";
import { configurationTakeAway, configTypeScript, outConfig, setConfigTypeScript, outConfigExample, outConfigProperty } from "../code/configuration";

export function runConfiguration(): void {
 log("CONFIGURATION");
 cl();
 cl("src/code/configuration");
 cl();
 cl("src/progress/configuration");
 cl();

 // one
 log("**Key Concepts** for `tsconfig.json`");
 cl();
 outConfig(configTypeScript);
 
 // two
 cl();
 log("`tsconfig.json` example configurations:");
 cl();
 outConfigExample(1);
 cl();
 outConfigExample(2);

 // three
 cl();
 log("To generate a `tscconfig.json` file run:");
 cl();
 setConfigTypeScript("generate", "tsc --init");
 log(`\`\`\`bash`);
 log(configTypeScript.generate || "");
 log(`\`\`\``);
 
 // four
 cl();
 log(`Use Cases for \`tsconfig.json\`:`);
 cl();
 setConfigTypeScript("useCase", {monorepo: "Use references and extends to share settings across packages.", library: "Set declaration and outDir for type definitions.", app: "Use strict and esModuleInterop for best compatibility."});
 outConfigProperty(configTypeScript.useCase);

 // five
 cl();
 log("Common errors of `tsconfig.json` are:");
 cl();
 setConfigTypeScript("troubleshoot", {misconf: "Misuse of `include/exclude` causes missed or unexpected inclusion of files.", path: "Paths are not resolved with `baseUrl` or `paths` properties.", typeError: "Changing `strict` can cause type errors."});
 outConfigProperty(configTypeScript.troubleshoot);

 // six
 cl();
 log("Some best practices for TypeScript are:");
 cl();
 setConfigTypeScript("bestPractice", {safe: "Using `strict` to keep code safe.", extends: "Use `extends` in order to not duplicate config in monorepos or other projects.", commits: "Not commititing output folder i.e. `dist` to version control." } );
 outConfigProperty(configTypeScript.bestPractice);

 // output takeaway
 log(configurationTakeAway.outTakeAway()); 
}

```

</details>

**Key Concepts** for `tsconfig.json`

```text

concepts:
  compilerOptions : Controls how TypeScript compiles your code (e.g., target, module, strictness).
  include : Files or folders to include in the compilation.
  exclude : Files or folders to exclude.
  files : Explicit list of files to include (rarely used with include).
  extends : Inherit options from another config file.
  references : Enable project references for monorepos or multi-package setups.

```

`tsconfig.json` example configurations:

**Basic Example**:

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs"
  },
  "include": ["src/**/*"]
}
```

**Verbose Example**:

```json
{
  "compilerOptions": {
    "target": "es2020",
    "module": "esnext",
    "strict": true,
    "baseUrl": ".",
    "paths": {
      "@app/*": ["src/app/*"]
    },
    "outDir": "dist",
    "esModuleInterop": true
  },
  "include": ["src"],
  "exclude": ["node_modules", "dist"]
}
```
  
To generate a `tscconfig.json` file run:

```bash
tsc --init
```

Use Cases for `tsconfig.json`:

```text

  monorepo : Use references and extends to share settings across packages.
  library : Set declaration and outDir for type definitions.
  app : Use strict and esModuleInterop for best compatibility.

```

Common errors of `tsconfig.json` are:

```text

  misconf : Misuse of `include/exclude` causes missed or unexpected inclusion of files.
  path : Paths are not resolved with `baseUrl` or `paths` properties.
  typeError : Changing `strict` can cause type errors.

```

Some best practices for TypeScript are:

```text

  safe : Using `strict` to keep code safe.
  extends : Use `extends` in order to not duplicate config in monorepos or other projects.
  commits : Not commititing output folder i.e. `dist` to version control.

```

************************************************

### TAKEAWAY - Configuration

* Key concepts:

  * compilerOptions
  * include
  * exclude
  * files
  * extends
  * references

* Getting Started:

```json
{
  "compilerOptions": {
    "target": "es2020",
    "module": "esnext",
    "strict": true,
    "baseUrl": ".",
    "paths": {
      "@app/*": ["src/app/*"]
    },
    "outDir": "dist",
    "esModuleInterop": true
  },
  "include": ["src"],
  "exclude": ["node_modules", "dist"]
}
```

* To generate use `tsc --init`
* Case uses:

   1. `monorepo` use `reference` and `extends`.
   2. `Library` set `declarations` and `outDir` for type definitions.
   3. `App` use `strict` and `esModuleInterop` for compatibility.
* Common Erros:

  * Misuse of `include / exclude`.
  * Misconfigure `baseUrl` and `paths` cause path errors.
  * Type errors when changing `strict`.

* Best Practices:

  * Use `strict` for safe code
  * Use `extends` avoids duplicating config in monorepo or other projects.
  * Do not include folders like `dist` in commits for version control.

NODEJS

<details>
 <summary><b>Section Code - src/code/nodeJS.ts</b></summary>

 [src/code/nodeJS](src/code/nodeJS.ts)

```ts
// nodeJS
// Example code for nodeJS.

import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

// Repeat output functions.
// For bash, text, and ts examples.
export function outText(val: string, heading: string, code: string):string {
 return `
**${heading}**
 
\`\`\`${code}
${val}
\`\`\`
`; 
}

// For longer bash, text, and ts examples.
export function outDetails(val: string, heading: string, code: string):string {
 return `
**${heading}**

<details>

<summary>Show Details</summary>

\`\`\`${code}
${val}
\`\`\`
</details>
`; 
}

// set takeaway
export var nodeJSTakeAway = new takeAway("NodeJS");
nodeJSTakeAway.setTakeAway(
 `New Project:

'''bash
mkdir my-ts-node-app
cd my-ts-node-app
npm init -y
npm install typescript @types/node --save-dev
npx tsc --init
'''
`,
"For most projects use `dist` as output folder."
);

```

</details>

<details>
 <summary><b>Section Code - src/progress/nodeJS.ts</b></summary>

 [src/progress/nodeJS](src/progress/nodeJS.ts)

```ts
// nodeJS
// Output code for nodeJS.

import { log } from "../support/format";
import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { sideNote } from "../support/sideNotes";
import { nodeJSTakeAway, outText, outDetails } from "../code/nodeJS";

export function runNodeJS(): void {
 log("NODEJS");
 cl();
 cl("src/code/nodeJS");
 cl();
 cl("src/progress/nodeJS");
 cl();

 // why use nodejs
 log(outText(`
- Type safety for JavaScript code
- Better IDE support with autocompletion
- Early error detection during development
- Improved code maintainability and documentation
- Easier refactoring
  `, "Why use NodeJS with TypeScript", "text"));

 // getting started
 log(outText(`
mkdir my-ts-node-app
cd my-ts-node-app
npm init -y
npm install typescript @types/node --save-dev
npx tsc --init
`, "Start TypeScript with NodeJS", "bash"));
 // out text
 log(outText(`
- typescript adds the TypeScript compiler (tsc)
- @types/node provides Node.js type definitions
- npx tsc --init creates a tsconfig.json config file  
`, "Getting Started Explained", "text"));

 // config tsconfig.json
 log(outDetails(`
{
    "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "sourceMap": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}  
`, "Generate tsconfig.json", "json"));
 // out text
 log(outText(`
- \`rootDir/outDir\`: keeps source (\`src\`) separate from build output (\`dist\`).
- \`strict\`: enables the safest type checking.
- \`esModuleInterop\`: smoother interop with CommonJS/ES modules.
- \`sourceMap\`: generate maps for debugging compiled code.
`, "Configed `tsconfig.json` Explained", "text"));

 // install dependencies
 log(outText(`
npm install express body-parser
npm install --save-dev ts-node nodemon @types/express
`, "Install for Runtime and Dev Dependencies", "bash"));
 
 // side note
 log(sideNote(`Use ts-node and nodemon only for development. For production, compile with tsc and run Node on the JS output.`));
 log(outText(`
my-ts-node-app/
  src/
    server.ts
    middleware/
      auth.ts
    entity/
      User.ts
    config/
      database.ts
  dist/
  node_modules/
  package.json
  tsconfig.json
`, "Example Project Structure", "text"));

 // output example
 log(outDetails(`
import express, { Request, Response, NextFunction } from 'express';
import { json } from 'body-parser';

interface User {
  id: number;
  username: string;
  email: string;
}

// Initialize Express app
const app = express();
const PORT = process.env.PORT || 3000;

// Middleware
app.use(json());

// In-memory database
const users: User[] = [
  { id: 1, username: 'user1', email: 'user1@example.com' },
  { id: 2, username: 'user2', email: 'user2@example.com' }
];

// Routes
app.get('/api/users', (req: Request, res: Response) => {
  res.json(users);
});

app.get('/api/users/:id', (req: Request, res: Response) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).json({ message: 'User not found' });
  res.json(user);
});

app.post('/api/users', (req: Request, res: Response) => {
  const { username, email } = req.body;
 
  if (!username || !email) {
    return res.status(400).json({ message: 'Username and email are required' });
  }
 
  const newUser: User = {
    id: users.length + 1,
    username,
    email
  };
 
  users.push(newUser);
  res.status(201).json(newUser);
});

// Error handling middleware
app.use((err: Error, req: Request, res: Response, next: NextFunction) => {
  console.error(err.stack);
  res.status(500).json({ message: 'Something went wrong!' });
});

// Start server
app.listen(PORT, () => {
  console.log(\`Server is running on http://localhost:\${PORT}\`);
});  
`, "Server Example at `src/server.ts`", "ts"));
 // server explained
 log(outText(`
- Typed \`Request\`, \`Response\`, and \`NextFunction\` for Express handlers.
- A \`User\` interface to guarantee the shape of user data.
- Safer refactoring and better autocompletion with typed route params and bodies.  
`, "`src/server.ts` Explained", "text"));

 // src/middleware/auth.ts
 log(outDetails(`
import { Request, Response, NextFunction } from 'express';

// Extend the Express Request type to include custom properties
declare global {
  namespace Express {
    interface Request {
      user?: { id: number; role: string };
    }
  }
}

export const authenticate = (req: Request, res: Response, next: NextFunction) => {
  const token = req.header('Authorization')?.replace('Bearer ', '');
 
  if (!token) {
    return res.status(401).json({ message: 'No token provided' });
  }
 
  try {
    // In a real app, verify the JWT token here
    const decoded = { id: 1, role: 'admin' }; // Mock decoded token
    req.user = decoded;
    next();
  } catch (error) {
    res.status(401).json({ message: 'Invalid token' });
  }
};

export const authorize = (roles: string[]) => {
  return (req: Request, res: Response, next: NextFunction) => {
    if (!req.user) {
      return res.status(401).json({ message: 'Not authenticated' });
    }
   
    if (!roles.includes(req.user.role)) {
      return res.status(403).json({ message: 'Not authorized' });
    }
   
    next();
  };
};  
`, "Example `src/middleware/auth.ts`", "ts"));
 // using auth.ts in server.ts
 log(outText(`
// src/server.ts
import { authenticate, authorize } from './middleware/auth';

app.get('/api/admin', authenticate, authorize(['admin']), (req, res) => {
  res.json({ message: \`Hello admin \${req.user?.id}\` });
});  
`, "Using in `src/server/ts`", "ts"));

 // database example
 log(outText(`
npm install typeorm reflect-metadata pg
`, "TypeScript with Database - TypeORM", "bash")); 
 log(outText(`
{
   "compilerOptions": {
     "experimentalDecorators": true, 
     "emitDecoratorMetadata": true 
   } 
}  
`, "Config `tsconfig.json`", "json"));
 // side note
 log(sideNote("Import reflect-metadata once at app startup."));
 // src/entity/User.ts
 log(outDetails(`
import { Entity, PrimaryGeneratedColumn, Column, CreateDateColumn, UpdateDateColumn } from 'typeorm';

@Entity('users')
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ unique: true })
  username: string;

  @Column({ unique: true })
  email: string;

  @Column({ select: false })
  password: string;

  @Column({ default: 'user' })
  role: string;

  @CreateDateColumn()
  createdAt: Date;

  @UpdateDateColumn()
  updatedAt: Date;
}  
`, "Example `src/entity/User.ts", "ts"));
 // src/config/database.ts
 log(outDetails(`
import 'reflect-metadata';
import { DataSource } from 'typeorm';
import { User } from '../entity/User';

export const AppDataSource = new DataSource({
  type: 'postgres',
  host: process.env.DB_HOST || 'localhost',
  port: parseInt(process.env.DB_PORT || '5432'),
  username: process.env.DB_USERNAME || 'postgres',
  password: process.env.DB_PASSWORD || 'postgres',
  database: process.env.DB_NAME || 'mydb',
  synchronize: process.env.NODE_ENV !== 'production',
  logging: false,
  entities: [User],
  migrations: [],
  subscribers: [],
});  
`, "Example `src/config/database.ts", "ts"));
 // using in src/server.ts
 log(outText(`
// src/server.ts
import { AppDataSource } from './config/database';

AppDataSource.initialize()
  .then(() => {
   app.listen(PORT, () => console.log(\`Server running on http://localhost:\${PORT}\`));
  })
  .catch((err) => {
   console.error('DB init error', err);
   process.exit(1);
  });
`, "Using in `src/server.ts`", "ts"));

 // development
 log("#### Development Steps");
 cl();
 log(outText(`
{
  "scripts": {
    "build": "tsc",
    "start": "node dist/server.js",
    "dev": "nodemon --exec ts-node src/server.ts",
    "watch": "tsc -w",
    "test": "jest --config jest.config.js"
  }
}
`, "Include in `package.json`", "json"));
 log(outText(`
# Development mode
npm run dev

# Production build
npm run build
npm start

# Debug
node --enable-source-maps dist/server.js
`, "Run Development Mode, Build for Production, and Debug", "bash"));
 
 // best practices
 log(outText(`
- Always define types for function parameters and return values
- Use interfaces for object shapes
- Enable strict mode in tsconfig.json
- Use type guards for runtime type checking
- Leverage TypeScript's utility types (Partial, Pick, Omit, etc.)
- Keep your type definitions in .d.ts files
- Use enums or const assertions for fixed sets of values
- Document complex types with JSDoc comments
- Prefer environment variables for secrets and config; validate them at startup.
- Use ts-node/nodemon only in dev; compile for prod.
- Consider ESLint + Prettier with @typescript-eslint for consistent code quality.
`, "TypeScript with NodeJS Best Practices", "text"));
 

 // output takeaway
 log(nodeJSTakeAway.outTakeAway());
}

```

</details>

**Why use NodeJS with TypeScript**

```text

- Type safety for JavaScript code
- Better IDE support with autocompletion
- Early error detection during development
- Improved code maintainability and documentation
- Easier refactoring
  
```

**Start TypeScript with NodeJS**

```bash

mkdir my-ts-node-app
cd my-ts-node-app
npm init -y
npm install typescript @types/node --save-dev
npx tsc --init

```

**Getting Started Explained**

```text

- typescript adds the TypeScript compiler (tsc)
- @types/node provides Node.js type definitions
- npx tsc --init creates a tsconfig.json config file  

```

**Generate tsconfig.json**

<details>

<summary>Show Details</summary>

```json

{
    "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "sourceMap": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}  

```

</details>

**Configed `tsconfig.json` Explained**

```text

- `rootDir/outDir`: keeps source (`src`) separate from build output (`dist`).
- `strict`: enables the safest type checking.
- `esModuleInterop`: smoother interop with CommonJS/ES modules.
- `sourceMap`: generate maps for debugging compiled code.

```

**Install for Runtime and Dev Dependencies**

```bash

npm install express body-parser
npm install --save-dev ts-node nodemon @types/express

```

> [!NOTE]
> Use ts-node and nodemon only for development. For production, compile with tsc and run Node on the JS output.

**Example Project Structure**

```text

my-ts-node-app/
  src/
    server.ts
    middleware/
      auth.ts
    entity/
      User.ts
    config/
      database.ts
  dist/
  node_modules/
  package.json
  tsconfig.json

```

**Server Example at `src/server.ts`**

<details>

<summary>Show Details</summary>

```ts

import express, { Request, Response, NextFunction } from 'express';
import { json } from 'body-parser';

interface User {
  id: number;
  username: string;
  email: string;
}

// Initialize Express app
const app = express();
const PORT = process.env.PORT || 3000;

// Middleware
app.use(json());

// In-memory database
const users: User[] = [
  { id: 1, username: 'user1', email: 'user1@example.com' },
  { id: 2, username: 'user2', email: 'user2@example.com' }
];

// Routes
app.get('/api/users', (req: Request, res: Response) => {
  res.json(users);
});

app.get('/api/users/:id', (req: Request, res: Response) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).json({ message: 'User not found' });
  res.json(user);
});

app.post('/api/users', (req: Request, res: Response) => {
  const { username, email } = req.body;
 
  if (!username || !email) {
    return res.status(400).json({ message: 'Username and email are required' });
  }
 
  const newUser: User = {
    id: users.length + 1,
    username,
    email
  };
 
  users.push(newUser);
  res.status(201).json(newUser);
});

// Error handling middleware
app.use((err: Error, req: Request, res: Response, next: NextFunction) => {
  console.error(err.stack);
  res.status(500).json({ message: 'Something went wrong!' });
});

// Start server
app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});  

```

</details>

**`src/server.ts` Explained**

```text

- Typed `Request`, `Response`, and `NextFunction` for Express handlers.
- A `User` interface to guarantee the shape of user data.
- Safer refactoring and better autocompletion with typed route params and bodies.  

```

**Example `src/middleware/auth.ts`**

<details>

<summary>Show Details</summary>

```ts

import { Request, Response, NextFunction } from 'express';

// Extend the Express Request type to include custom properties
declare global {
  namespace Express {
    interface Request {
      user?: { id: number; role: string };
    }
  }
}

export const authenticate = (req: Request, res: Response, next: NextFunction) => {
  const token = req.header('Authorization')?.replace('Bearer ', '');
 
  if (!token) {
    return res.status(401).json({ message: 'No token provided' });
  }
 
  try {
    // In a real app, verify the JWT token here
    const decoded = { id: 1, role: 'admin' }; // Mock decoded token
    req.user = decoded;
    next();
  } catch (error) {
    res.status(401).json({ message: 'Invalid token' });
  }
};

export const authorize = (roles: string[]) => {
  return (req: Request, res: Response, next: NextFunction) => {
    if (!req.user) {
      return res.status(401).json({ message: 'Not authenticated' });
    }
   
    if (!roles.includes(req.user.role)) {
      return res.status(403).json({ message: 'Not authorized' });
    }
   
    next();
  };
};  

```

</details>

**Using in `src/server/ts`**

```ts

// src/server.ts
import { authenticate, authorize } from './middleware/auth';

app.get('/api/admin', authenticate, authorize(['admin']), (req, res) => {
  res.json({ message: `Hello admin ${req.user?.id}` });
});  

```

**TypeScript with Database - TypeORM**

```bash

npm install typeorm reflect-metadata pg

```

**Config `tsconfig.json`**

```json

{
   "compilerOptions": {
     "experimentalDecorators": true, 
     "emitDecoratorMetadata": true 
   } 
}  

```

> [!NOTE]
> Import reflect-metadata once at app startup.

**Example `src/entity/User.ts**

<details>

<summary>Show Details</summary>

```ts

import { Entity, PrimaryGeneratedColumn, Column, CreateDateColumn, UpdateDateColumn } from 'typeorm';

@Entity('users')
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ unique: true })
  username: string;

  @Column({ unique: true })
  email: string;

  @Column({ select: false })
  password: string;

  @Column({ default: 'user' })
  role: string;

  @CreateDateColumn()
  createdAt: Date;

  @UpdateDateColumn()
  updatedAt: Date;
}  

```

</details>

**Example `src/config/database.ts**

<details>

<summary>Show Details</summary>

```ts

import 'reflect-metadata';
import { DataSource } from 'typeorm';
import { User } from '../entity/User';

export const AppDataSource = new DataSource({
  type: 'postgres',
  host: process.env.DB_HOST || 'localhost',
  port: parseInt(process.env.DB_PORT || '5432'),
  username: process.env.DB_USERNAME || 'postgres',
  password: process.env.DB_PASSWORD || 'postgres',
  database: process.env.DB_NAME || 'mydb',
  synchronize: process.env.NODE_ENV !== 'production',
  logging: false,
  entities: [User],
  migrations: [],
  subscribers: [],
});  

```

</details>

**Using in `src/server.ts`**

```ts

// src/server.ts
import { AppDataSource } from './config/database';

AppDataSource.initialize()
  .then(() => {
   app.listen(PORT, () => console.log(`Server running on http://localhost:${PORT}`));
  })
  .catch((err) => {
   console.error('DB init error', err);
   process.exit(1);
  });

```

#### Development Steps

**Include in `package.json`**

```json

{
  "scripts": {
    "build": "tsc",
    "start": "node dist/server.js",
    "dev": "nodemon --exec ts-node src/server.ts",
    "watch": "tsc -w",
    "test": "jest --config jest.config.js"
  }
}

```

**Run Development Mode, Build for Production, and Debug**

```bash

# Development mode
npm run dev

# Production build
npm run build
npm start

# Debug
node --enable-source-maps dist/server.js

```

**TypeScript with NodeJS Best Practices**

```text

- Always define types for function parameters and return values
- Use interfaces for object shapes
- Enable strict mode in tsconfig.json
- Use type guards for runtime type checking
- Leverage TypeScript's utility types (Partial, Pick, Omit, etc.)
- Keep your type definitions in .d.ts files
- Use enums or const assertions for fixed sets of values
- Document complex types with JSDoc comments
- Prefer environment variables for secrets and config; validate them at startup.
- Use ts-node/nodemon only in dev; compile for prod.
- Consider ESLint + Prettier with @typescript-eslint for consistent code quality.

```

************************************************

### TAKEAWAY - NodeJS

* New Project:

```bash
mkdir my-ts-node-app
cd my-ts-node-app
npm init -y
npm install typescript @types/node --save-dev
npx tsc --init
```

* For most projects use `dist` as output folder.

REACT

<details>
 <summary><b>Section Code - src/code/react.ts</b></summary>

 [src/code/react](src/code/react.ts)

```ts
// react
// Example code for react.

import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

// Repeat output functions.
// For bash, text, tsx, and json examples.
export function outText(val: string, heading: string, code: string):string {
 return `
**${heading}**
 
\`\`\`${code}
${val}
\`\`\`
`; 
}

// For longer bash, text, tsx, and json examples.
export function outDetails(val: string, heading: string, code: string):string {
 return `
**${heading}**

<details>

<summary>Show Details</summary>

\`\`\`${code}
${val}
\`\`\`
</details>
`; 
}

// set takeaway
export var reactTakeAway = new takeAway("React");
reactTakeAway.setTakeAway(
 `New React + TypeScript Project with Vite:

'''bash
npm create vite@latest my-app -- --template react-ts
cd my-app
npm install
npm run dev
'''
`,
"Always enable `strict` mode in `tsconfig.json` for best type safety.",
"Use `React.ReactNode` for children props.",
"Type event handlers explicitly: `React.ChangeEvent<HTMLInputElement>`, `React.MouseEvent<HTMLButtonElement>`.",
"Prefer direct function component typing over `React.FC`."
);

```

</details>

<details>
 <summary><b>Section Code - src/progress/react.ts</b></summary>

 [src/progress/react](src/progress/react.ts)

```ts
// react
// Output code for react.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { log } from "../support/format";
import { sideNote } from "../support/sideNotes";
import { reactTakeAway, outText, outDetails } from "../code/react";

export function runReact(): void {
 log("REACT");
 cl();
 cl("src/code/react");
 cl();
 cl("src/progress/react");
 cl();

 // why use react with typescript
 log(outText(`
- Type safety for props, state, and context
- Better IDE autocompletion and refactoring
- Early error detection during development
  `, "Why use React with TypeScript", "text"));

 // getting started
 log(outText(`
npm create vite@latest my-app -- --template react-ts
cd my-app
npm install
npm run dev
`, "Create React + TypeScript App with Vite", "bash"));

 // side note
 log(sideNote(`This tutorial assumes basic knowledge of React.`));

 // config tsconfig.json
 log(outDetails(`
{
  "compilerOptions": {
    "target": "ES2020",
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "moduleResolution": "Node",
    "jsx": "react-jsx",
    "strict": true,
    "skipLibCheck": true,
    "noEmit": true,
    "resolveJsonModule": true,
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": ["src"]
}
`, "Recommended `tsconfig.json` for React", "json"));

 // side note
 log(sideNote(`Keep 'strict' enabled for best type safety. These options work well with Vite and Create React App.`));

 // component typing
 log("#### Component Typing");
 cl();
 log(outText(`
// Greeting.tsx
type GreetingProps = {
  name: string;
  age?: number;
};

export function Greeting({ name, age }: GreetingProps) {
  return (
    <div>
      <h2>Hello, {name}!</h2>
      {age !== undefined && <p>You are {age} years old</p>}
    </div>
  );
}
`, "Functional Component with Typed Props", "tsx"));

 // common patterns
 log("#### Common Patterns");
 cl();

 // type-safe events
 log(outText(`
// Input change
function NameInput() {
  function handleChange(e: React.ChangeEvent<HTMLInputElement>) {
    console.log(e.target.value);
  }
  return <input onChange={handleChange} />;
}

// Button click
function SaveButton() {
  function handleClick(e: React.MouseEvent<HTMLButtonElement>) {
    e.preventDefault();
  }
  return <button onClick={handleClick}>Save</button>;
}
`, "Type-Safe Event Handlers", "tsx"));

 // typing state with useState
 log(outText(`
const [count, setCount] = React.useState<number>(0);
const [status, setStatus] = React.useState<'idle' | 'loading' | 'error'>('idle');

type User = { id: string; name: string };
const [user, setUser] = React.useState<User | null>(null);
`, "Typing State with useState", "tsx"));

 // useRef with DOM elements
 log(outText(`
function FocusInput() {
  const inputRef = React.useRef<HTMLInputElement>(null);
  return <input ref={inputRef} onFocus={() => inputRef.current?.select()} />;
}
`, "useRef with DOM Elements", "tsx"));

 // children typing
 log(outText(`
type CardProps = { title: string; children?: React.ReactNode };

function Card({ title, children }: CardProps) {
  return (
    <div>
      <h2>{title}</h2>
      {children}
    </div>
  );
}
`, "Children Typing with React.ReactNode", "tsx"));

 // fetch helpers with generics
 log(outDetails(`
async function fetchJson<T>(url: string): Promise<T> {
  const res = await fetch(url);
  if (!res.ok) throw new Error('Network error');
  return res.json() as Promise<T>;
}

// Usage inside an async function/component effect
async function loadPosts() {
  type Post = { id: number; title: string };
  const posts = await fetchJson<Post[]>("/api/posts");
  console.log(posts);
}
`, "Fetch Helpers with Generics", "tsx"));

 // minimal context and custom hook
 log(outDetails(`
type Theme = 'light' | 'dark';
const ThemeContext = React.createContext<{ theme: Theme; toggle(): void } | null>(null);

function ThemeProvider({ children }: { children: React.ReactNode }) {
  const [theme, setTheme] = React.useState<Theme>('light');
  const value = { theme, toggle: () => setTheme(t => (t === 'light' ? 'dark' : 'light')) };
  return <ThemeContext.Provider value={value}>{children}</ThemeContext.Provider>;
}

function useTheme() {
  const ctx = React.useContext(ThemeContext);
  if (!ctx) throw new Error('useTheme must be used within ThemeProvider');
  return ctx;
}
`, "Context with Custom Hook", "tsx"));

 // vite typescript types
 log(outText(`
// src/vite-env.d.ts
/// <reference types="vite/client" />
`, "Add Vite's Ambient Types", "ts"));

 // or in tsconfig.json
 log(outText(`
{
  "compilerOptions": {
    "types": ["vite/client"]
  }
}
`, "Alternatively in `tsconfig.json`", "json"));

 // side note
 log(sideNote(`About React.FC: Prefer directly typed function components. 'React.FC' is optional; it implicitly adds 'children' but isn't required.`));

 // optional baseUrl and paths
 log(outText(`
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  }
}
`, "Optional baseUrl and paths for Import Aliases", "json"));

 // side note
 log(sideNote(`Configure path aliases only if your tooling (e.g., Vite, tsconfig-paths) supports them.`));

 // best practices
 log(outText(`
- Enable strict mode in tsconfig.json for maximum type safety
- Define types for all props, state, and context
- Use React.ReactNode for children props
- Type event handlers explicitly (React.ChangeEvent, React.MouseEvent)
- Prefer direct function component typing over React.FC
- Use generics for reusable components and API calls
- Leverage TypeScript utility types (Partial, Pick, Omit, etc.)
- Add proper null checks when using refs and context
- Keep your type definitions close to where they're used
- Use union types for state machines (e.g., 'idle' | 'loading' | 'error')
`, "TypeScript with React Best Practices", "text"));

 // output takeaway
 log(reactTakeAway.outTakeAway());
}

```

</details>

**Why use React with TypeScript**

```text

- Type safety for props, state, and context
- Better IDE autocompletion and refactoring
- Early error detection during development
  
```

**Create React + TypeScript App with Vite**

```bash

npm create vite@latest my-app -- --template react-ts
cd my-app
npm install
npm run dev

```

> [!NOTE]
> This tutorial assumes basic knowledge of React.

**Recommended `tsconfig.json` for React**

<details>

<summary>Show Details</summary>

```json

{
  "compilerOptions": {
    "target": "ES2020",
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "moduleResolution": "Node",
    "jsx": "react-jsx",
    "strict": true,
    "skipLibCheck": true,
    "noEmit": true,
    "resolveJsonModule": true,
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": ["src"]
}

```

</details>

> [!NOTE]
> Keep 'strict' enabled for best type safety. These options work well with Vite and Create React App.
>
#### Component Typing

**Functional Component with Typed Props**

```tsx

// Greeting.tsx
type GreetingProps = {
  name: string;
  age?: number;
};

export function Greeting({ name, age }: GreetingProps) {
  return (
    <div>
      <h2>Hello, {name}!</h2>
      {age !== undefined && <p>You are {age} years old</p>}
    </div>
  );
}

```

#### Common Patterns

**Type-Safe Event Handlers**

```tsx

// Input change
function NameInput() {
  function handleChange(e: React.ChangeEvent<HTMLInputElement>) {
    console.log(e.target.value);
  }
  return <input onChange={handleChange} />;
}

// Button click
function SaveButton() {
  function handleClick(e: React.MouseEvent<HTMLButtonElement>) {
    e.preventDefault();
  }
  return <button onClick={handleClick}>Save</button>;
}

```

**Typing State with useState**

```tsx

const [count, setCount] = React.useState<number>(0);
const [status, setStatus] = React.useState<'idle' | 'loading' | 'error'>('idle');

type User = { id: string; name: string };
const [user, setUser] = React.useState<User | null>(null);

```

**useRef with DOM Elements**

```tsx

function FocusInput() {
  const inputRef = React.useRef<HTMLInputElement>(null);
  return <input ref={inputRef} onFocus={() => inputRef.current?.select()} />;
}

```

**Children Typing with React.ReactNode**

```tsx

type CardProps = { title: string; children?: React.ReactNode };

function Card({ title, children }: CardProps) {
  return (
    <div>
      <h2>{title}</h2>
      {children}
    </div>
  );
}

```

**Fetch Helpers with Generics**

<details>

<summary>Show Details</summary>

```tsx

async function fetchJson<T>(url: string): Promise<T> {
  const res = await fetch(url);
  if (!res.ok) throw new Error('Network error');
  return res.json() as Promise<T>;
}

// Usage inside an async function/component effect
async function loadPosts() {
  type Post = { id: number; title: string };
  const posts = await fetchJson<Post[]>("/api/posts");
  console.log(posts);
}

```

</details>

**Context with Custom Hook**

<details>

<summary>Show Details</summary>

```tsx

type Theme = 'light' | 'dark';
const ThemeContext = React.createContext<{ theme: Theme; toggle(): void } | null>(null);

function ThemeProvider({ children }: { children: React.ReactNode }) {
  const [theme, setTheme] = React.useState<Theme>('light');
  const value = { theme, toggle: () => setTheme(t => (t === 'light' ? 'dark' : 'light')) };
  return <ThemeContext.Provider value={value}>{children}</ThemeContext.Provider>;
}

function useTheme() {
  const ctx = React.useContext(ThemeContext);
  if (!ctx) throw new Error('useTheme must be used within ThemeProvider');
  return ctx;
}

```

</details>

**Add Vite's Ambient Types**

```ts

// src/vite-env.d.ts
/// <reference types="vite/client" />

```

**Alternatively in `tsconfig.json`**

```json

{
  "compilerOptions": {
    "types": ["vite/client"]
  }
}

```

> [!NOTE]
> About React.FC: Prefer directly typed function components. 'React.FC' is optional; it implicitly adds 'children' but isn't required.

**Optional baseUrl and paths for Import Aliases**

```json

{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  }
}

```

> [!NOTE]
> Configure path aliases only if your tooling (e.g., Vite, tsconfig-paths) supports them.

**TypeScript with React Best Practices**

```text

- Enable strict mode in tsconfig.json for maximum type safety
- Define types for all props, state, and context
- Use React.ReactNode for children props
- Type event handlers explicitly (React.ChangeEvent, React.MouseEvent)
- Prefer direct function component typing over React.FC
- Use generics for reusable components and API calls
- Leverage TypeScript utility types (Partial, Pick, Omit, etc.)
- Add proper null checks when using refs and context
- Keep your type definitions close to where they're used
- Use union types for state machines (e.g., 'idle' | 'loading' | 'error')

```

************************************************

### TAKEAWAY - React

* New React + TypeScript Project with Vite:

```bash
npm create vite@latest my-app -- --template react-ts
cd my-app
npm install
npm run dev
```

* Always enable `strict` mode in `tsconfig.json` for best type safety.
* Use `React.ReactNode` for children props.
* Type event handlers explicitly: `React.ChangeEvent<HTMLInputElement>`, `React.MouseEvent<HTMLButtonElement>`.
* Prefer direct function component typing over `React.FC`.

TOOLING

<details>
 <summary><b>Section Code - src/code/tooling.ts</b></summary>

 [src/code/tooling](src/code/tooling.ts)

```ts
// tooling
// Example code for tooling.

import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

// Repeat output functions.
// For bash, text, json, js, and ts examples.
export function outText(val: string, heading: string, code: string):string {
 return `
**${heading}**
 
\`\`\`${code}
${val}
\`\`\`
`; 
}

// For longer bash, text, json, js, and ts examples.
export function outDetails(val: string, heading: string, code: string):string {
 return `
**${heading}**

<details>

<summary>Show Details</summary>

\`\`\`${code}
${val}
\`\`\`
</details>
`; 
}

// set takeaway
export var toolingTakeAway = new takeAway("Tooling");
toolingTakeAway.setTakeAway(
 `TypeScript Development Ecosystem:

   - Code Quality: ESLint with TypeScript support
   - Development: VS Code integration, debugging tools, HMR
   - Build & Deploy: Vite, Webpack, Parcel
`,
"Vite is the recommended choice for fast dev server and modern builds.",
"Use 'eslint-config-prettier' to avoid ESLint and Prettier conflicts.",
"Enable 'strict' mode in tsconfig.json for best type safety.",
"Recommended VS Code extensions: ESLint, Prettier, Error Lens, Path IntelliSense."
);

```

</details>

<details>
 <summary><b>Section Code - src/progress/tooling.ts</b></summary>

 [src/progress/tooling](src/progress/tooling.ts)

```ts
// tooling
// Output code for tooling.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { log } from "../support/format";
import { sideNote } from "../support/sideNotes";
import { toolingTakeAway, outText, outDetails } from "../code/tooling";

export function runTooling(): void {
 log("TOOLING");
 cl();
 cl("src/code/tooling");
 cl();
 cl("src/progress/tooling");
 cl();

 // typescript development ecosystem
 log("#### TypeScript Development Ecosystem");
 cl();
 log(outText(`
- Code Quality: ESLint with TypeScript support, type checking, code style enforcement
- Development: VS Code integration, debugging tools, Hot Module Replacement (HMR)
- Build & Deploy: Bundlers (Vite, Webpack, Parcel), module bundling, production optimization
  `, "TypeScript's Tooling Strengths", "text"));

 // linting with eslint
 log("#### Linting with ESLint");
 cl();
 log(outText(`
npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
`, "Install ESLint with TypeScript Support", "bash"));

 log(outDetails(`
// .eslintrc.json
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": ["@typescript-eslint"],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:@typescript-eslint/recommended-requiring-type-checking"
  ],
  "parserOptions": {
    "project": "./tsconfig.json",
    "ecmaVersion": 2020,
    "sourceType": "module"
  },
  "rules": {
    "@typescript-eslint/explicit-function-return-type": "warn",
    "@typescript-eslint/no-explicit-any": "warn",
    "@typescript-eslint/no-unused-vars": ["error", { "argsIgnorePattern": "^_" }]
  }
}
`, "ESLint Configuration", "json"));

 log(outText(`
// package.json
{
  "scripts": {
    "lint": "eslint . --ext .ts,.tsx",
    "lint:fix": "eslint . --ext .ts,.tsx --fix",
    "type-check": "tsc --noEmit"
  }
}
`, "NPM Scripts for Linting", "json"));

 // side note
 log(sideNote(`Use 'lint:fix' to auto-fix simple issues.`));

 // code formatting with prettier
 log("#### Code Formatting with Prettier");
 cl();
 log(outText(`
npm install --save-dev prettier eslint-config-prettier eslint-plugin-prettier
`, "Install Prettier and Related Packages", "bash"));

 log(outText(`
// .prettierrc
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "printWidth": 100,
  "trailingComma": "es5",
  "bracketSpacing": true,
  "arrowParens": "avoid"
}

// .prettierignore
node_modules
build
dist
.next
.vscode
`, "Prettier Configuration", "text"));

 log(outText(`
// .eslintrc.json
{
  "extends": [
    // ... other configs
    "plugin:prettier/recommended" // Must be last in the array
  ]
}
`, "Integrate Prettier with ESLint", "json"));

 // modern build tools
 log("#### Modern Build Tools");
 cl();

 // vite
 log(outText(`
npm create vite@latest my-app -- --template react-ts
cd my-app
npm install
npm run dev
`, "Vite (Recommended) - Create React + TypeScript Project", "bash"));

 // side note
 log(sideNote(`Vite starts a dev server with HMR for rapid feedback.`));

 // webpack configuration
 log(outDetails(`
// webpack.config.js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.tsx',
  module: {
    rules: [
      {
        test: /\\.(ts|tsx)$/,
        use: 'ts-loader',
        exclude: /node_modules/,
      },
      {
        test: /\\.css$/,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
  resolve: {
    extensions: ['.tsx', '.ts', '.js'],
  },
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './public/index.html',
    }),
  ],
  devServer: {
    static: path.join(__dirname, 'dist'),
    compress: true,
    port: 3000,
  },
};
`, "Webpack Configuration", "js"));

 // typescript configuration
 log(outDetails(`
// tsconfig.json
{
  "compilerOptions": {
    "target": "es2020",
    "module": "esnext",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  },
  "include": ["src"],
  "exclude": ["node_modules"]
}
`, "TypeScript Configuration for Build Tools", "json"));

 // side note
 log(sideNote(`The optional 'baseUrl' and 'paths' help with absolute imports like '@/components/Button'.`));

 // development environment setup
 log("#### Development Environment Setup");
 cl();

 // vs code extensions
 log(outText(`
- TypeScript + Webpack Problem Matchers: Better error reporting
- ESLint: Integrates ESLint into VS Code
- Prettier - Code formatter: Consistent code formatting
- Path IntelliSense: Autocomplete filenames
- Error Lens: Show errors inline
  `, "Recommended VS Code Extensions", "text"));

 // vs code settings
 log(outDetails(`
// .vscode/settings.json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.organizeImports": true
  },
  "eslint.validate": ["javascript", "javascriptreact", "typescript", "typescriptreact"],
  "typescript.tsdk": "node_modules/typescript/lib",
  "typescript.preferences.importModuleSpecifier": "non-relative"
}
`, "VS Code Settings", "json"));

 // debugging configuration
 log(outDetails(`
// .vscode/launch.json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "chrome",
      "request": "launch",
      "name": "Launch Chrome against localhost",
      "url": "http://localhost:3000",
      "webRoot": "\${workspaceFolder}",
      "sourceMaps": true,
      "sourceMapPathOverrides": {
        "webpack:///./~/*": "\${workspaceFolder}/node_modules/*",
        "webpack:///./*": "\${workspaceFolder}/src/*"
      }
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Debug Tests",
      "runtimeExecutable": "\${workspaceRoot}/node_modules/.bin/jest",
      "args": ["--runInBand", "--no-cache"],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen"
    }
  ]
}
`, "VS Code Debugging Configuration", "json"));

 // testing setup
 log("#### Testing Setup");
 cl();
 log(outText(`
npm install --save-dev jest @types/jest ts-jest @testing-library/react @testing-library/jest-dom @testing-library/user-event
`, "Install Jest + Testing Library", "bash"));

 log(outDetails(`
// jest.config.js
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: ['@testing-library/jest-dom'],
  moduleNameMapper: {
    '^@/(.*)$': '<rootDir>/src/$1',
    '\\\\.(css|less|scss|sass)$': 'identity-obj-proxy',
  },
  transform: {
    '^.+\\\\.tsx?$': 'ts-jest',
  },
  testMatch: ['**/__tests__/**/*.test.(ts|tsx)'],
};
`, "Jest Configuration", "js"));

 log(outDetails(`
// src/__tests__/Button.test.tsx
import React from 'react';
import { render, screen, fireEvent } from '@testing-library/react';
import '@testing-library/jest-dom';
import Button from '../components/Button';

describe('Button', () => {
  it('renders button with correct text', () => {
    render(<Button>Click me</Button>);
    expect(screen.getByRole('button', { name: /click me/i })).toBeInTheDocument();
  });

  it('calls onClick when clicked', () => {
    const handleClick = jest.fn();
    render(<Button onClick={handleClick}>Click me</Button>);
    
    fireEvent.click(screen.getByRole('button'));
    expect(handleClick).toHaveBeenCalledTimes(1);
  });
});
`, "Example Test with Testing Library", "tsx"));

 // best practices
 log("#### Best Practices");
 cl();
 log(outText(`
Development Workflow:
- Use 'npm run dev' for development with hot reloading
- Run 'npm run type-check' to verify TypeScript types
- Use 'npm run lint' to check for linting errors
- Run 'npm run build' to create production build

Performance Optimization:
- Use code splitting with dynamic imports
- Enable tree-shaking in production builds
- Use React.memo and useMemo for expensive computations
- Lazy load non-critical components
  `, "Development Workflow and Performance", "text"));

 // common pitfalls
 log(outText(`
- TypeScript configuration: Ensure 'strict' mode is enabled
- ESLint + Prettier conflicts: Use 'eslint-config-prettier' to disable conflicting rules
- Slow builds: Consider using Vite or esbuild for faster development
- Missing type definitions: Install '@types' packages for all dependencies
- Debugging issues: Ensure source maps are properly configured
  `, "Common Pitfalls to Avoid", "text"));

 // recommended tools
 log(outText(`
- Bundlers: Vite, Webpack, Parcel
- Testing: Jest, React Testing Library, Cypress
- Linting/Formatting: ESLint, Prettier, Stylelint
- Documentation: TypeDoc, Storybook
- Performance: Web Vitals, Lighthouse
  `, "Recommended Tools", "text"));

 // output takeaway
 log(toolingTakeAway.outTakeAway());
}

```

</details>

#### TypeScript Development Ecosystem

**TypeScript's Tooling Strengths**

```text

- Code Quality: ESLint with TypeScript support, type checking, code style enforcement
- Development: VS Code integration, debugging tools, Hot Module Replacement (HMR)
- Build & Deploy: Bundlers (Vite, Webpack, Parcel), module bundling, production optimization
  
```

#### Linting with ESLint

**Install ESLint with TypeScript Support**

```bash

npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin

```

**ESLint Configuration**

<details>

<summary>Show Details</summary>

```json

// .eslintrc.json
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": ["@typescript-eslint"],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:@typescript-eslint/recommended-requiring-type-checking"
  ],
  "parserOptions": {
    "project": "./tsconfig.json",
    "ecmaVersion": 2020,
    "sourceType": "module"
  },
  "rules": {
    "@typescript-eslint/explicit-function-return-type": "warn",
    "@typescript-eslint/no-explicit-any": "warn",
    "@typescript-eslint/no-unused-vars": ["error", { "argsIgnorePattern": "^_" }]
  }
}

```

</details>

**NPM Scripts for Linting**

```json

// package.json
{
  "scripts": {
    "lint": "eslint . --ext .ts,.tsx",
    "lint:fix": "eslint . --ext .ts,.tsx --fix",
    "type-check": "tsc --noEmit"
  }
}

```

> [!NOTE]
> Use 'lint:fix' to auto-fix simple issues.
>
#### Code Formatting with Prettier

**Install Prettier and Related Packages**

```bash

npm install --save-dev prettier eslint-config-prettier eslint-plugin-prettier

```

**Prettier Configuration**

```text

// .prettierrc
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "printWidth": 100,
  "trailingComma": "es5",
  "bracketSpacing": true,
  "arrowParens": "avoid"
}

// .prettierignore
node_modules
build
dist
.next
.vscode

```

**Integrate Prettier with ESLint**

```json

// .eslintrc.json
{
  "extends": [
    // ... other configs
    "plugin:prettier/recommended" // Must be last in the array
  ]
}

```

#### Modern Build Tools

**Vite (Recommended) - Create React + TypeScript Project**

```bash

npm create vite@latest my-app -- --template react-ts
cd my-app
npm install
npm run dev

```

> [!NOTE]
> Vite starts a dev server with HMR for rapid feedback.

**Webpack Configuration**

<details>

<summary>Show Details</summary>

```js

// webpack.config.js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.tsx',
  module: {
    rules: [
      {
        test: /\.(ts|tsx)$/,
        use: 'ts-loader',
        exclude: /node_modules/,
      },
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
  resolve: {
    extensions: ['.tsx', '.ts', '.js'],
  },
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './public/index.html',
    }),
  ],
  devServer: {
    static: path.join(__dirname, 'dist'),
    compress: true,
    port: 3000,
  },
};

```

</details>

**TypeScript Configuration for Build Tools**

<details>

<summary>Show Details</summary>

```json

// tsconfig.json
{
  "compilerOptions": {
    "target": "es2020",
    "module": "esnext",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  },
  "include": ["src"],
  "exclude": ["node_modules"]
}

```

</details>

> [!NOTE]
> The optional 'baseUrl' and 'paths' help with absolute imports like '@/components/Button'.
>
#### Development Environment Setup

**Recommended VS Code Extensions**

```text

- TypeScript + Webpack Problem Matchers: Better error reporting
- ESLint: Integrates ESLint into VS Code
- Prettier - Code formatter: Consistent code formatting
- Path IntelliSense: Autocomplete filenames
- Error Lens: Show errors inline
  
```

**VS Code Settings**

<details>

<summary>Show Details</summary>

```json

// .vscode/settings.json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.organizeImports": true
  },
  "eslint.validate": ["javascript", "javascriptreact", "typescript", "typescriptreact"],
  "typescript.tsdk": "node_modules/typescript/lib",
  "typescript.preferences.importModuleSpecifier": "non-relative"
}

```

</details>

**VS Code Debugging Configuration**

<details>

<summary>Show Details</summary>

```json

// .vscode/launch.json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "chrome",
      "request": "launch",
      "name": "Launch Chrome against localhost",
      "url": "http://localhost:3000",
      "webRoot": "${workspaceFolder}",
      "sourceMaps": true,
      "sourceMapPathOverrides": {
        "webpack:///./~/*": "${workspaceFolder}/node_modules/*",
        "webpack:///./*": "${workspaceFolder}/src/*"
      }
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Debug Tests",
      "runtimeExecutable": "${workspaceRoot}/node_modules/.bin/jest",
      "args": ["--runInBand", "--no-cache"],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen"
    }
  ]
}

```

</details>

#### Testing Setup

**Install Jest + Testing Library**

```bash

npm install --save-dev jest @types/jest ts-jest @testing-library/react @testing-library/jest-dom @testing-library/user-event

```

**Jest Configuration**

<details>

<summary>Show Details</summary>

```js

// jest.config.js
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: ['@testing-library/jest-dom'],
  moduleNameMapper: {
    '^@/(.*)$': '<rootDir>/src/$1',
    '\\.(css|less|scss|sass)$': 'identity-obj-proxy',
  },
  transform: {
    '^.+\\.tsx?$': 'ts-jest',
  },
  testMatch: ['**/__tests__/**/*.test.(ts|tsx)'],
};

```

</details>

**Example Test with Testing Library**

<details>

<summary>Show Details</summary>

```tsx

// src/__tests__/Button.test.tsx
import React from 'react';
import { render, screen, fireEvent } from '@testing-library/react';
import '@testing-library/jest-dom';
import Button from '../components/Button';

describe('Button', () => {
  it('renders button with correct text', () => {
    render(<Button>Click me</Button>);
    expect(screen.getByRole('button', { name: /click me/i })).toBeInTheDocument();
  });

  it('calls onClick when clicked', () => {
    const handleClick = jest.fn();
    render(<Button onClick={handleClick}>Click me</Button>);
    
    fireEvent.click(screen.getByRole('button'));
    expect(handleClick).toHaveBeenCalledTimes(1);
  });
});

```

</details>

#### Best Practices

**Development Workflow and Performance**

```text

Development Workflow:
- Use 'npm run dev' for development with hot reloading
- Run 'npm run type-check' to verify TypeScript types
- Use 'npm run lint' to check for linting errors
- Run 'npm run build' to create production build

Performance Optimization:
- Use code splitting with dynamic imports
- Enable tree-shaking in production builds
- Use React.memo and useMemo for expensive computations
- Lazy load non-critical components
  
```

**Common Pitfalls to Avoid**

```text

- TypeScript configuration: Ensure 'strict' mode is enabled
- ESLint + Prettier conflicts: Use 'eslint-config-prettier' to disable conflicting rules
- Slow builds: Consider using Vite or esbuild for faster development
- Missing type definitions: Install '@types' packages for all dependencies
- Debugging issues: Ensure source maps are properly configured
  
```

**Recommended Tools**

```text

- Bundlers: Vite, Webpack, Parcel
- Testing: Jest, React Testing Library, Cypress
- Linting/Formatting: ESLint, Prettier, Stylelint
- Documentation: TypeDoc, Storybook
- Performance: Web Vitals, Lighthouse
  
```

************************************************

### TAKEAWAY - Tooling

* TypeScript Development Ecosystem:

  * Code Quality: ESLint with TypeScript support
  * Development: VS Code integration, debugging tools, HMR
  * Build & Deploy: Vite, Webpack, Parcel

* Vite is the recommended choice for fast dev server and modern builds.
* Use 'eslint-config-prettier' to avoid ESLint and Prettier conflicts.
* Enable 'strict' mode in tsconfig.json for best type safety.
* Recommended VS Code extensions: ESLint, Prettier, Error Lens, Path IntelliSense.

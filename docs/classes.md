
## TYPESCRIPT CLASSES

<details>
 <summary><b>Section Code - src/code/classBasic.ts</b></summary>

 [src/code/classBasic](src/code/classBasic.ts)

```ts
// classBasic
// Basics of class section.

class Person {name: string = ""};
var j = new Person();
j.name = "John";
export function outClassBasic():void {
 console.log(j.name);
}

```

</details>

<details>
 <summary><b>Section Code - src/progress/class.ts</b></summary>

 [src/progress/class](src/progress/class.ts)

```ts
// class
// Output class-related code to progress.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { log, codeBlock } from "../support/format";
import { outClassBasic } from "../code/classBasic";
import * as shClass from "../code/classShape";
import { outClassPerson } from "../code/classPerson";
import { outAbstractClass } from "../code/classAbstract";
import { takeAway } from "../support/takeAway";

var pageName = "class.ts";

export function runClass(): void {
 sectionHeader("Classes", "new"); 
 cl();
 cl("src/code/classBasic");
 cl();
 cl("src/progress/class");
 cl();
 // classBasic
 log("Class Members: Types", 3);
 cl();
 log(`The most basic use of classes:
\`\`\`ts
class Person {name: string = ""};
var j = new Person();
j.name = "John";
console.log(j.name);
/* Will return`);
 // John 
 outClassBasic();
 log(`*/
\`\`\``);
 
 // three types of visibility modifiers.
 log("Class Members: Visibility", 3);
 cl();
 log(`The three main visibility modifiers are:

1. public - (default) access globally.
2. private - accessed by member from within class.
3. protected - access by member from itself, and inheriting classes.
`);
 cl();
 log("Class Parameter Properties", 3);
 cl();
 log("The `constructor` can be used to define class members, adding visibility modifiers in parameter.");
 cl();
 codeBlock("ts", `
class Person {
  // name is a private member variable
  public constructor(private name: string) {}

  public getName(): string {
    return this.name;
  }
}

const person = new Person("Jane");
console.log(person.getName());
`);
 log("Readonly Class", 3);
 cl();
 log(`The \`readonly\` keyword prevents members from being changed.`);
 cl();
 // classShape
 log("Class Inheritance: Implements", 3);
 cl();
 log(`Interfaces defines the type a class will follow with the \`implements\` keyword.`);
 cl();
 log(`Example:
\`\`\`ts
interface Shape {
  getArea: () => number;
}
class Rectangle implements Shape {
  public constructor(protected readonly width: number, protected readonly height: number) {}

  public getArea(): number {
    return this.width * this.height;
  }
}
\`\`\`
`);
 cl();
 log(`Classes can implement multiple interfaces by listing as: class Rectangle implements Shape, Colored {...}`);
 cl();
 log("Class Inheritance: Extends", 3);
 cl();
 log("Classes can extend **one** other class using the `extends` keyword.");
 cl();
 log("Override Class", 3);
 cl();
 log(`Classes extending others can override members of the parent. In newer TypeScript versions this is explicitly allowed with the \`override\` keyword.`);
 cl();
 log("Example of making class using an extended class with overrides:");
 cl();
 cl("src/code/classShape");
 const myC = new shClass.Circle(3, 6);
 log(`
\`\`\`ts
console.log(shClass.mySq.toString());
// returns
// ${shClass.mySq.toString()}

console.log(shClass.mySq.getMath());
// returns
// ${shClass.mySq.getMath()}

console.log(myC.toString());
// returns
// ${myC.toString()}

console.log(myC.getMath());
// returns
// ${myC.getMath()}

\`\`\`
`);
 cl();

 // classPerson
 log("Person Class Example", 3);
 cl();
 log("Another example of an extending class:");
 cl("src/code/classPerson");
 log(`Using the function \`outClassPerson()\` will output:`);
 cl();
 log("**" + outClassPerson() + "**");
 cl();
 log(`The \`override\` keyword is optional for overriding methods. It helps prevent overriding a method that does not exist. Using \`noImplicitOverride\` forces it to be used when overriding.`);
 cl();
 log("Abstract Classes", 3);
 cl();
 log(`Classes can be used so that they are allowed to be a base class for another class without using all members. This is done with the \`abstract\` keyword. Unimplemented members in turn use the \`abstract\` keyword.`); 
 cl();
 cl("src/code/classAbstract");
 cl();
 log("Using the function `outAbstractClass()` will return:");
 cl();
 log(outAbstractClass());
 cl();

 // class takeaways
 var classTakeAway = new takeAway("Classes");
 classTakeAway.setTakeAway(`Basic Class Example:
'''ts
class Person {
  private readonly name: string;

  public constructor(name: string) {
    // name cannot be changed after this initial definition, which has to be either at its declaration or in the constructor.
    this.name = name;
  }

  public getName(): string {
    return this.name;
  }
}

const person = new Person("Jane");
console.log(person.getName());
// returns Jane
'''
`, `Three visibility modifiers:

1. public (default)
2. private
3. protected
`, `\`implements\` keyword:

'''ts
interface Shape {
  getArea: () => number;
}

class Rectangle implements Shape {
  public constructor(protected readonly width: number, protected readonly height: number) {}

  public getArea(): number {
    return this.width * this.height;
  }
}
'''
`, "`extends` keyword `class Square extends Rectangle {...}`", "`abstract` keyword `abstract class Polygon {...}`");
log(classTakeAway.outTakeAway());
}

```

</details>

### Class Members: Types

The most basic use of classes:

```ts
class Person {name: string = ""};
var j = new Person();
j.name = "John";
console.log(j.name);
/* Will return
John
*/
```

### Class Members: Visibility

The three main visibility modifiers are:

1. public - (default) access globally.
2. private - accessed by member from within class.
3. protected - access by member from itself, and inheriting classes.

### Class Parameter Properties

The `constructor` can be used to define class members, adding visibility modifiers in parameter.

```ts

class Person {
  // name is a private member variable
  public constructor(private name: string) {}

  public getName(): string {
    return this.name;
  }
}

const person = new Person("Jane");
console.log(person.getName());

```

### Readonly Class

The `readonly` keyword prevents members from being changed.

### Class Inheritance: Implements

Interfaces defines the type a class will follow with the `implements` keyword.

Example:

```ts
interface Shape {
  getArea: () => number;
}
class Rectangle implements Shape {
  public constructor(protected readonly width: number, protected readonly height: number) {}

  public getArea(): number {
    return this.width * this.height;
  }
}
```

Classes can implement multiple interfaces by listing as: class Rectangle implements Shape, Colored {...}

### Class Inheritance: Extends

Classes can extend **one** other class using the `extends` keyword.

### Override Class

Classes extending others can override members of the parent. In newer TypeScript versions this is explicitly allowed with the `override` keyword.

Example of making class using an extended class with overrides:

<details>
 <summary><b>Section Code - src/code/classShape.ts</b></summary>

 [src/code/classShape](src/code/classShape.ts)

```ts
// classShape
// Shape class exercise.


interface Shape {
 getMath: () => number;
}

class Rectangle implements Shape {
 public constructor(protected readonly width: number, protected readonly height: number) {}
 public getMath(): number {
  return this.width * this.height;
 }
 public toString(): string {
  return `Shape[width=${this.width}, height=${this.height}]`;
 }
}

class Square extends Rectangle {
  public constructor(width: number) {
    super(width, width);
  }

  // this toString replaces the toString from Rectangle
  public override toString(): string {
    return `Square[width=${this.width}]`;
  }
}
type radius = number
type diameter = number
export class Circle extends Rectangle { 
 public constructor(width: radius, height: diameter) {
  super(width, height);
 }
 circum:number = 2 * (Math.PI) * (this.width);
 
 public override getMath():number {
  return this.circum;
 }
}

export const mySq = new Square(20);


```

</details>

```ts
console.log(shClass.mySq.toString());
// returns
// Square[width=20]

console.log(shClass.mySq.getMath());
// returns
// 400

console.log(myC.toString());
// returns
// Shape[width=3, height=6]

console.log(myC.getMath());
// returns
// 18.84955592153876

```

### Person Class Example

Another example of an extending class:

<details>
 <summary><b>Section Code - src/code/classPerson.ts</b></summary>

 [src/code/classPerson](src/code/classPerson.ts)

```ts
// classPerson
// Section for extending classes.

class Person {
  public constructor(protected readonly name: string) {}
   public getName():string {
      return this.name;
       }
}

class perName extends Person {
 lname:string = "";
  public constructor(name: string) {
     super(name);
      }
}

let p = new perName("John");
p.lname = "Haugabook";
export function outClassPerson():string {
 return `Using extended class, where class builds on another. Name: ${p.getName()} ${p.lname}`;
}

```

</details>

Using the function `outClassPerson()` will output:

**Using extended class, where class builds on another. Name: John Haugabook**

The `override` keyword is optional for overriding methods. It helps prevent overriding a method that does not exist. Using `noImplicitOverride` forces it to be used when overriding.

### Abstract Classes

Classes can be used so that they are allowed to be a base class for another class without using all members. This is done with the `abstract` keyword. Unimplemented members in turn use the `abstract` keyword.

<details>
 <summary><b>Section Code - src/code/classAbstract.ts</b></summary>

 [src/code/classAbstract](src/code/classAbstract.ts)

```ts
// classAbstract
// Code for the example of abstract classes.

abstract class Polygon {
  public abstract getArea(): number;

  public toString(): string {
    return `Polygon[area=${this.getArea()}]`;
  }
}

class Rectangle extends Polygon {
  public constructor(protected readonly width: number, protected readonly height: number) {
    super();
  }

  public getArea(): number {
    return this.width * this.height;
  }
}

const myRect = new Rectangle(10,20);

export function outAbstractClass():any {
 return myRect.getArea();
}
```

</details>

Using the function `outAbstractClass()` will return:

200

************************************************

### TAKEAWAY - Classes

* Basic Class Example:

```ts
class Person {
  private readonly name: string;

  public constructor(name: string) {
    // name cannot be changed after this initial definition, which has to be either at its declaration or in the constructor.
    this.name = name;
  }

  public getName(): string {
    return this.name;
  }
}

const person = new Person("Jane");
console.log(person.getName());
// returns Jane
```

* Three visibility modifiers:

1. public (default)
2. private
3. protected

* `implements` keyword:

```ts
interface Shape {
  getArea: () => number;
}

class Rectangle implements Shape {
  public constructor(protected readonly width: number, protected readonly height: number) {}

  public getArea(): number {
    return this.width * this.height;
  }
}
```

* `extends` keyword `class Square extends Rectangle {...}`
* `abstract` keyword `abstract class Polygon {...}`

### GENERICS

<details>
 <summary><b>Section Code - src/progress/generics.ts</b></summary>

 [src/progress/generics](src/progress/generics.ts)

```ts
// generics
// Output code/generics.ts to progress.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { log } from "../support/format";
import { takeAway } from "../support/takeAway";

import * as gen from "../code/generics";

export function runGenerics(): void {
 log("### GENERICS");
 cl();
 cl("src/progress/generics");
 cl();
 log(`Use **Generics** to create 'type variables', which create classes, functions and type aliases without having to explicitly define the types being used. Generics make it easy to keep code **DRY** (*Don't Repeat Yourself*).`);
 cl();
 log("Generic Example:");
 cl();
 cl("src/code/generics");
 cl();
 log(`Running example as:
\`\`\`ts
console.log(gen.basicGeneric("Angle bracke with types", ", then set function to types in square bracker; return with square."));
// returns
// ${gen.basicGeneric("Angle bracke with types", ", then set function to types in square bracker; return with square.")}

console.log(gen.basicGenericTwo("one", "Now set the fucntion with generic angle brackets and function type as A | B."));
// returns
// ${gen.basicGenericTwo("one", "Now set the fucntion with generic angle brackets and function type as A | B.")}

console.log(gen.basicGenericTwo("two", "Now set the fucntion with generic angle brackets and function type as A | B."));
// returns
// ${gen.basicGenericTwo("two", "Now set the fucntion with generic angle brackets and function type as A | B.")}
\`\`\`
`);
 cl();
 log(`And running:
\`\`\`ts
console.log(gen.outGen.getValue());
// returns 
// ${gen.outGen.getValue()}

console.log(gen.outGen.toString());
// returns
//${gen.outGen.toString()}
\`\`\`
`);
 cl();
 log(`And running:
\`\`\`ts
console.log(gen.outDefault.getValue());
// returns
// ${gen.outDefault.getValue()}

console.log(gen.outDefault.toString());
// returns 
// ${gen.outDefault.toString()}
\`\`\`
`);
 cl();
 log(`And running:
\`\`\`ts
console.log(gen.createGenericPair("Generic Pair", "abc and xyz"));
// returns
// ${gen.createGenericPair("Generic Pair", "abc and xyz")}
 
console.log(gen.createGenericEither("one", "two"));
// returns
// ${gen.createGenericEither("one", "two")}
 
console.log(gen.createGenericEither(1, "two"));
// returns
// ${gen.createGenericEither(1, "two")}
\`\`\`
`);
 cl();

 // generic takeaway
 var genericTakeAway = new takeAway("Generic");
 genericTakeAway.setTakeAway(`Generic function:
'''ts
function createPair<S, T>(v1: S, v2: T): [S, T] {
  return [v1, v2];
}
console.log(createPair<string, number>('hello', 42)); // ['hello', 42]
'''
`, `Basic \`public\` Generic:
'''ts
class NamedValue<T> {
  _value: T | undefined;

  constructor(private name: string) {}

  public setValue(value: T) {
    this._value = value;
  }
 }
      
const value = new NamedValue<number>('myNumber');
value.setValue(10);
console.log(value._value); // myNumber: 10
'''
`, `Type alias:
'''ts
type Wrapped<T> = { value: T };

const wrappedValue: Wrapped<number> = { value: 10 };
'''
`, `\`extends\` keyword:
'''ts
function createLoggedPair<S extends string | number, 
T extends string | number>
(v1: S, v2: T): [S, T] {
  console.log(\`log pair: v1='\${v1}', v2='\${v2}'\`);
  return [v1, v2];
}
createLoggedPair("a", 1); // log pair: v1='a', v2='1'
'''
`
);
log(genericTakeAway.outTakeAway()); 
}

```

</details>

Use **Generics** to create 'type variables', which create classes, functions and type aliases without having to explicitly define the types being used. Generics make it easy to keep code **DRY** (*Don't Repeat Yourself*).

Generic Example:

<details>
 <summary><b>Section Code - src/code/generics.ts</b></summary>

 [src/code/generics](src/code/generics.ts)

```ts
// generics
// Basic generics section.

export function basicGeneric<A, B>(one: A, two: B): [A, B] {
 return [one, two];
}


export function basicGenericTwo<A, B>(one: A, two: B): A | B {
 if (one == "one") return one;
 else return two;
}

class genericClass<T> {
 private _value: T | undefined;
 constructor(private name: string) {}
 public setValue(value: T) {
  this._value = value;
 }
 public getValue(): T | undefined {
  return this._value;
 }
 public toString(): string | undefined {
  return `${this.name}: ${this._value}`;
 }
}

export let outGen = new genericClass<number>("Generic Number");
outGen.setValue(3);

class genDefault<T = string> {
 private _value: T | undefined;
 constructor(private name: string) {}
 public setValue(value: T) {
  this._value = value;
 }
 public getValue(): T | undefined {
  return this._value;
 }
 public toString():string {
  return `${this.name}: ${this._value}`;
 }
}

export var outDefault = new genDefault("Default Generic Class");
outDefault.setValue("This was set to string because the default type is string, and none was declared when defining variables.");

export function createGenericPair<S extends string | number, T extends string | number>(v1: S, v2: T): [S, T] {
 return [v1, v2];
}

export function createGenericEither<S extends string | number,
T extends string | number>(v1: S, v2: T): S | T {
 if (v1 == "one") return v1;
 else return v2;
}
```

</details>

Running example as:

```ts
console.log(gen.basicGeneric("Angle bracke with types", ", then set function to types in square bracker; return with square."));
// returns
// Angle bracke with types,, then set function to types in square bracker; return with square.

console.log(gen.basicGenericTwo("one", "Now set the fucntion with generic angle brackets and function type as A | B."));
// returns
// one

console.log(gen.basicGenericTwo("two", "Now set the fucntion with generic angle brackets and function type as A | B."));
// returns
// Now set the fucntion with generic angle brackets and function type as A | B.
```

And running:

```ts
console.log(gen.outGen.getValue());
// returns 
// 3

console.log(gen.outGen.toString());
// returns
//Generic Number: 3
```

And running:

```ts
console.log(gen.outDefault.getValue());
// returns
// This was set to string because the default type is string, and none was declared when defining variables.

console.log(gen.outDefault.toString());
// returns 
// Default Generic Class: This was set to string because the default type is string, and none was declared when defining variables.
```

And running:

```ts
console.log(gen.createGenericPair("Generic Pair", "abc and xyz"));
// returns
// Generic Pair,abc and xyz
 
console.log(gen.createGenericEither("one", "two"));
// returns
// one
 
console.log(gen.createGenericEither(1, "two"));
// returns
// two
```

************************************************

### TAKEAWAY - Generic

* Generic function:

```ts
function createPair<S, T>(v1: S, v2: T): [S, T] {
  return [v1, v2];
}
console.log(createPair<string, number>('hello', 42)); // ['hello', 42]
```

* Basic `public` Generic:

```ts
class NamedValue<T> {
  _value: T | undefined;

  constructor(private name: string) {}

  public setValue(value: T) {
    this._value = value;
  }
 }
      
const value = new NamedValue<number>('myNumber');
value.setValue(10);
console.log(value._value); // myNumber: 10
```

* Type alias:

```ts
type Wrapped<T> = { value: T };

const wrappedValue: Wrapped<number> = { value: 10 };
```

* `extends` keyword:

```ts
function createLoggedPair<S extends string | number, 
T extends string | number>
(v1: S, v2: T): [S, T] {
  console.log(`log pair: v1='${v1}', v2='${v2}'`);
  return [v1, v2];
}
createLoggedPair("a", 1); // log pair: v1='a', v2='1'
```

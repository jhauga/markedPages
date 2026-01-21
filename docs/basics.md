## TYPESCRIPT BASICS - ARRAYS AND TUPLES

## Getting Started

### Intalling TypeScript Compiler

```bash
npm install typescript --save-dev

# INSTALL GLOBALLY
npm install -g typescript

```

### Configure TypeScript Compiler

#### Create with Recommended Settings

```bash
npx tsc --init  

```

#### Customize Compile Settings

```json
{
  "include": ["src"],
  "compilerOptions": {
    "outDir": "./build"
  }
}  

```

### Getting Started Project

```ts
// hello.ts
function greet(name: string): string {
  return `Hello, = ${name}!`;
}

const message: string = greet("World");
console.log(message);  

```
Then compile code with:

```bash
npx tsc hello.ts
```

### Simple Types

The types are defined as **primitive**. All JavaScript primitive types can be used, but TypeScript also has primitives unique to it.

#### Boolean

```ts
let name: boolean = true;
let user = false; // TypeScript infers `boolean`  

```

#### Number

```ts
let decimal: number = 6;
let hex: number = 0xf00d;      // Hexadecimal
let binary: number = 0b1010;   // Binary
let octal: number = 0o744;     // Octal
let float: number = 3.14;      // Floating point

```

#### String

```ts
let color: string = "blue";
let fullName: string = 'John Doe';
let age: number = 30;
let sentence: string = `Hello, my name is ${fullName} and I'll be ${age + 1} next year.`;

```

#### BigInt (ES2020+)

```ts
const bigNumber: bigint = 9007199254740991n;
const hugeNumber = BigInt(9007199254740991); // Alternative syntax

```

#### Symbol

```ts
const uniqueKey: symbol = Symbol("some text");
const obj = {
 [uniqueKey]: 'Text for a unique property'
};
console.log(obj[uniqueKey]); // "Text for a unique property"

```
* Array declared as type `var name: type[] = [];` .
* When this one had typed declared it was explicity given type readonly string[] -  `const readOnlyArr: readonly string[] = [ // this, sentence ];`
* Define optional parameters as `(name?: type)`. In function use a default value like:
 `return name || "left blank";`
* String but this one was not typed declared. Tuples are similary but they are typed arrays essentially when 1st declared
* Another tuple is readonly and it is readonly . Declared like `const tupTwo: readonly[string, string[], number[], string] = [ // this, sentence ]`
* Output of number array use when forEach has expression for types:

```ts
  const arrNum: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
  const powNum = ():void => {
   console.log(Math.pow(num, 2));
  };
  // returns
  // 2025;
```

* Using:

```ts
  const coord: [x: number, y: number] = [28.43221, 30.34];
  const [x, y] = coord; 
  console.log(String(x + ", " + y));
```

* Deconstructes tuple with coordinates 28.43221, 30.34

> [!NOTE]
> 11. This was output from an imported function. The parameter is type sring | number. The function

************************************************

### TAKEAWAY - Basics

* String Array - var name: string[]
* Number Array - var name: number[]
* Constant readonly array - var name: readonly string[] | number[]
* Similar JavaScript statements: for, forEach, if-else-else if, while, function, etc.
* Optional parameter/property = prop?:val
* Tuples are typed arrays.

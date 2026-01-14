## TYPESCRIPT BASICS - ARRAYS AND TUPLES

## Getting Started

<details>
 <summary><b>Section Code - src/code/basics.ts</b></summary>

 [src/code/basics](src/code/basics.ts)

```ts
// basic
// Essentials of TypeScript.

import { num } from "../progress";
import { takeAway } from "../support/takeAway";

// Global variables.
export var note:string;
export const arrOne: string[] = ["Array", "declared", "as", "type", "`var name: type[] = [];`"];
export const arrFillOne = ["string", "but", "this", "one", "was", "not", "typed declared."];
export const arrNum: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
export const readOnlyArr: readonly string[] = ["When", "this one had typed declared", "it was explicity given type readonly", "string[] - ", "`const readOnlyArr: readonly string[] = [ // this, sentence ];`"];
// this is reset
export var text: string = "";

// loop with temp variable
export function loopReadOnlyArr(arr: string[]): string {
 let txt = "";
 arr.forEach(out => {
  txt += out + " ";
 });
 return txt;
}

// arrow function
export const outFillOne = (item?: string):string => {
 return item || `Define optional parameters as \`(name?: type)\`. In function use a default value like:
 \`return name || "left blank";\``;
};

// added to global text
export const tupOne: [string, string[], number, string] = ["Tuples are similary", ["but", "they", "are", "typed", "arrays", "essentially", "when"], 1, "st declared"];

// added to global text
export const tupTwo: readonly[string, string[], number[], string] = ["Another tuple is readonly", ["and it", "is", "readonly"], arrNum, ". Declared like `const tupTwo: readonly[string, string[], number[], string] = [ // this, sentence ]`"];

export const powNum = ():string => {
 return `${Math.pow(num, 2)}`;
};

// used in progress
export const coord: [x: number, y: number] = [28.43221, 30.34];

export var basicTakeAway = new takeAway("Basics");
basicTakeAway.setTakeAway("String Array - var name: string[]", "Number Array - var name: number[]", "Constant readonly array - var name: readonly string[] | number[]", "Similar JavaScript statements: for, forEach, if-else-else if, while, function, etc.", "Optional parameter/property = prop?:val", "Tuples are typed arrays.");
```

</details>

<details>
 <summary><b>Section Code - src/progress/basics.ts</b></summary>

 [src/progress/basics](src/progress/basics.ts)

```ts
// basics
// Output code/basics.ts to progress.

import * as format from "../support/format";
import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import * as sideNotes from "../support/sideNotes";
import * as basic from "../code/basics";
import * as playground from "../code/playground";
import { num } from "../progress";

var pageName = "basics.ts";

export function runBasics(): void {
 // Start outputs.
 sectionHeader("Basics - Arrays and Tuples","first");
 format.log("Getting Started", 2);
 cl();
 cl("src/code/basics");
 cl();
 cl("src/progress/basics");
 cl();
 format.log("Intalling TypeScript Compiler", 3);
 cl();
 format.codeBlock("bash", `
npm install typescript --save-dev

# INSTALL GLOBALLY
npm install -g typescript
`);
 cl();
 format.log("Configure TypeScript Compiler", 3);
 cl();
 format.log("Create with Recommended Settings", 4);
 cl();
 format.codeBlock("bash", `
npx tsc --init  
`);
 cl();
 format.log("Customize Compile Settings", 4);
 cl();
 format.codeBlock("json", `
{
  "include": ["src"],
  "compilerOptions": {
    "outDir": "./build"
  }
}  
`);
 cl();
 format.log("Getting Started Project", 3);
 cl();
 format.codeBlock("ts", `
// hello.ts
function greet(name: string): string {
  return \`Hello, = \${name}!\`;
}

const message: string = greet("World");
console.log(message);  
`);
 cl();
 format.log("Then compile code with:");
 cl();
 format.codeBlock("bash", `npx tsc hello.ts`);
 cl();
 format.log("Simple Types", 3);
 cl();
 format.log("The types are defined as **primitive**. All JavaScript primitive types can be used, but TypeScript also has primitives unique to it.");
 cl();
 format.log("Boolean", 4);
 cl();
 format.codeBlock("ts", `
let name: boolean = true;
let user = false; // TypeScript infers \`boolean\`  
`);
 cl();
 format.log("Number", 4);
 cl();
 format.codeBlock("ts", `
let decimal: number = 6;
let hex: number = 0xf00d;      // Hexadecimal
let binary: number = 0b1010;   // Binary
let octal: number = 0o744;     // Octal
let float: number = 3.14;      // Floating point
`);
 cl();
 format.log("String", 4);
 cl();
 format.codeBlock("ts", `
let color: string = "blue";
let fullName: string = 'John Doe';
let age: number = 30;
let sentence: string = \`Hello, my name is \${fullName} and I'll be \${age + 1} next year.\`;
`);
 cl();
 format.log("BigInt (ES2020+)", 4);
 cl();
 format.codeBlock("ts", `
const bigNumber: bigint = 9007199254740991n;
const hugeNumber = BigInt(9007199254740991); // Alternative syntax
`);
 cl();
 format.log("Symbol", 4);
 cl();
 format.codeBlock("ts", `
const uniqueKey: symbol = Symbol("some text");
const obj = {
 [uniqueKey]: 'Text for a unique property'
};
console.log(obj[uniqueKey]); // "Text for a unique property"
`);
 
 basic.arrOne.forEach(item => {
  (basic.text as any) += item + " ";
 });
 console.log("* " + basic.text + ".");
 console.log("* " + basic.loopReadOnlyArr(basic.readOnlyArr as any));
 (basic.text as any) = "";


 (basic.text as any) += basic.outFillOne();
 console.log("* " + (basic.text as any));

 (basic.text as any) = "";
 // add to global text
 basic.arrFillOne.forEach(itm => { 
  (basic.text as any) += basic.outFillOne(itm) + " ";
 });

 basic.tupOne.forEach(item => {
  (basic.text as any) += `${format.nestIterate(item)}`;
 });
 //(basic.text as any) = format.makeSentence((basic.text as any));
 console.log("* " + format.makeSentence((basic.text as any)));

 (basic.text as any) = "";

 (basic.tupTwo as any).forEach((item: any) => {
  if (typeof item == "string") {
   (basic.text as any) += `${item} `;
  } else {
   item.forEach((itm: any) => {
    if (typeof itm == "string") {
     (basic.text as any) += itm + " ";
    } else {
     (num as any) += itm;
    }
   });
  }
 });
 console.log("* " + basic.text);
 var basicPOW: string = basic.powNum();
 console.log(`* Output of number array use when forEach has expression for types:

\`\`\`ts
  const arrNum: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
  const powNum = ():void => {
   console.log(Math.pow(num, 2));
  };
  // returns
  // ${basicPOW};
\`\`\`
`);

 console.log(`* Using: 

\`\`\`ts
  const coord: [x: number, y: number] = [28.43221, 30.34];
  const [x, y] = coord; 
  console.log(String(x + ", " + y));
\`\`\`
`);

 const [x, y] = basic.coord;
 console.log("* Deconstructes tuple with coordinates " + String(x + ", " + y));

 (basic.note as any) = sideNotes.sideNote(playground.stringNum("digit") + ". This was output from an imported function. The parameter is type sring | number. The function");
 console.log(basic.note); 
 console.log(basic.basicTakeAway.outTakeAway());
}
```

</details>

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

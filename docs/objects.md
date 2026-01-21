## TYPESCRIPT OBJECTS

<details>
 <summary><b>Section Code - src/code/objects.ts</b></summary>

```ts
// objects
// Object types, enums, aliases and interfaces, and union types section of progress.

import { takeAway } from "../support/takeAway";
import { log } from "../support/format";

export var typeCar: {type: string, model: string, color: string, year: number};
export function typeObject(type:string, model:string, color:string, year:number):void {
 typeCar = {
  type: type,
  model: model,
  color: color,
  year: year
 };
}
export var typeOpt: {location: string, mileage: number, owner?: string};
export function typeOptional(location: string, mileage: number, owner?: string):void {
 typeOpt = {
  location: location,
  mileage: mileage,
  owner: owner || "Not sold"
 };
}

function outIndexSignature(val: any):any {
 return val;
}

export var typeIndex: { [index: string]: any } = {};
export function typeIndexSignature(prop: any, val: any):void {
 typeIndex[prop] = val;
 log("```ts");
 log("var typeIndex: { [index: string]: any } = {};");
 log(`typeIndex[${prop}] = "${val}";`);
 log("return typeIndex;");
 log("/* RETURNS")
 log(outIndexSignature(typeIndex));
 log("*/");
 log("```");
}

export var objTakeAway = new takeAway("Objects");
objTakeAway.setTakeAway("`var typedObj: {typeA: string, typeB: number, etc..}`", "Can use function to define values.", "Optional => `property?: type`", "`property: propName || default value`","use `function name():void` if no return.", "MAIN - Index signatures can use `prop:value` without defined list.", `
'''ts
 const nameAgeMap: { [index: string]: number } = {};
 nameAgeMap.Jack = 25;
 nameAgeMap.Mark = 50;
'''
`);

```

</details>

<details>
 <summary><b>Section Code - src/progress/objects.ts</b></summary>

```ts
// objects
// Output code/objects.ts to progress.

import { sectionHeader, blankLine as cl } from "../support/sectionHeader";
import { typeObject as typObj, typeOptional as typOpt, typeIndexSignature as typeSig, typeCar, typeOpt, typeIndex, objTakeAway } from "../code/objects";
import { log } from "../support/format";

var pageName = "objects.ts";

function outObject(cur: any): string {
 let out = "```ts";
 for (const prop in cur) {
  out += `
   ${prop}: ${cur[prop as keyof typeof cur]}`;
 }
 out += `
\`\`\`
`;
 return out;
}

export function runObjects(): void {
 sectionHeader("Objects", "new", "src/code/objects");
 cl();
 cl("src/progress/objects");
 typObj("Ford", "Ranger", "Black", 2023);
 
 // call local function
 console.log(outObject(typeCar));
 
 // update object and call local function
 typOpt("Ga", 125000);
 console.log("After updating the object using `typOpt(\"Ga\", 125000);`.");
 cl();
 console.log(outObject(typeOpt));
 cl();
 log("**Index Signatures** are usefule when set is not defined. Example:");
 typeSig("indexSignatures", "good for a list of objects without a defined set of propery values.");
 console.log(objTakeAway.outTakeAway());
}

```

</details>

```ts
   type: Ford
   model: Ranger
   color: Black
   year: 2023
```

After updating the object using `typOpt("Ga", 125000);`.

```ts
   location: Ga
   mileage: 125000
   owner: Not sold
```

**Index Signatures** are usefule when set is not defined. Example:

```ts
var typeIndex: { [index: string]: any } = {};
typeIndex[indexSignatures] = "good for a list of objects without a defined set of propery values.";
return typeIndex;
/* RETURNS
[object Object]
*/
```

************************************************

### TAKEAWAY - Objects

* `var typedObj: {typeA: string, typeB: number, etc..}`
* Can use function to define values.
* Optional => `property?: type`
* `property: propName || default value`
* use `function name():void` if no return.
* MAIN - Index signatures can use `prop:value` without defined list.

```ts
 const nameAgeMap: { [index: string]: number } = {};
 nameAgeMap.Jack = 25;
 nameAgeMap.Mark = 50;
```

<details>
 <summary><b>Section Code - src/code/casting.ts</b></summary>

```ts
// casting
// Casting section

import { takeAway } from "../support/takeAway";

var castX = ():unknown => {return `Arrow function when **casting type** is unknown. Can cast number method outputs to string. Example:

\`\`\`ts
var castX = ():unknown => {return '// This section;'};

function outX():void {
 console.log((<string>castX()));
 console.log((<string>castX()).length);
 console.log(typeof (<string>castX()).length);
}
\`\`\` 
`;};
export var basicXCast: unknown = 'hello';

export function outX():void {
 console.log((<string>castX()));
 console.log((<string>castX()).length);
 console.log(typeof (<string>castX()).length);
}

export var castingTakeAway = new takeAway("Casting");

castingTakeAway.setTakeAway("Use (name as any).method() to HOT-GLUE", "Syntax A - `(x as string)`", "Syntax B - `<string>x`");
```

</details>

<details>
 <summary><b>Section Code - src/progress/casting.ts</b></summary>

```ts
// casting
// Output code/casting.ts to progress.

import { sectionHeader } from "../support/sectionHeader";
import { outX, basicXCast, castingTakeAway } from "../code/casting";

export function runCasting(): void {
 // casting
 console.log("CASTING:");
 console.log((basicXCast as string).length);
 outX();
 console.log(castingTakeAway.outTakeAway());
}

```

</details>

## Casting, enums, interface, union, and functions

CASTING:
5
Arrow function when **casting type** is unknown. Can cast number method outputs to string. Example:

```ts
var castX = ():unknown => {return '// This section;'};

function outX():void {
 console.log((<string>castX()));
 console.log((<string>castX()).length);
 console.log(typeof (<string>castX()).length);
}
```

313
number

************************************************

### TAKEAWAY - Casting

* Use (name as any).method() to HOT-GLUE
* Syntax A - `(x as string)`
* Syntax B - `<string>x`

### ENUMS

<details>
 <summary><b>Section Code - src/code/enums.ts</b></summary>

```ts
// enums
// Enums are class that represent constant variables.

import { takeAway } from "../support/takeAway";

enum CardinalNumDirections {
  North,
  East,
  South,
  West
};
            
export var currentDirection = CardinalNumDirections.North;

export enum CardinalDirections {
  North = 'North',
  East = "East",
  South = "South",
  West = "West"
};

export var enumTakeAway = new takeAway("Enums");
enumTakeAway.setTakeAway("enums increment", `use: 

'''
enum enumName {
 one,   // 0
 two,   // 1
 three, // 2
 etc..
}
'''`
, "Can be string => `one = \"one\";` // all have to be defined", "Good for constants like directions: north, south, east, and west");
```

</details>

<details>
 <summary><b>Section Code - src/progress/enums.ts</b></summary>

```ts
// enums
// Output code/enums.ts to progress.

import { blankLine as cl } from "../support/sectionHeader";
import * as en from "../code/enums";
import { log } from "../support/format";

export function runEnums(): void {
 // enums
 log("### ENUMS:")
 cl("src/code/enums");
 cl();
 cl("src/progress/enums");
 // North is the first value so it logs '0'
 log(`The output of:
\`\`\`ts
enum CardinalNumDirections {
  North,
  East,
  South,
  West
};
            
var currentDirection = CardinalNumDirections.North;
console.log(CardinalNumDirections.North);
\`\`\`
Would be **${en.currentDirection}**.`);

 // logs "North"
 cl();
 log(`Using \`console.log(en.CardinalDirections.North);\` would return **${en.CardinalDirections.North}**.`);
 
 // logs "West"
 cl();
 log(`Using \`console.log(en.CardinalDirections.West);\` would return **${en.CardinalDirections.West}**.`);
 log(en.enumTakeAway.outTakeAway());
}

```

</details>

The output of:

```ts
enum CardinalNumDirections {
  North,
  East,
  South,
  West
};
            
var currentDirection = CardinalNumDirections.North;
console.log(CardinalNumDirections.North);
```

Would be **0**.

Using `console.log(en.CardinalDirections.North);` would return **North**.

Using `console.log(en.CardinalDirections.West);` would return **West**.

************************************************

### TAKEAWAY - Enums

* enums increment
* use:

```
enum enumName {
 one,   // 0
 two,   // 1
 three, // 2
 etc..
}
```

* Can be string => `one = "one";` // all have to be defined
* Good for constants like directions: north, south, east, and west

### INTERFACE

<details>
 <summary><b>Section Code - src/code/interface.ts</b></summary>

```ts
// interface
// Using type alias, and interface and extendended interface.

import { blankLine as cl } from "../support/sectionHeader";
import { takeAway } from "../support/takeAway";
import { sideNote } from "../support/sideNotes";
import { log } from "../support/format";

export type aliasNamed = string

// Try creating a new interface and extending it like below
interface Rectangle {
  height: number,
  width: number
}

interface ColoredRectangle extends Rectangle {
  color: string
}

const coloredRectangle: ColoredRectangle = {
  height: 20,
  width: 10,
  color: "red"
};
const rectOut: Rectangle = {
 height: 10,
 width: 30
};
export function interfaceOut():void {
 cl();
 log("Interface");
 cl();
 log(`\`\`\`ts
interface Rectangle {
  height: number,
  width: number
}
interface ColoredRectangle extends Rectangle {
  color: string
}
\`\`\`

Extended Interface using Rectangle, adding color property. Now using:

\`\`\`ts
const rectOut: Rectangle = {
 height: 10,
 width: 30
};
console.log(\`$\{rectOut\}\`); 
// returns ${rectOut}
`);

 log(`console.log(coloredRectangle);
\`\`\`

will return `);
 log(coloredRectangle);
 cl();
 log(sideNote(`But if wrapped in backtick or adajent to quote character like:
\`\`\`ts
console.log(\`\${coloredRectangle}\`);
console.log("**" + coloredRectangle + "**");
\`\`\`
`));
 cl();
 log("Will return:");
 cl();
 log(`${coloredRectangle}`);
 cl();
 log("**" + coloredRectangle + "**");
}

// Section takeaway.
export var interfaceTakeAway = new takeAway("Interface");
interfaceTakeAway.setTakeAway("Interfaces can be extended.", `use:
'''ts
interface extName extends Name {
  property: type
}
'''`, "Interfaces do not end with `;` character.", "To output raw data use only variable name out print statement, and do not include any wrapping characters i.e. `, ', or \"; or any adjacent data wrapped in characters.");

```

</details>

<details>
 <summary><b>Section Code - src/progress/interface.ts</b></summary>

```ts
// interface
// Output code/interface.ts to progress.

import { blankLine as cl } from "../support/sectionHeader";
import { aliasNamed as alName, interfaceOut, interfaceTakeAway } from "../code/interface";
import { log } from "../support/format";

export function runInterface(): void {
 // interface
 console.log("### INTERFACE:")
 cl("src/code/interface");
 cl();
 cl("src/progress/interface");
 let outAlias: alName = "This uses `type aliasNamed = string` without `;` at end of line.";
 console.log(outAlias);
 interfaceOut();
 log(interfaceTakeAway.outTakeAway());
}

```

</details>

This uses `type aliasNamed = string` without `;` at end of line.

Interface

```ts
interface Rectangle {
  height: number,
  width: number
}
interface ColoredRectangle extends Rectangle {
  color: string
}
```

Extended Interface using Rectangle, adding color property. Now using:

```ts
const rectOut: Rectangle = {
 height: 10,
 width: 30
};
console.log(`${rectOut}`); 
// returns [object Object]

console.log(coloredRectangle);
```

will return
[object Object]

> [!NOTE]
> But if wrapped in backtick or adajent to quote character like:

```ts
console.log(`${coloredRectangle}`);
console.log("**" + coloredRectangle + "**");
```

Will return:

[object Object]

**[object Object]**

************************************************

### TAKEAWAY - Interface

* Interfaces can be extended.
* use:

```ts
interface extName extends Name {
  property: type
}
```

* Interfaces do not end with `;` character.
* To output raw data use only variable name out print statement, and do not include any wrapping characters i.e. `, ', or "; or any adjacent data wrapped in characters.

### UNION

<details>
 <summary><b>Section Code - src/code/union.ts</b></summary>

```ts
// union
// Parameter that can be of two types.

import { log } from "../support/format";
import { takeAway } from "../support/takeAway";

export function printStatusCode(code: string | number) {
  log(`Status code is ${code}.`)
  log(`Status code type is: ${typeof code}`);
}

export var unionTakeAway = new takeAway("Union");
unionTakeAway.setTakeAway("For variable unions `let name: string | number;`", 
 "For function types ` let localUnion = (val: any):number | string => {...}; `",
 "For parameters `fnName(param: string | number)`"
);
```

</details>

<details>
 <summary><b>Section Code - src/progress/union.ts</b></summary>

```ts
// union
// Output code/union.ts to progress.

import { blankLine as cl } from "../support/sectionHeader";
import { log } from "../support/format";
import { printStatusCode, unionTakeAway } from "../code/union"; 

export function runUnion(): void {
 // union
 console.log("### UNION:")
 cl("src/code/union");
 cl();
 cl("src/progress/union");
 log("Union refers to when a value can be over one type.");
 cl();
 // local union
 let union: number | string;
 let localUnion = (val: any):number | string => {
  if (typeof val == "string") return val.toUpperCase();
  else if (typeof val == "number") return Math.random() * (val * 100);
  else return "error";
 };
 log(`Using union for a variable \`let name: typeA | typeB;\`. Example:
\`\`\`ts
 let union: number | string;
 let localUnion = (val: any):number | string) => {
  if (typeof val == "string") return val.toUpperCase;
  else if (typeof val == "number") return Math.random() * (val * 100);
  else return "error";
 };
 console.log(localUnion("2"));
 console.log(localUnion(2));
 /* will return`);
 log(localUnion("2"));
 cl();
 log(localUnion(2));
 log(`*/
\`\`\`
`);
 log("And the output of another function like `export function printStatusCode(code: string | number) { return code; }`");
 cl();
 log("Could be `printStatusCode(404);`");
 cl();
 printStatusCode(404);
 cl();
 log("Or `printStatusCode('404');`");
 cl();
 printStatusCode('404');
 cl();
 log(unionTakeAway.outTakeAway());
}

```

</details>

Union refers to when a value can be over one type.

Using union for a variable `let name: typeA | typeB;`. Example:

```ts
 let union: number | string;
 let localUnion = (val: any):number | string) => {
  if (typeof val == "string") return val.toUpperCase;
  else if (typeof val == "number") return Math.random() * (val * 100);
  else return "error";
 };
 console.log(localUnion("2"));
 console.log(localUnion(2));
 /* will return
2

193.75375103767135
*/
```

And the output of another function like `export function printStatusCode(code: string | number) { return code; }`

Could be `printStatusCode(404);`

Status code is 404.
Status code type is: number

Or `printStatusCode('404');`

Status code is 404.
Status code type is: string

************************************************

### TAKEAWAY - Union

* For variable unions `let name: string | number;`
* For function types ` let localUnion = (val: any):number | string => {...}; `
* For parameters `fnName(param: string | number)`

### FUNCTIONS

<details>
 <summary><b>Section Code - src/code/function.ts</b></summary>

```ts
// function
// Function section with all w3 examples.

// the `: number` here specifies that this function returns a number
export function getTime(): number {
  return new Date().getTime();
}

export function printHello(): void {
  console.log('Hello!');
}

export function pow(value: number, exponent: number = 10) {
  return value ** exponent;
}

export function divide({ dividend, divisor }: { dividend: number, divisor: number }) {
  return dividend / divisor;
}

export function add(a: number, b: number, ...rest: number[]) {
  return a + b + rest.reduce((p, c) => p + c, 0);
}

type Negate = (value: number) => number;

// in this function, the parameter `value` automatically gets assigned the type `number` from the type `Negate`
export const negateFunction: Negate = (value) => value * -1;
```

</details>

<details>
 <summary><b>Section Code - src/progress/function.ts</b></summary>

```ts
// function
// Output code/function.ts to progress.

import { blankLine as cl } from "../support/sectionHeader";
import * as fn from "../code/function";

export function runFunction(): void {
 // function
 console.log("### FUNCTIONS:")
 cl("src/code/function");
 cl();
 cl("src/progress/function");
 console.log(fn.getTime());
 fn.printHello();
 console.log(fn.pow(10));
 console.log(fn.divide({dividend: 10, divisor: 2}));
 console.log(fn.add(10,10,10,10,10));
 console.log(fn.negateFunction(10));
}

```

</details>

1766193773123
Hello!
10000000000
5
50
-10

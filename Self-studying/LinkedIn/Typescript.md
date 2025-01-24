![[Pasted image 20250123233037.png]]
![[Pasted image 20250123233111.png]]
[Typescript doc](https://www.typescriptlang.org/docs/handbook/intro.html)
[Nodejs](https://www.node.org/en)
[npmjs](https://www.npmjs.com)

# Configuring and run tsc
`tsconfig.json` = file that contains all typescript configuratiojn options
```json
{
	"include": ["src/**/*"], // Indicates the folder and files that tsc will watch
	"compilerOptions": { 
		"target": "esnext", // The compilation options (esnext compiles with whatever the latest version compatible)
		"outDir": "build", // Folder where tsc will transpile to js
		"noEmit": true, // Tells tsc not to write out anything to disk at all and just checking types
		"allowJs": true, // Enables searching of existing js files
		"checkJs": true, // Enables checking of existing js files
	}
}
```

> For checking third-part types, go to npm packages and search for `@type <library>` and install the typescript definitions in terminal

> Run `tsc` to run typescript

# Primitives and built-in-types
Tsc has a inference power when defining a variable. But in case you only declare a variable:

```typescript
let x: number;
let y: string;
let z: boolean;
let a: Date
let b: any;
let c: string[];
```

# Custom types with interfaces
The biggest differenece between an interface and a class is that interfaces strictly exist as a way for you to provide type information to Tsc

```typescript
// Merges the address interface into contact interface
interface Contact extends Address { 
	id: number;
	name: string;
	birthDate?: Date; // Optional field
}

interface Address {
	region: string;
	disctrict: string;
}

let primaryContact: Contact = {
	id: 12345,
	name: "Jeff",
	birthDate: new Date('16/03/2005'),
	region: "Lima",
	district: "SMP"
}

```

# Type aliases
Other way to defining custom types. It's just an alias to another type

```typescript
interface Contact { 
	id: number;
	name: ContactName; // Alias to a new type
	birthDate?: Date; 
}

let primaryContact: Contact = {
	id: 12345,
	name: "Jeff",
	birthDate: new Date('16/03/2005'),
}

type ContactName = string // Type aliases
```

# Enumerable types

```typescript
interface Contact { 
	id: number;
	name: ContactName;
	birthDate?: Date; 
	status: ContactStatus; // Just can be one of the options of the enum
}

// Enum with tree options
enum ContactStatus {
	Active = "active", 
	Inactive = "inactive", 
	New = "new"
}

let primaryContact: Contact = {
	id: 12345,
	name: "Jeff",
	birthDate: new Date('16/03/2005'),
	status: ContactStatus.Active // Define the attribute with one option
}

type ContactName = string
```

# Typing functions

```typescript
interface Contact { 
	id: number;
	name: string;
}

// parameters and functions can have their own type
function clone(source: Contact, fun: ): Contact {
	return Object.apply({}, source)
}

const a: Contact = { id: 123, name: "Jeff"};
const b = clone(a)
```
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
+ Other way to defining custom types. It's just an alias to another type
+ They provide an alternative name for an existing type

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
+ They are compiled and available at runtime

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
	clone(name: string): Contact; // function as attribute
}

// parameters and return values can have their own type
function clone(source: Contact): Contact {
	return Object.apply({}, source)
}

const a: Contact = { id: 123, name: "Jeff"};
const b = clone(a)
```

# Metatype using Generics
+ Generic type = Meta type
+ A type that represents any other type you might sustitute in
+ A placeholder type

## Generic variables

```typescript
interface Contact { 
	id: number;
	name: string;
}

// The variable T will be replaced by any other type
function clone<T>(source: T): T {
	return Object.apply({}, source)
}

const a: Contact = { id: 123, name: "Jeff"};
const b = clone(a)

const dateRange = { startDate: Date.now(), endDate: Date.now()}
// Tsc dynamically replace T with the structure of this variable 
const dateRangeCopy = clone(dateRange)
```

## Multiple generic variables

```typescript
interface Contact { 
	id: number;
	name: string;
}

// Two generic types dynamically
function clone<T1, T2>(source: T1): T2 {
	return Object.apply({}, source)
}

// It's necessary to indicate Tsc the variable types
const a: Contact = { id: 123, name: "Jeff"};
const b = clone<Contact, Date>(a) // T1: Contact, T2: Date
```

## Generic constraints
+ Restrictic rules to some variables

```typescript
interface Contact { 
	id: number;
	name: string;
}

interface UserContact { 
	id: number;
	name: string;
	username: string;
}

// Restriction: T2 type has to extend T1 type 
function clone<T1, T2 extends T1>(source: T1): T2 {
	return Object.apply({}, source)
}

const a: Contact = { id: 123, name: "Jeff"};
// Here UserContact interface extends Contact interface
const b = clone<Contact, UserContact>(a) 
```

## Generics applied to everywhere
### Interfaces
```typescript
// Generic type to a interface
interface UserContact<TExternalId> { 
	id: number;
	name: string;
	username: string;
	externalId: TExternalId; // Generic type
	loadExternalId(): Task<TExternalId> 
}
```

# Union types

```typescript
type ContactName = string;

// enum ContactStatus {
//    Active = "active",
//    Inactive = "inactive",
//    New = "new"
//}

// Instead of using enum
type ContactStatus = "active" | "inactive" | "new";

type ContactBirthDate = Date | number | string; // Accept one of those types

interface Contact {
    id: number;
    name: ContactName; // Type aliases
    birthDate?: ContactBirthDate;
    status?: ContactStatus;
}

interface Address {
    line1: string;
    line2: string;
    province: string;
    region: string;
    postalCode: string;
}

type AddressableContact = Contact & Address; // Creates a new type with the union

function getBirthDate(contact: Contact) {
    if (typeof contact.birthDate === "number") { // typeof number
        return new Date(contact.birthDate);
    }
    else if (typeof contact.birthDate === "string") { // typeof string 
        return Date.parse(contact.birthDate)
    }
    else {
        return contact.birthDate
    }
}

let primaryContact: Contact = {
    id: 12345,
    name: "Jamie Johnson",
    status: "active" // Write the values directly, without enum syntax
}
```

# Keyof operator
+ Looks like using the native instanceof operator
+ Only available in compile time
+  Defines a type alias consisting of all of the properties on the contact type

```typescript
type ContactName = string;
type ContactStatus = "active" | "inactive" | "new"
type ContactBirthDate = Date | number | string

interface Contact  {
    id: number;
    name: ContactName;
    birthDate?: ContactBirthDate;
    status?: ContactStatus;
    email: string;
}

let primaryContact: Contact = {
    id: 12345,
    name: "Jamie Johnson",
    status: "active"
}

// Defines a type alias consisting of all of the properties on the contact type
type ContactFields = keyof Contact;

// The propertyName can just have an existing property of T
function getValue<T>(source: T, propertyName: keyof T) {
	return source[propertyName]

const value = getValue({min: 1, max: 200}, "min") // only min | max
```

## Generic constraints with keyof
```typescript
// The second parameter is limited by the properties on the generic T type
function getValue<T, U extends keyof T>(source: T, propertyName: U) {
	return source[propertyName] 
}

const value = getValue({min: 1, max: 200}, "min")
```

# Typeof operator
+ compile runtime
+ Returns the type 

```typescript
const x = "string"
const y = true
console.log(typeof x) // --> "string"
console.log(typeof y) // --> "boolean"
 

type ContactName = string;
type ContactStatus = "active" | "inactive" | "new"
type ContactBirthDate = Date | number | string

interface Contact {
    id: number;
    name: ContactName;
    birthDate?: ContactBirthDate;
    status?: ContactStatus;
}

function toContact(nameOrContact: string | Contact): Contact {
    if (typeof nameOrContact === "object") {
        return {
            id: nameOrContact.id,
            name: nameOrContact.name,
            status: nameOrContact.status
        }
    }
    else { // Tsc infers automatically that the type is string
        return {
            id: 0,
            name: nameOrContact,
            status: "active"
        }
    }
}

const myType = {min: 1, max: 200}

// The parameter source must match the same structure as myType
function save(source: typeof myType) {}
```

# Indexed access types
+ Determine the type of a certain property
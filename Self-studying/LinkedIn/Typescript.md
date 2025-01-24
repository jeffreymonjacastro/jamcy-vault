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
+ It's the same as javascript syntax 

```typescript
type ContactStatus = "active" | "inactive" | "new";

interface Address {
    street: string;
    province: string;
    postalCode: string;
}

interface Contact {
    id: number;
    name: string;
    status: ContactStatus;
    address: Address;
}

type Awesome = Contact["id"]; // Awesome will be a number
type Awesome2 = Contact["address"]["postalCode"]; // Awesome will be a string

interface ContactEvent {
    contactId: Contact["id"];
}

interface ContactDeletedEvent extends ContactEvent { 
}

interface ContactStatusChangedEvent extends ContactEvent { 
    oldStatus: Contact["status"];
    newStatus: Contact["status"]; 
}

interface ContactEvents {
    deleted: ContactDeletedEvent;
    statusChanged: ContactStatusChangedEvent;
    // ... and so on
}

function getValue<T, U extends keyof T>(source: T, propertyName: U) {
    return source[propertyName];
}

// IDK what is going on, but it referes to index types
function handleEvent<T, U extends keyof ContactEvents>(
	eventName: T,
	handler: (evt: ContactEvents[T]) => void
) {
	if (eventName === "statusChanged") {
		handler({contactId: 1, oldStatus: "active", newStatus: "inactive"})
	}
}

handleEvent("statusChanged", evt => evt)
```

# Record type
+ Avoids using any type
+ Is a very flexible type definition that allows you to define some structures and even some typing without having to detail every possible property of the type youre trying to describe
+ Syntax:
	+ It's a generic syntax with two generic parameters
	+ The first parameter is the possible property values
	+ The second is the possible property types

```typescript
// Not recommended using any
let x: any = { name: "Wruce Bayne" };
x.id = 1234;
x = "banana";
x = true;
x = () => console.log("awesome!");

let x: Record<string, string | number | boolean | Function > = {name: "Wruce Bayne"}
x.number = 1234;
x.active = true;
x.log = () => console.log("awesome!");

////////////////////

type ContactStatus = "active" | "inactive" | "new";

interface Address {
    street: string;
    province: string;
    postalCode: string;
}

interface Contact {
    id: number;
    name: string;
    status: ContactStatus;
    address: Address;
}

interface Query {
    sort?: 'asc' | 'desc';
    matches(val): boolean;
}

function searchContacts(contacts: Contact[], query: Record<keyof Contact, Query>) {
    return contacts.filter(contact => {
        for (const property of Object.keys(contact) as (keyof Contact)[]) {
            // get the query object for this property
            const propertyQuery = query[property];
            // check to see if it matches
            if (propertyQuery && propertyQuery.matches(contact[property])) {
                return true;
            }
        }

        return false;
    })
}

const filteredContacts = searchContacts(
    [/* contacts */],
    {
        id: { matches: (id) => id === 123 },
        name: { matches: (name) => name === "Carol Weaver" },
    }
);
```

# Using statement
+ Ensures that the resources your application is consuming are properly cleaned up after use even when the code using them results in an error.
+ Makes applications more reliable and mantainable

```typescript
class TempData {
	private filePath: string;
	
	constructor(id?: string) {
		this.filePath = `${id || new Date().toISOString()}.txt`;
	}

	write(data: string) {
		fs.writeFileSync(this.filePath, data);
	}

	clear() {
		fs.unlinkSync(this.filePath);
	}

	// For using keyword to clean up
	[Symbol.dispose]() {
		this.clear();
	}
}

function writeTempData() {
	using temp = new TempData();
	temp.write("This is great!");
}

writeTempData();
```

# Extending and modifying existing types
+ Utility types that allow you to extend from existing types, like record, but pick and choose which properties you want to include and exclude in your new type.
	+ **Partial:** Creates a new type that looks exactly like the type it wraps, but with all of its partials defined as optional
	+ **Omit:** the omit helper is a generic type that wraps another type and copies that type's definition, but, like its name suggests, it allows you to omit certain properties from that cloned definition. Unlike partial, however, the omit helper requires a second generic parameter, the list of property names that you'd like to omit.
	+ **Pick:** It creates a new type using only the properties named by its second generic parameter.
	+ **Required:** which is the opposite of the partial helper, turning all properties of a type to required properties, instead of optional.

```typescript
type ContactStatus = "active" | "inactive" | "new";

interface Address {
    street: string;
    province: string;
    postalCode: string;
}

interface Contact {
    id: number;
    name: string;
    status: ContactStatus;
    address: Address;
}

interface Query {
    sort?: 'asc' | 'desc';
    matches(val): boolean;
}

// Partial type
type ContactQuery = Partial<Record<keyof Contact, Query>>;

// Omit type
type ContactQuery = 
	Omit<
		Partial<
			Record<keyof Contact, Query>
		>, 
		"address" | "status"
	>;

// Pick type
type ContactQuery = 
	Partial<
		Pick<
			Record<keyof Contact, Query>,
			"id" | "name"
		> 
	>;
	
// Required
type RequiredContactQuery = Required<ContactQuery> 

function searchContacts(contacts: Contact[], query: ContactQuery) {
    return contacts.filter(contact => {
        for (const property of Object.keys(contact) as (keyof Contact)[]) {
            // get the query object for this property
            const propertyQuery = query[property];
            // check to see if it matches
            if (propertyQuery && propertyQuery.matches(contact[property])) {
                return true;
            }
        }

        return false;
    })
}

const filteredContacts = searchContacts(
    [/* contacts */],
    {
        id: { matches: (id) => id === 123 },
        name: { matches: (name) => name === "Carol Weaver" },
    }
);
```

# Extracting metadata from existing types
+ Mapped

```typescript
type ContactStatus = "active" | "inactive" | "new";

interface Address {
    street: string;
    province: string;
    postalCode: string;
}

interface Contact {
    id: number;
    name: string;
    status: ContactStatus;
    address: Address;
}

interface Query {
    sort?: 'asc' | 'desc';
    matches(val): boolean;
}

type ContactQuery = {
	[TProp in ]
}

function searchContacts(contacts: Contact[], query: ContactQuery) {
    return contacts.filter(contact => {
        for (const property of Object.keys(contact) as (keyof Contact)[]) {
            // get the query object for this property
            const propertyQuery = query[property];
            // check to see if it matches
            if (propertyQuery && propertyQuery.matches(contact[property])) {
                return true;
            }
        }

        return false;
    })
}

const filteredContacts = searchContacts(
    [/* contacts */],
    {
        id: { matches: (id) => id === 123 },
        name: { matches: (name) => name === "Carol Weaver" },
    }
);

```
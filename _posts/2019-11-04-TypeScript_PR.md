---
layout: post
title:  PR_Type Script
date:   2019-11-04
excerpt: "Just about TypeScript Practice"
tag:
- Type Script
comments: true
---

## Type Script Practice
Use Type Script debugger by <a href="https://github.com/Enterprise-JS/vscode-ts-node-debugging">vscode-ts-code-debugging</a><br>
Code and Explanation is in.<br>
Is is refered <a href="https://www.youtube.com/playlist?list=PLlSZlNj22M7QxeiQkge94penoAixMJMMF">Team Jupeter</a><br>

#### 1st Class and Calling
<ul>
<li>Class_Call : index.ts<br>{% highlight typescript %}
import { Person } from './person';

let person = new Person('Bob', 34);

console.log(person.getGreeting());
{% endhighlight %}</li>

<li>Class : person.ts<br>{% highlight typescript %}
export class Person {

    constructor(
        public name: string,
        public age: number) {
    }

    getGreeting() {
        return 'Hi ' + this.name;
    }

}
{% endhighlight %}</li>
</ul>

#### 2nd Hello World
<ul>
<li>Hello TypeScipt : index.ts<br>{% highlight typescript %}
class Greeting {
    greet():void {
        console.log("Hello Type Script!!")
    }
}

var obj = new Greeting();
obj.greet();
{% endhighlight %}
</li>
</ul>

#### 3rd Scope
<ul>
<li>Scope : index.ts<br>{% highlight typescript %}
// global variable
var global_num = 12;

class Numbers {
    // can't write action like console.log();
    // because class has only property (variable and function)

    // class variable
    num_val = 13;
    // static field
    // call every where
    static sval = 10;

    storeNum(): void {
        // function variable
        var local_num = 14;
    }
}

console.log("Global num: " + global_num);
console.log(Numbers.sval);
var objs = new Numbers();
console.log("Class num: " + objs.num_val);
// Error : obj.sval
{% endhighlight %}
</li>
</ul>

#### 4th Conditional
<ul>
<li>Conditional : index.ts<br>{% highlight typescript %}
var num:number = -2;
// conditional
var result:string = num > 0 ?"positive":"non-positive";
console.log(result)
{% endhighlight %}
</li>
</ul>

#### 5th Loops
<ul>
<li>Loops : index.ts<br>{% highlight typescript %}
var i:number = 1;

while (i <= 10) {
    console.log(i);

    if (i % 5 == 0) {
        console.log("The first multiple of 5 between 1 and 10 is : " + i);
        // break out this while
        break;
    }
    i++;
}

console.log("the end");

var num:number = 0;
var count:number = 0;

for(num=0; num<=20; num++){
    if (num % 2 == 0) {
        // move next loops -> don't work after continue in loops
        // => don't work count++ / console.log
        continue
    }
    count++
    console.log(num);
}
console.log(" The count of odd values between 0 and 20 is : " + count);
{% endhighlight %}
</li>
</ul>

#### 6th Variable
<ul>
<li>Variable : index.ts<br>{% highlight typescript %}
// Type Script variable is let not Var!!!
let fullName: string = 'Artyrie';
let age: number = 23;

// single quote ''
// double quote ""
// back quote ``
// Why use back quote?
// It works well even it has special string like '
// and It can call variable that can calculate in ``
let sentence: string = `Hello, my name is ${ fullName }.
I'll be ${ age + 1 } years old next month.`;

console.log(sentence);
{% endhighlight %}
</li>
</ul>

#### 7th Function
<ul>
<li>Function : index.ts<br>{% highlight typescript %}
function disp_details(id:number, name:string, mail_id?:string): void {
    
    console.log("ID:", id);
    console.log("Name", name);

    if(mail_id != undefined){
        console.log("Emial Id", mail_id);
    }

    // parameter id can't used out function
}

disp_details(123, "John");
disp_details(111, "mary", "mary@xyz.com");
{% endhighlight %}
</li>
</ul>

#### 8th Interface
<ul>
<li>Interface : index.ts<br>{% highlight typescript %}
// user defined data type
interface LabelledValue {
    label: string;
}

// use user defined data type labelledValue
function printLabel(labelledObj: LabelledValue) {
    console.log(labelledObj.label)
    ;
}

// Why can use unexpected parameter size?
// It doesn't occur error but, can't use 'labelledObj.size' in printLabel
// Because interface LabelledValue doesn't have size.
let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
console.log(myObj);

interface SquareConfig {
    // variable?: type <- opional
    // exits or not exits
    // All possible.
    color?: string;
    width?: number;
}

console.log("Second Example");

// after parameter {} <- return
function createSquare(config: SquareConfig): {color: string; area: number}{
    // default value
    let newSquare = {color: "white", area: 100};
    // if color exists
    if (config.color) {
        newSquare.color = config.color;
    }
    if (config.width) {
        newSquare.area = config.width * config.width;
    }

    return newSquare;
}

// It can work because ptional property 'width'
let mySquare = createSquare({color: "black"});
console.log(mySquare.color);
// return default value area: 100
console.log(mySquare.area);
{% endhighlight %}
</li>
</ul>

#### 9th Class basic
<ul>
<li>Class : index.ts<br>{% highlight typescript %}
// class has Capital first alphabet
class Greeter {
    greeting: string;

    // constructor execute when class called
    constructor(message: string) {
        this.greeting = message;
    }

    greet() {
        return "Hello, " + this.greeting;
    }
}

let greeter = new Greeter("World!");
console.log(greeter.greet());
console.log(greeter.greeting);
{% endhighlight %}
</li>
</ul>

#### 10th Inheritance Class
<ul>
<li>Inheritance Class : index.ts<br>{% highlight typescript %}
class Animal {
    name: string;
    constructor(theName: string) {
        this.name = theName;
    }

    // define default of parameter : 0
    move(distanceInMeters: number = 0) {
        console.log(`${this.name} moved ${distanceInMeters}m.`);
    }
}

let dog1 = new Animal("Mong");
console.log(dog1.move());
console.log("1st end");

// Dog inherit Animal
class Dog extends Animal {
    constructor(name: string) {
        // what is super?
        // call parents constructor
        super(name);
    }
    // define parameter with value
    // same to super move. default value : 5
    // Inherited priority is more high than parent
    move(distanceInMeters = 5) {
        console.log("Meong...");
        // Difference of super
        super.move(distanceInMeters);
    }
}

let dog2 = new Dog("Navi");
console.log(dog2.name);
console.log(dog2.move());
console.log("2nd end");
console.log(dog2.name);
console.log(dog2.move(10));
console.log("3rd end");
{% endhighlight %}
</li>
</ul>

#### 11th Type; Public, Private, Protected
<ul>
<li>Type; Public, Private, Protected : index.ts<br>{% highlight typescript %}
class Animals {
    // protected name: string => Only use in class and Inhertied class
    protected name: string;
    // private name: string => Only use in class
    // If you want to get private value, make function in class
    // Why use? making a limitation that helps not to twist code.
    // public name: string => use everywhere that object animal defined
    age: number = 10;
    constructor(theName: string) {
        this.name = theName;
    }
    animalCall() {
        this.name = "hi";
    }
}

let animal = new Animals("Goat");

class Rhino extends Animals {
    constructor() {
        super("Rhino");
        // If private name: string => can't call this.
        console.log(this.name);
    }
}

let rhino = new Rhino();

class Persons {
    protected name: string;
    constructor(name: string) {
        this.name = name;
    }
}

class Employee extends Persons {
    private department: string;

    constructor(name: string, department: string) {
        super(name)
        this.department = department;
    }

    public getElevatorPtich() {
        return `Hello, my name is ${this.name} and I work in ${this.department}.`
    }
}

let howard = new Employee("Howard", "Sales");
console.log(howard.getElevatorPtich());
{% endhighlight %}
</li>
</ul>

#### 12th Getter Setter Method
<ul>
<li>Getter Setter Method : index.ts<br>{% highlight typescript %}
let passcode = "secret passcode";

class Employees {
    private _fullName: string;

    // Getter Method
    // To get private property
    get fullName(): string {
        return this._fullName;
    }

    // Setter Method
    // To modify private property
    set fullName(newName: string) {
        if (passcode && passcode == "secret passcode") {
            this._fullName = newName;
        }
    }

}

let employee = new Employees();
// Can't use fullName();
// Because it used by set and get method.
// it is called by this form
employee.fullName = "Bob Smith";

console.log(employee.fullName);
{% endhighlight %}
</li>
</ul>

#### 13th StaticProperty
<ul>
<li>StaticProperty
<ul> : index.ts<br>{% highlight typescript %}
// Using interface is formal way.

//interface Point {
//  x: number;
//  y: number;
//}

class Grid {
    // static property : what is used by class
    // => class field that uses in class
    static origin = {
        x: 0,
        y: 0
    };
    //calculateDistanceFromOrigin(point: Point) {
    calculateDistanceFromOrigin(point: {x: number; y: number}) {
        let xDist = (point.x - Grid.origin.x);
        let yDist = (point.y - Grid.origin.y);
        return Math.sqrt(xDist * xDist + yDist * yDist) / this.scale;
    }
    constructor (public scale: number) {}
}

let grid1 = new Grid(1.0);
let grid2 = new Grid(5.0);

console.log(grid1.calculateDistanceFromOrigin({x: 10, y: 10}));
console.log(grid2.calculateDistanceFromOrigin({x: 40, y: 50}));
{% endhighlight %}
</li>
</ul>

#### 14th AbstractClass
<ul>
<li>AbstractClass : index.ts<br>{% highlight typescript %}
// Doesn't make instance and implement
// implement => Action of function.
// Thus don't declare implement in function.
// Thus abstract, we can't use 'department = new Department();'
abstract class Department {
    constructor(public name: string) {}

    printName(): void {
        console.log("Department name: " + this.name);
    }

    // doesn't have implement
    abstract printMeeting(): void;
}

class AccountingDepartment extends Department {
    constructor() {
        super("Accounting and Auditing");
    }

    printMeeting(): void {
        console.log("The Accounting Department meets each Monday at 10am.");
    }

    // Parents doesn't have this function.
    // So, declare is possible but we can't use this.
    generateReports(): void {
        console.log("Generating accountung reports...");    
    }
}

let department: Department;
//Error
//department = new Department();
department = new AccountingDepartment();
department.printName();
department.printMeeting();
//Error
//department.generatingReports();
{% endhighlight %}
</li>
</ul>

#### 15th Function Type
<ul>
<li>Function Type : index.ts<br>{% highlight typescript %}
// function add(x: any, y: any) {
// any type is used by all type.
// but it destoryed typescript's goodness.

// Named function
// add(~): number << number is function's type.
// => Function's type is return value's type.
function add(x: number, y: number): number {
    return x * y;
}

// Anonymous function
// => doens't have name.
let myAdd = function(x: number, y: number) {
    return x + y;
};
console.log(myAdd(2, 3));
{% endhighlight %}
</li>
</ul>

#### 16th Optional Parameter
<ul>
<li>Optional Parameter : index.ts<br>{% highlight typescript %}
// lastName? <- optional parameter.
// Exits or none. all possible.

// function buildName(fistName: string, lastName="Artyrie"): string {
// Defining parameter's default value to lastName="Artyrie" 
function buildName(firstName: string, lastName?: string): string {
    return firstName + " " + lastName;
}

// ...parameter: string << doesn't # of limit arguments 
function buildNames(firstName: String, ...restOfName: string[]): string {
    console.log(arguments[0]);
    console.log(arguments[1]);
    console.log(arguments[2]);
    console.log(arguments[3]);

    return firstName + " " + restOfName.join(" ");
}

let result1 = buildName("Bob");
let result2 = buildName("Bob", "Adams");
console.log(result1);

let employeeName = buildNames("Joseph", "Samuel", "Lucas");
console.log(employeeName);
{% endhighlight %}
</li>
</ul>

#### 17th Generics
<ul>
<li>Generics : index.ts<br>{% highlight typescript %}
// Use Generic for use more 2 function's type.
// Thus T, we can use String type and Number
function identity<T>(arg: T): T {
    return arg;
}

let output = identity("Artyrie");
let output2 = identity(35);
let output3 = identity<string>("Art");

console.log(output);
console.log(output2);
console.log(output3);
{% endhighlight %}
</li>
</ul>

#### 18th Enum
<ul>
<li>Enum : index.ts<br>{% highlight typescript %}
// to use not value, use word (Constance)
// instead number, use word

enum Driection {
    Up, // Auto 0 if Up=1, declare 1~4
    Down, // Auto 1
    Left, // Auto 2
    Right, // Auto 3
}

console.log(Driection.Left);
{% endhighlight %}
</li>
</ul>

#### 4th Iterators for List
<ul>
<li>Iterators for List : index.ts<br>{% highlight typescript %}
let list = [4, 5, 6];

// index number
for (let i in list) {
    console.log(i); // "0", "1", "2"
}

// index value
for (let i of list) {
    console.log(i); // "4", "5", "6"
}
{% endhighlight %}
</li>
</ul>

#### 20th Module; Import and Export
<ul>
<li>Module; Import and Export : index.ts<br>{% highlight typescript %}
// Global value => Module value
// validate is maden function name
import validate from "./StaticZipCodeValidator";

let strings = ["Hello", "98052", "101"]

strings.forEach(s => {
    console.log(`"${s}" ${validate(s) ? "matches" : "does not match"}`);
});
{% endhighlight %}
</li>

<li>Module; Import and Export : StaticZipCodeValidator.ts<br>{% highlight typescript %}
const numberRegexp = /^[0-9]+$/;

// export : in this function -> other module(other file and program) can use.
// by export, what variable is declared in this file can't out this file.
// So, if you want to use in this file, you have to use import like index.ts

// default : who person use this function can make function name
export default function (s: string) {
    // test method is in Regexp.
    return s.length === 5 && numberRegexp.test(s);
}
{% endhighlight %}
</li>
</ul>

#### 21th Namespaces
<ul>
<li>Namespaces : StaticZipCodeValidator.ts<br>{% highlight typescript %}
interface StringValidator {
    isAcceptable(s: string): boolean;
}

let lettersRegexp = /^[A-Za-z]+$/;
let numberRegexp = /^[0-9]+$/;

// implements? not inherit
// but follow form
class LettersOnlyValidator implements StringValidator {
    isAcceptable(s: string) {
        return lettersRegexp.test(s);
    }
}

class ZipCodeValidator implements StringValidator {
    isAcceptable(s: string) {
        return s.length === 5 && numberRegexp.test(s);
    }
} 

let strings = ["Hello", "98052", "101"];

// object. key form => [s: string] / value form => StringValidator
// => Associative Array
let validators: { [s: string]: StringValidator; } = {};
validators["Zip code"] = new ZipCodeValidator();
validators["Letters only"] = new LettersOnlyValidator();

// strings value
for (let s of strings) {
    // validators index => key
    // Thus validators 2 keys and value, rotate 2 class
    for (let name in validators) {
        let isMatch = validators[name].isAcceptable(s);
        console.log(`'${ s }' ${ isMatch ? "matches" : "does not match" } '${ name }'.`);
    }
}
{% endhighlight %}
</li>

<li>Namespaces : StaticZipCodeValidator2.ts<br>{% highlight typescript %}
// Reduce confused big program
namespace Validation {
    export interface StringValidators {
        isAcceptables(s: string): boolean;
    }

    let lettersRegexps = /^[A-Za-z]+$/;
    let numberRegexps = /^[0-9]+$/;

    // implements? not inherit
    // but follow form
    export class LettersOnlyValidators implements StringValidators {
        isAcceptables(s: string) {
            return lettersRegexps.test(s);
        }
    }

    export class ZipCodeValidators implements StringValidators {
        isAcceptables(s: string) {
            return s.length === 5 && numberRegexps.test(s);
        }
    } 
}

let stringss = ["Hello", "98052", "101"];

let validatorss: { [s: string]: Validation.StringValidators; } = {};
validatorss["ZIP code"] = new Validation.ZipCodeValidators();
validatorss["Letter Only"] = new Validation.LettersOnlyValidators();

for (let s of stringss) {
    for (let name in validatorss) {
        let isMatch = validatorss[name].isAcceptables(s);
        console.log(`'${ s }' ${ isMatch ? "matches" : "does not match" } '${ name }'.`);
    }
}
{% endhighlight %}
</li>
</ul>

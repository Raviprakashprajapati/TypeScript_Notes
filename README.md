#Typescript_Notes

INTRODUCTION:

Typescript is a Superset of Javascript . It was developed by Microsoft . It just a development tool by using the chances of producing the error is much more less as compared to JS. After writting TS code it will compiled into javasscirpt because Browser can only understand html,css js . It just offers type safety to the code

Online TS PlayGround : https://www.typescriptlang.org/play?#code/Q
CheatSheet: https://github.com/rmolinamir/typescript-cheatsheet?tab=readme-ov-file#tuples


Installation and Usage:

Global Installation: npm install -g typescript
Compiling File: tsc <filename>.ts 

Install TS Porject:

tsc --init
npm init -y
create two FOlder dist and src(index.ts)
create index.html
edit out to ./dist
tsc -w it autmatic compile and create index.js in dist

DATATYPES -----------------------------

let variableName: type = value;

Primitive Types: number, string, boolean, symbol, null, undefined
Type Inference: TypeScript can often infer the type from the assigned value.
any Type: Use with caution as it bypasses type checking.


FUNCTION ---------

How to make a function ?

function signUpUser(name: string, email: string, password: string){
}

How to handle return values  in the Funtion ?

function sum(a: number, b: number): number {
    return "hello"
}

To handle Void Fucntion? 

function consoleError(error: string): void{
    console.log(error)
    return "1" //error
}



 OBJECT ------

To handle return Object from the function ?

function createCourse():{name: string, price: number}{
    return {name:"ravi",price:99}
}



Alias -----

type is used like a tmeplate of creating our own Object structure before actual creating actual object 

type User = {
    name: string;
    email : string;
    isActive: boolean;
}

function createNewUser(user: User){

}

createNewUser({name:"Ravi",email:"afsf@gamil.com",isActive:false})



READONLY/OPTIONAL -----

type User = {
   readonly _id: string
    name: string
    creditCardDetails?: number
}

let myUser: User = {
    _id:"12345",
    name:"ravi",
    isActive:false
}

readonly : you will not able to update _id further
? : it is optional


we can combine type Object?

type CardNumber = {
    cardNumber: string
}

type CardDate = {
    cardDate: string
}

type CardDetails = CardNumber & CardDate & {
    cvv: number
}




ARRAY ------

How to define arrays?

const superHeros: string[] = []
const heroPower: number[] = [1,2,3]
const heroPower: Array<number> = [1,2,3]

How to speified array object values ?

type User = {
    name: string
    isActive: boolean
}

const allUsers: User[] = [{},{}]

How to create arrayOfarra\ys?

const  arrayOfarrays: number[][] = [
    [1,2],
    ["ra"] //error
]



UNION ------

Unions allow a variable  to hold more than one  possible types

let score: number | string  = 33

const data:string[] | number[] = ["4"] 
it either all string[] or number[]

const data:(string | number)[] = ["4",8] 

function getDbId(id: string | number ){
    // id.toLowerCase() //eror

    if(typeof id === "string"){  
        id.toLowerCase() 
    }
}


let weeks: "monday" | "sunday"
weeks = "monday"
weeks = "fbgfgf" //error




TUPLES -------

const user: [string, number, boolean] = ["ravi",123,true,]


ENUM -----


const enum SeatChoice {
    MIDDLE=45,
    WINDOW=899
}
by default It has 0

const seat = SeatChoice.WINDOW



INTERFACE -------

 Interfaces define the shape of an object, specifying the properties it must have and their expected types.

 interface User {
    readonly dbId: number,
    email: string,
    userId: number,
    // startTrail: () => string
    startTrail(): string,
    getCoupon(couponName: string): number
}


const ravi: User = {
    email:"ravi@gmail.com",
    userId:123,
    dbId:321135,
    startTrail: () =>{ return "trail started"},
    getCoupon: (name:"ravi")=>{ return 10}
}


we can laos reopen exist interface ?

interface User {
    githubToken: string
}


interface Admin extends User {
    role: "admin" | "learner"
}



TYPE v/s INTERFACE


type cannot be re-opened to add new properties BUT Interface can do it

type cannot be extends BUT interface can do it


ABSTRACT ------

Abstract classes are base classes from which other classes may be derived. They may not be instantiated directly.
The abstract keyword is used to define abstract classes as well as abstract methods within an abstract class.

Methods within an abstract class that are marked as abstract do not contain an implementation and must be implemented in derived classes.

 abstract class TakePhoto {
    
    constructor(
        public camera: string,
        public filter: string
    ){}

    abstract getSepia(): void
    getReelTime(): number {
        return 8
    }
}


abstract class Project {

    projectName: string = 'Default';
    buget: number = 0;

    abstract changeName(name: string): void;
    
    calcBudget(){
        return this.buget * 2;
    }
}






GENERICS 

// function identity4<T>(value: T): T {
//     return value
// }


function getSearchProduct<T>(products: T[]): T {
    
    return products[3]
}

const getMoreSearchProducts = <T>(value:T[]): T =>{
        return value[3]
}


//class generics

class Animal<T> {
    public habits: T[] = []

    addHabits(habit: T){
        this.habits.push(habit)
    }
}





IN is used to verify that this property exist in interface or not


instanceof

function logValue(x: Date | string){
    if(x instanceof Date){
        console.log(x.toUTCString())
    }
}

OPTIONAL OBJECT -?-
const obj: {name: string, age?: number} = {name:"ravi"}


Methods of the Typescript accessor property: 

getter: This method comes when you want to access any property of an object. A getter is also called an accessor.
setter: This method comes when you want to change any property of an object. A setter is also known as a mutator.

Note for using this we cannot need () like regular funciton thus it mkae it more efficient to get and set members of the class no matter it is private or public like this:



public get name()  return this._name;
public set name(name: string) this.name=name;

student.name = "ravi setter"
console.log(student.name)



STATIC Properties & Methods ----

Static properties and methods are class members that can be accessed from an outer scope of the class, and without having to instantiate the class either.

class Helpers {
    static PT: number = 3.14
    static calCircumference(diameter: number): number {
        return this.PT * diameter
    }
}



SINGLETON -----------------

a singleton is a class that can only be instantiated once, or in other words, a class that can only have one object, single(ton).



EXPORT & IMPORTS ====

Modules are executed within their own scope, not in the global scope; this means that variables, functions, classes, etc. declared in a module are not visible outside the module unless they are explicitly exported using one of the export forms. Conversely, to consume a variable, function, class, interface, etc. exported from a different module, it has to be imported using one of the import forms.

#export

export const PI = 3.14
export const calculateCircumfirance = (diameter: number) => diameter*PI
export interface Phone { brand: name }

const PI = 3.14
export default PI

#import

TypeScript v^3.0
├── app.ts
├── src
│   ├── circle.ts
│   ├── rectangle.ts

import {PI,calculateCircumfirance} from "./src/circle.ts"



TYPE ASSERTION ----

In Typescript, Type assertion is a technique that informs the compiler about the type of a variable. Type assertion is similar to typecasting but it doesn’t reconstruct code.

We can either use <> angular brackets or as keywords to do type assertion.

Ex:

let a: unknown = 4554
let b: number = a as number


Ex:
 
let num: any = 77; 
  
// Conversion from any to number 
let num1 = <Number> num; 




UTILITY TYPE_-----------------

Partial changes all the properties in an object to be optional.
type User = {name: string, email: string}
type Admin = Partial<User> 

Required changes all the properties in an object to be required.
type User = {name: string, email?: string}
type Admin = Partial<User> 

Readonly is used to create a new type where all properties are readonly, meaning they cannot be modified once assigned a value. 
const newUser: Readonly<User> = {name:"ra",email:"dss"}

Pick removes all but the specified keys from an object type.
type User2 = Pick<User,"name" | "email">

Omit is opposite of Pick it select all keys except writtern key
type User3 = Omit<User,"name">

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


ABSTRACT

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

# TypeScript_Notes



INTRODUCTION:

Typescript is a Superset of Javascript . It was developed by Microsoft . It just a development tool by using the chances of producing the error is much more less as compared to JS. After writting TS code it will compiled into javasscirpt because Browser can only understand html,css js . It just offers type safety to the code

Online TS PlayGround : https://www.typescriptlang.org/play?#code/Q


Installation and Usage:

Global Installation: npm install -g typescript
Compiling File: tsc <filename>.ts (creates a corresponding .js file)
Syntax:



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

type is used like a tmeplate of creating Object

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

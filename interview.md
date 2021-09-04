************************************************************************************************************//
**How Javascript works!

1. Everything in Javascript happens inside an Execution Context. when a code runs execution context is created
    assume that it is like big box or container by whole javascript code will be executed!!
    it has 2 components 
MEMORY AND CODE Component
    in memory components varibles and functions are stored as key-value Pair//MEMORY components is   known  as Varible environment.
    in code components code will be executed one line at time// CODE Components is also known as THREAD OF EXECUTION 

JAVASCRIPT IS SINGLE THREADED SYNCHRONOUS LANGUAGE. it will execute  one command at time in specific order.

3 phases when code runs
1. MEMORY CREATION= allocate the memory for varibales and functions
2. CODE EXECUTION

then comes the stack //CALL STACK
call stack handles the each phase 
whenever code runs that times execution context is pushed into call stack
bottom of the stack there is Global execution context
CALL STACK MAINTAIN THE ORDER OF EXECUTION OF EXECUTION CONTEXTS
CALLSTACK IS KNOW BY THIS NAMES AS WELL
1.EXECUTION CONTEXT STACK
2.PROGRAMME STACK
3.RUNTIME STACK
4.MACHINE STACK
---

**HOISTING IN JS
      Hoisting is phenomenon in which you can access the variable and function even before declare/initialize it.

var a=7
function demo(){
     console.log('namaste MAHARASHTRA');
}

console.log(a);
console.log(demo);
---
differnece between Undefined and not define

undefined is the default value of
a variable that has not been assigned a specific value.
a function that has no explicit return value.
  let a;
console.log(a);

not defined means variable is not declared or defined

null is
a value that represents no value.
a value that has been explicitly defined to a variable.
For example, we get a value of null when the fs.readFile method does not throw an error.
---
**Scopes** in js
scope mean where you can access a variable and function
..scope is depend on lexical environment
lexical means in order/herarcy
local memory+ lexical environments of parents
----
**closures**
global scope
let iHaveGlobalScope=`I can be accessed from anywhere in this document`

function localScope()
{
    console.log(iHaveGlobalScope)

    // lcoal scope1
    let iHaveLocalScope=`I am bound to the local scope of function localScope`
    }


console.log(localScope())
I can be accessed from anywhere in this document

console.log(iHaveLocalScope)
ReferenceError: iHaveLocalScope is not defined

function Scope
function functionScope(){
     var iHaveFunctionScope=`something something mj`
     console.log(iHaveFunctionScope)
 }
 functionScope()
 something something mj

 console.log(iHaveFunctionScope);
 Reference Error 

var outerFunction = function () {
     let variable1 = "Example of closure"

     var innerFunction = function () {
         console.log(variable1)


     }
     return innerFunction;
 }

 var newFunction = outerFunction()
 newFunction()
Example of closure

---

**IIFE**
It’s an Immediately-Invoked Function Expression, or IIFE for short. It executes immediately after it’s created:

(function IIFE(){
     console.log( "Hello!" );
 })();
 // "Hello!"

 This pattern is often used when trying to avoid polluting the global namespace, because all the variables used inside the IIFE (like in any other normal function) are not visible outside its scope.

---
NPM

npm stands for Node Package Manager. npm provides following two main functionalities:
Online repositories for node.js packages/modules which are searchable on search.nodejs.org
Command line utility to install packages, do version management and dependency management of Node.js packages.
---
Callbacks are simply Functions In JavaScript which are to be called and then executed after the execution of another function has finished.
The problem with callbacks is that when the application gets bigger, we have to do a lot of nesting which can lead to what is called callback hell . Error handling becomes difficult in this situation. Hence JavaScript gave us a solution called promises introduced in ES6
function a(){
console.log("hello");
}
function b(cb){
    cb()
    console.log('navgururkul');

}
b(a)

Example no-1
setTimeout(function() {  
    console.log('hello1');  
  }, 2000)
console.log(numbers);

Example no-2
console.log('start');
function sam(cb){setTimeout(() => {
     cb('we are in setTimeout'); 
}, 2000)}
let d=sam(data=>{console.log(data);})
console.log('end');

Example no-3
const fs=require('fs')
fs.promises.readFile('t.txt',)
.then((result) => {
     console.log(result.toString());
}).catch((err) => {

     console.log(er);
});
---

///////////////////////////fething api with promises///////////////////
**promises** in javascript........
promises are introduced  for handling asynchronous operations in javascript
Promises Promises provide a mechanism to handle the results and errors from asynchronous operations. You can accomplish the same thing with callbacks, but promises provide improved readability via method chaining and succinct error handling.
They are easy to manage when dealing with multiple  asynchronous operation where callbacks can create callback hell leading to unmanageable code
A promise is an object that keeps track of whether a certain event has happened already or not.
Determines  what happens after the events have happened.


var mypromise = new Promise(
    (resolve, reject) => {
        var b = false
        if (b) {
            resolve('ok');
        }
        else {
            reject('rejected');

        }
    }
)

mypromise.then(()=>
    console.log('success'))
.catch(()=>
console.log('rejected'))
console.log(mypromise);

**Fetching a api using node-fetch module  by PROMISES
const fetch = require('node-fetch');
const url="https://pokeapi.co/api/v2/pokemon"
fetch(url)
.then((res) =>res.json())
.then((data)=>console.log(data))

.catch((err) => {
     console.log(err);
});
---
//////////////////////////////////////////fetching api with Async await/////////////////////////////
** ASYNC AWAIT 
const onfetch=async()=>{
     const res=await fetch(url)
     const data=await res.json()
     console.log(data);
}
onfetch()
---
//////////////////////////////////////////////////////////////////////////////////////////////////////////////
genreators in js. specal function that can return multiple values and can be paused and resumed in the executions of middway
function* oddNumberFinder(numbers) {
    for (const i of numbers) {
        if (i % 2 === 1) {
            yield i;
        }
    }
}

const numbers = Array.from(Array(20).keys())
    .sort((a, b) => Math.random() > 0.5 ? 1.0 : -1.0);

const oddNumbers = oddNumberFinder(numbers);

console.log(oddNumbers);
let num

while (num = oddNumbers.next().value) {
    console.log('Number: ' + num);
}
---
/////////////////////////////////////////////////////////////////////////////////////////////////////////////
**create server using http module in node>js**
const http = require('http')
    const server = http.createServer((req, res) => {
        console.log(req.url);
        if (req.url == '/') {
            res.end('hello bhai log')
        }
        else if (req.url == '/mypage') {

            res.end('this is my page');
        }

        else {
            res.writeHead(404,{"content-type":"text/html"})
            res.end('404 page not found') }
    });

    server.listen(8000, '127.0.0.1', () => {
        console.log('i am listening')})

---
/////////////////////////////////////////////////////////////////////////////////////////////////////////////
**What is NodeJS ?**
Node.js is a web application framework built on Google Chrome's JavaScript Engine (V8 Engine).
Node.js comes with runtime environment on which a Javascript based script can be interpreted and executed (It is analogus to JVM to JAVA byte code). This runtime allows to execute a JavaScript code on any machine outside a browser. Because of this runtime of Node.js, JavaScript is now can be executed on server as well.

most important that it performs the non-blocking I/O operations
Node.js = Runtime Environment + JavaScript Library


**Node.js is a Server-side scripting which is used to build scalable programs.


Node JS is a JavaScript framework that allows us to use JavaScript outside of the browser and on the server-side.The Server-side is the system that runs on the server (Node JS runs here), and the client-side is the software that runs on a user's web browser (Vanilla JavaScript or React JS runs here). </p>

 **What is Express ?**
<p> Express JS is a popular framework of Node JS that makes it easier to manage web applications, Express JS is the E in both M*ERN and ME*AN stack.</p>   


CORE MODULES IN NODE.JS
EventEmitter
Stream
FS
Net
Global Objects
---
//////////////////////////////////////////////////////////////////////////////////////////////////
**WHY NODE JS IN SINGLE THREADED ?

For async processing, Node.js was created explicitly as an experiment. It is believed that more performance and scalability can be achieved by doing async processing on a single thread under typical web loads than the typical thread-based implementation.

more performance and scalability can be achieved by doing async processing on a single thread under typical web loads than the typical thread-based implementation.

The two types of API functions in Node.js are
a) Asynchronous, non-blocking functions
b) Synchronous, blocking functions
---
/////////////////////////////////////////////////////////////////////////////////////////////////////////////
What is EVENT-DRIVEN programming ?

In computer programming, event-driven programming is a programming paradigm in which the flow of the program is determined by events like messages from other programs or threads.

SIMPLY FLOW OF PROGRAM IS DETERMINED BY EVENTS LIKE MESSAGES AND THREADS

It is an application architecture technique divided into two sections

1) Event Selection
 2) Event Handling
---
/////////////////////////////////////////////////////////////////////////////////////////////////////////////



**REACT
/////////////////////////////////////////////////////////////////////////////////////////////////////////////
AngularJS 
is a web application development framework. It’s a JavaScript and it is different from other web app frameworks written in JavaScript like jQuery. NodeJS is a runtime environment used for building server-side applications while AngularJS is a JavaScript framework mainly useful in building/developing client-side part of applications which run inside a web browser.


///////////////////////////////////////ORM////////////////////////////////////////////////////////////////////
(**************Databases*************************)
two types sql and no-sql
SQL
SQL or Structured Query Language is pronounced as “S-Q-L” or sometimes as “see-quel” is a standard language to access and manipulate Relational Databases.
Common and Popular Examples of Relational Databases which use SQL are —

MySQL

Oracle

SQLite

Postgres

MS-SQL

No-SQL
As the name suggests NoSQL is “not” SQL, in other words, it is a non-relational database and is unstructured. Due to its unstructured nature, it is sometimes called as UnQL

Common and Popular Examples of NoSQL Databases are —

Mongo DB

BigTable

Cassandra

Hbase

Redis
As the name suggests NoSQL is “not” SQL, in other words, it is a non-relational database and is unstructured. Due to its unstructured nature, it is sometimes called as UnQL

ORM stands for "Object to Relational Mapping" where
it allows you to call and manipulate data from the database using your language of choice instead of SQL.

The Object part is the one you use with your programming language ( python in this case )

The Relational part is a Relational Database Manager System ( A database that is ) there are other types of databases but the most popular is relational ( you know tables, columns, pk fk etc eg Oracle MySQL, MS-SQL )

And finally the Mapping part is where you do a bridge between your objects and your tables.
//////////////////////////////////////////////////////////////////////////////////////////////////////////////
---
1) TO display top 20 in rows
Query is
SELECT   * FROM table_name LIMIT 0,20;
//////////////////////////////////////    **default port is 3006
2) To show timestamp
select NOW();
//
3) To show dateString
select CURRENT_DATE();

4) To count the number of the rows
select COUNT user_id from table_name;
////////////////////////////////////
increasing order query
select city,temperature form weather ORDER BY  temperature;
//////////////////////////////////////
ADD COLUMNS IN TABLES
ALTER TABLE table_name ADD column_name;
////////////////////////////////////////

ENUM
---
AGREGATE FUNCTIONS IN MYSQL
1. MAX
2. MIN
3. COUNT
4. SUM
5. AVG

To get max value(sallery)
   select MAX(sallery) from Employee_table;
To get min value(sallery)
   select MIN(sallery) from Employee_table;
To get count of sallery;
   select COUNT(sallery) from Employee_table;
   to get unique(not duplicate) count of sallery from employee table
      SELECT DISTINC(COUNT(sallery)) from Employee_table;

To get Sum  of sallery;
   select SUM(sallery) from Employee_table;
   to get unique(not duplicate) SUM of sallery from employee table
      SELECT DISTINC(SUM(sallery)) from Employee_table;

To get AVERAGE 
avg=sum(sallery)/count(sallery)
---
////////////////////////
**  JOINS IN MYSQL */
JOINS are used to retrieve data from multiple tables. A MySQL JOIN is performed whenever two or more tables are joined in a SQL statement
to join two table it must have something common in between this two tables;
** types of JOIN */
1. CROSS JOIN
2. NATURAL JOIN  //// **MOST IMPORTANT JOIN
3.CONDITIONAL JOIN
4.  EQUE JOIN
5. SELF  JOIN
6. OUTER JOIN 
         1-LEFT
         2-RIGHT
         3-FULL
         
         
---
//////////////MAX/////////////////////////////////////////////////////////////////////////////////////////////
**LOGICAL QUESTIONS
var secondMax = function (){ 
    var arr = [20, 120, 111, 215, 54, 78]; // use int arrays
    var max = Math.max.apply(null, arr); // get the max of the array
    arr.splice(arr.indexOf(max), 1); // remove max from the array
    return Math.max.apply(null, arr); // get the 2nd max
};
console.log(secondMax());
---
//////////////////////////////////////////////////////////////////////////////////////////////////////////////
function nextBiggest(arr) {
     let max = -Infinity, result = -Infinity;
     for (const value of arr) {
          const nr = Number(value)
          if (nr > max) {
               [result, max] = [max, nr] // save previous max              
          }
          else if (nr < max && nr > result) {
               result = nr; // new second biggest
          }
     }
     console.log(result)]

}
const arr = ['20', '120', '111', '215', '54', '78'];
nextBiggest(arr);
/////////////////////////////////////////
   here's your array :
var stringArray = new Array('20','120','111','215','54','78');
// let's convert it to a real array of numbers, not of strings :
var intArray = stringArray.map(Number);
console.log(intArray);
// now let's sort it and take the second element :
var second = intArray.sort(function(a,b){return b-a});
console.log(second);
/////////////////////////////////////////////////////////////////
map is a higher order function used to transform a list, returning a new list:
const arr = [11, 4, 5, 6, 15, 1, 9]
let a = 0
arr.forEach(i=>{
     console.log(i);
})

arr.map((i) => {
     if (a < i) {
          a = i
          console.log(i);

     }
})
console.log(a);
/////////////////////////////////////
arr.filter(i=>{
     console.log(i);
})

arr.map(i=>{
     console.log(i);
})
/

2nd max
prime number//time complextiy
find out duplicate from array
////////////////////////////////////////
const fs=require('fs')
fs.writeFile("t1.json","utf-8",(er,data)=>{
if(er){
   console.log(er);
}
console.log(data);
})



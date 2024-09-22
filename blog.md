## what is node js ?
1.Node.js is an open-source Javascript runtime(	Written in JavaScript, C++, Python, C)
2.Uses the V8 Javascript Engine that Google Chrome Uses
3. Takes the Javascript out of the browser
4.Fast and Scalable and Popular in many areas of the Industry

## What Cover in this Cource ?
What is Node.js and how does it work?

Installation, setup, package.json, npm, etc

Modules import/export (CommonJS & ES Modules)

HTTP Module, req/res, routing, serving JSON/HTML

Custom middleware

Other Core Modules - fs, path, url, events, process, os
...
## Let Start :

npm stands for Node Package Manager;(it fecilitates to install packages)

npm install in short form : npm i  (here i means install)

***|| a  node.js runs in a single process , without creating a new thread for every request

***|| node.js uses event-driven , non blocking I/O model to hande cuncurrent request with a single thread

**|| host in anywhere ...

##<CHAPTER _ 01> --------------------------------(<BASICS-WE-NEED-FOR-NODE>)---------------------->

BY using NODE.JS we Can BUild  ....
       ---- Streaming Web Applications Like NetFLix, Amazon
       ---- Real-Time Web Applications Like Chat , IM(instant messaging)
       ----MicroServices and IOT Applications 
       ---- Any <MERN-STACK> Application like E-Commerce,Payments etc..
       ----Social Media And Networking Applications Like LinkedIN,Medium 
       ---- Creating REST-FULL API's

DIFF BETWEEN  NODE.JS AND BROWSER  :
   --- Both Node.js and Browser USe JS and Their Programming Launguage..

   --- Building apps that runs in the Browser that is completely Different With Building a  Node.js Application

   With Browser We have Access to the <DOM>,<WebAPi> whereas in the Node.js We have Modules Provide to access to file System , OS.

   --<IMP> Node.js Suppors both the Common-JS <require()> and ES Module Systems <import()>
   While in the Browser  we are Starting to see the ES Modules Standards Being implimented

   BEFORE JUMP TO NODE.JS YOU SHOULD KNOW THE THESE JS CONCEPTSSS....

   1.Classes              4.Scopes & Loops   7. Async Prog & Call-backs
   2.Arrays & Objects     5. Async & Wait    8. Async Prog & Callbacks
   3.Functions            6. Closures        9. Event loop

   10. variable
   11. Expression 
   12. Types


## .env extension :
    in .env file :{
    NAME ="AJEYA"
    PROFF="STUDENT"
    COURSE="NODE"
    }
    in index.js file :{
    require("dotenv").config();  || or use command in cmd (node -r dotenv/config _yr_file_name.js)
    console.log(process.env.NAME);
    console.log(process.env.PROFF);
    console.log(process.env.COURSE);
    }
  ## Learn Little Bit About REPL (module) of node (READ EVALUATE PRINT LOOP)-->node cosole(to enter into that simply type  command "node" and hit enter)


## repl in index.js as module import :
     const repl = require("repl");
     const local = repl.start("root $ ");
   
     local.on("exit",()=>{
     console.log("Bye From REPL");
     process.exit();
    })

## argv funct :
    (giving input through cmd can accepted by this process.argv only)
    process.argv:
    process.argv is an array in Node.js that contains the command-line arguments passed when the script was executed.
    The first two elements of this array are:
    process.argv[0]: The path to the Node.js executable.
    process.argv[1]: The path to the script being executed.
    The remaining elements (starting from process.argv[2] onward) are the actual arguments passed by the user.

    const minimist = require("minimist");
    console.log(process.argv);
    console.log(process.argv.slice(2)[0]);
    process.argv.forEach((val,ind)=>{
    console.log(`${ind} -> ${val}`);
    })
    const nw = minimist(process.argv.slice(2));
    console.log(n
    w.name);

<console function in Node (output module functionss)>*** :
          let x=30;
          let y=5;

          console.log(x+y);
          </ Format Specifiers >
          1. %s for strings
          2. %d for numebers
          3. %i for integer type
          4. %o for objects 

          console.log("%s is aged about %i","ajay",18);

          console.clear(); // this will clear your console when you run this file

          console.count("Krishnaa");
          console.count("Krishnaa");
          console.count("Krishnaa");
          console.count("Ajeyaa");
          console.countReset();
          console.count("Krishna");
          console.count("Ajey");

****<TO-SEE-STACK-OF-YOUR-CODE(function)> --- You Can Print the Stack of Your Witten Functions in your code
    const fun1 = ()=> console.trace();

    const func2 = ()=> fun1();

    func2();

    OUT_PUT : (here function 2 called first and then func1 so fuc1 one should appear on top of the stack...)

    35
    Trace
        at fun1 (C:\Users\ajeya\OneDrive\Downloads\Desktop\node\index.js:25:27)
        at func2 (C:\Users\ajeya\OneDrive\Downloads\Desktop\node\index.js:27:20)
        at Object.<anonymous> (C:\Users\ajeya\OneDrive\Downloads\Desktop\node\index.js:29:1)
        at Module._compile (node:internal/modules/cjs/loader:1469:14)
        at Module._extensions..js (node:internal/modules/cjs/loader:1548:10)
        at Module.load (node:internal/modules/cjs/loader:1288:32)
        at Module._load (node:internal/modules/cjs/loader:1104:12)
        at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:174:12)
        at node:internal/main/run_main_module:28:49

    
<|** YOU CAN CALCULATE TIME SPENT BY --------------YOUR FUNCTION ------------------(***)|>
       
        const sum = ()=>{
            console.log(`Addition... ${2} + ${3} == ${2+3}`);
        }
        const multiply =()=>{
            console.log(`Multiplication ${3*5}`);
        }
        const measureTime=()=>{
            console.time();
            sum();
            console.timeEnd();
            console.time();
            multiply();
            console.timeEnd();
        }
        measureTime();  
        OUPUT :
                Addition... 2 + 3 == 5
                default: 5.567ms
                Multiplication 15
                default: 0.137ms
<Creating the Progress Bar>
    const ProgressBar = require("progress");

    const bar = new ProgressBar('download aga varegu kaayo sisya [:bar] :rate/bps :percent :etas',{
        total : 50,
    });
    const timer = setInterval(()=>{
        bar.tick();
        if(bar.complete){
            clearInterval(timer);
            console.log("Dowload Completed");
        }
    },100)
    you create a new progress bar instance.
    The string 'downloading [:bar] :rate/bps :percent :etas' defines the format of the progress bar:
    [:bar]: The actual progress bar.
    :rate/bps: Shows the rate of progress (bytes per second).
    :percent: Displays the percentage complete.
    :etas: Displays the estimated time remaining.
    { total: 20 }: Sets the total number of steps or "ticks" the progress bar will go through.
    etas is expected time

    // ??--
    setInterval: This function runs the code inside it every 100 milliseconds (0.1 seconds).
    bar.tick(): This method moves the progress bar forward by 1 step each time it's called.
    bar.complete: This property checks if the progress bar has finished (all 20 ticks).
    clearInterval(timer): Stops the interval once the progress bar is complete.
    console.log('Download complete'): Prints a message when the progress is finished.

    How it Works:
    The progress bar starts at 0%.
    Every 100 milliseconds, the bar moves forward 1 step.
    Once 20 steps (ticks) are completed, the bar reaches 100%, and the interval stops.
    The message "Download complete" is printed at the end.
    This creates a simulated download progress in your terminal!

## here the code inside the index.js :
      const ProgressBar = require("progress");

      const bar = new ProgressBar('download aga varegu kaayo sisya [:bar] :rate/bps :percent :etas',{
          total : 50,
      });
      const timer = setInterval(()=>{
          bar.tick();
          if(bar.complete){
              clearInterval(timer);
              console.log("Dowload Completed");
          }
      },100)
      const chalk = require('chalk');
      console.log(chalk.blue("This IS BLUE"));
      

      // output :
      This IS BLUE(this line is printed in blue color)
      download aga varegu kaayo sisya [==================================================] 10/bps 100% 0.0s
      Dowload Completed


## standard input methodss.. :
      const readline = require("readline");

      const prompt = require('prompt-sync')();//ask chatgpt why is this ...

      const rl = readline.createInterface({
          input:process.stdin,
          output:process.stdout,
      });
      rl.question(`what is your name :`,(name)=>{
          console.log(`Hi ${name}`);
          rl.close();
      })
      const a = prompt("What's Your Name :");
      console.log(`Hi  ${a}`);

      //output-for-both cases :
      // What's Your Name :ajeya
      // Hi  ajeya 


<CHAPTER-02>--------------------(NODE.JS PACKAGE MANAGER (NPM))------------------>

1.  NPM is the standard package manager for the node.js 

2. As of sep,2022 it has around 2.1 million packages listed in NPM registry

3. NPM is a way of download and manage dependecies for both fronted and backend application using javascipt

4.  Yarn and pnpm are the alternative for npm cli

5. open npm.com in browser search for CLI commands (Learn of them for react projects)

list of CLI commands :

1.  npm init( it is to bootstrap the json file in the node)

2. npm install <package_name>[-g,--save-dev,--no-save,--save]
(--save-dev)--> it going to install package under the dev-dependencies(/)

3.npm install <package_name>@<version>

4. npm update (it going up date all dependencies that are listed in package.json file)

or npm update <package_name>

5. npm run <package_name>

6. npm list (list down's all dependencies)

7. npm view <package_name>version   (suppose you want view version of specific package)

8. npm uninstall <package_name>  (it is going to uninstall dependend packagess)

9. npm help (use this and learn ..)

10. npx create-react-app (npx is the node package runner it will run the executable's)

11. npm install package_name@oldversion  (to install old-versions of the package)

** package.json() is the manifest file which contains all information related to your project


## SYMENTIC VERSIONING :

EX  :  "express" : ^4.18.1 

X : the first digit is major version
Y : the second digit is minor version
Z : the third digit is patch version

see like this ....... 
1.  ^ 4.18.1 : means change the minor or patch version
2.  ~ 4.18.1 : means change only patch version

** note : learn destructuring in javascript(node) // by using chat-gpt

import and export module funtioss :

suppose in index.js file :

    console.log("Hello World");
    person = require("./second");
    console.log(person);
    or-->
    const {data}=require("./second); // here we are doing destructuring of the object..
    console.log(data)   
suppose in second.js file:
   
     bharath = {
      name :"bharath",
     favnum : 9,
     isgaandu:true,
     tech:"developer" 
    }
    module.exports=bharath; or exports.data = bharath (it sends the data in the object form..)

here in second.js file exporting bharath object then.. in index.js file recieving that by calling the function  require (you can google it and check what feautures of this fuction ) and it is stored in anothor variable,, we are printing that variable...


*** how to print or console.log the objects beutifully..

    console.log(JSON.stringify(obj_name,null,2)); // 2-> for how much space you want
    console.log(JSON.stringify(obj_name,null,2));
    index.js ->:
    const obj={
        name:"ajeya",
        age:18,
        skill:"node-sql"
    };
    console.log(JSON.stringify(obj,null,6));


<CHAPTER-03> --> ERROR HANDLING IN THE NODE.JS----------------------------------->

        const error = new Error("Something Went Wrong..");
        // console.log(error.stack);
        // console.log(error.message);
        class CustomError extends Error{
            constructor(message){
                super(message);
            }
        }
        const {Custom}=new CustomError;
        // throw new Error("Hello Im Error Obj");
        throw new CustomError("No Wait a min");



## handling error by try and catch....
        
        
        try{
            dot();
        }
        catch(e){
            console.log("Error banthu");
            console.log(e);
        }
        function dot(){
            // console.log("Hello Bro");
            const data = fetch("localhost:300/api");
            console.log(data);
        }



            // Uncaught Exception 
            function dosome(){
                const data = fetch("localhost:300/api");
            }
            process.on("uncaughtException",(err)=>{
                console.log("there is a erro bro :",err.message);
                process.exit(1);
            });
            dosome();

            // Exceptions with promises
            function dosome(){
                // const data = fetch ("localhost:300/api");
                return ("Hllo")
            }
            const promise = new Promise((resolve,reject)=>{
                if(true){
                    resolve(dosome());
                }
                else{
                    reject(dosome());
                }
            });
            promise.then((val)=>{
                console.log(val);
            }).catch((err)=>{
                console.log("erro banthu sisya");
                console.log(err);
            })
              

              // Exception Handling with Async Await...
                function dosome(){
                    // console.log("IM from do somthing Baby...");
                    const data = fetch("localhost:300/api")
                }
                const  something = async()=>{
                    try{
                        await dosome();
                    }
                    catch(e){
                        console.log("Error Occured");
                        throw new Error(e.message);
                    }
                }
                something();

##  Node  Path Modules ....:
    
    const path = require('path');
    const a = path.basename('C:\\temp\\myfile.html');
    console.log(a);
    console.log(__filename);

    // const path = require("path");
    // const filepath ="C:\Users\ajeya\OneDrive\Downloads\Desktop\node\file-txt\one.txt"
    // console.log(path.basename(filepath));
    // console.log(path.dirname(filepath));
    // console.log(path.extname(filepath));

    // console.log(__dirname);
    // console.log(__filename);

    // const patht = "sample.txt";
    // console.log(path.join(path.dirname(filepath),patht));


## about FS Module ( file system module ) :
    {  const fs = require('node:fs');

    // fs.readFile("file.txt","utf-8",(err,data)=>{
    //     console.log(err,data); 
    //})
 
    const a = fs.readFileSync("file.txt");
    console.log(a.toString());
    console.log("Fishing reading file");
    }


    const a = fs.readFileSync("file.txt");
    console.log(a.toString());
    console.log("Fishing reading file");

    fs.writeFile("file.txt","Namaskara Gaandu",()=>{
        console.log("Okay Written Job Done!");
    });
    const b = fs.writeFileSync("file.txt","im the source of all spiritual and material things in the world -- krishna");
    console.log(b);



## os module and its functionsss

first import module as : const os = require("os")  --> here we did'nt use ./ bcz it is build in module

console.log("Hello World");
const person = require("./second");
console.log(person);
console.log(exports,require,module,__filename,__dirname);

const os = require('os');
console.log(os.freemem());
console.log(os.homedir());
console.log(os.hostname());
console.log(os.platform());
console.log(os.machine());
console.log(os.release());
console.log(os.type());
var http = require('http');
http.createServer(function(req,res){
    res.write("Hello Client");
    res.end();    
}).listen(8080);

--------
## path module :




## ECMAScript modules  :

index.js  :
   
   import { simple } from "./next.js";
   simple();

   import { complex as simple } from "./next.js";
   simple();

   import  thesa  from "./next.js"; 
   thesa();

   import * as node from "./next.js"
   console.log(node.simple());

next.js :

  function simple (){
    console.log("We are Doing Import and Export Simply.. bye  ");
  }
  module.exports = simple;
  export function simple (){
    console.log("We are Doing Import and Export Simply By Different Method of inport and exporting..");
  }
  export default function complex (){
    console.log("We are Doing Import and Export Simply By Different Method of inport and exporting..");
  }

  export function simple(){
    console.log("Helo maga >=");
    return 35
}

## URL modules  :
  import url from "url"

  const myurl = new URL ('https://google.com');
  myurl.pathname="/vasanthnagar/mejestic/tumkur/sira/darmapura/aralikere";
  myurl.search="oorige-hogbeku"
  console.log(myurl);
  console.log(myurl.href);
  console.log(myurl.host);
  console.log(myurl.protocol);

## node.js is the Event Driven Architechture,,(you can fire an event ,, you can listen that event )


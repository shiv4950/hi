okAss 2 q1 strict soft mode

 const number_order = (x, y, z) => {

  if (y > x && z > y) {
  
    return "strict mode";
  } 
  else if (z >= y) { 
  
    return "soft mode";
  } 
  else {
  
    return "not increasing";
  }
};

console.log(number_order(10, 15, 31)); 

console.log(number_order(24, 22, 31));

console.log(number_order(22, 22, 31)); 

console.log(number_order(50, 21, 15)); 


ass 2 q2

const num = 5;

const isGreater = (value, target) => value > target;

console.log(${num} is greater than 3: ${isGreater(num, 3)});

console.log(${num} is less than 7: ${isGreater(num, 7)});  


ass 2 q3 browser

const isBrowser = () => !['undefined', 'undefined'].includes(typeof window, typeof document);

if (isBrowser()) {

  console.log("Running in a browser environment");
 
} else {
  
  console.log("Not running in a browser environment (likely Node.js)");
  
}

ass 2 q 4seed

function unfold(fn, seed) {

  const result = [];
  
  let val = [null, seed];

  while ((val = fn(val[1]))) {
  
    result.push(val[0]);
  }

  return result;
}


const f = n => (n > 50 ? false : [-n, n + 10]); 

const generatedArray = unfold(f, 10);

console.log(generatedArray);

q6 52 cards

function* generateDeck() {
  
  const suits = ["Hearts", "Diamonds", "Spades", "Clubs"];
  
  const ranks = ["A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"];

  for (const suit of suits) {
  
    for (const rank of ranks) {
    
      yield { suit, rank };
    }
  }
}

for (const card of generateDeck()) {

  console.log(card);
}

Q7snake case

function convertToCase(str, separator){  

  const regex = /([A-Z])(?=[^A-Z]*)/g;


  const words = str.match(regex) || [];


  const convertedWords = words.map(word => word.toLowerCase());

  const convertedString = convertedWords.join(separator);

  return convertedString;
}

const snakeCase = convertToCase("This is a String", "_");

console.log("Snake Case:", snakeCase); 

const kebabCase = convertToCase("This is a String", "-");

Q9 series of async operation

async function performOperationsSequentially(operations) {
  
  for (const operation of operations) {
   
    await operation();
  }

  console.log("All operations completed!");
}
 
 asynchronous operations (replace with your actual operations)

function asyncOperation1() {

  return new Promise((resolve) => {
  
    setTimeout(() => {
    
      console.log("Operation 1 completed!");
      
      resolve();
    
    }, 1000);
  
  });

}

function asyncOperation2() {

  return new Promise((resolve) => {
  
    setTimeout(() => {
    
      console.log("Operation 2 completed!");
      
      resolve();
   
    }, 2000);
  
  });

}

function asyncOperation3() {

  return new Promise((resolve) => {
  
    setTimeout(() => {
    
      console.log("Operation 3 completed!");
      
      resolve();
    
    }, 3000);
  
  });
}

 
performOperationsSequentially([asyncOperation1, asyncOperation2, asyncOperation3]);

console.log("Kebab Case:", kebabCase); 

Q10 left to right composition for asynch

const composeAsyncFunctions = (...fns) => async (arg) => {
 
  return fns.reduce(async (p, f) => f(await p), Promise.resolve(arg));
};

async function asyncAdd1(x) {
  
  return x + 1;
}

async function asyncMultiplyBy2(x) {
  
  await new Promise((resolve) => setTimeout(resolve, 1000));
  
  return x * 2;
}

async function asyncSquare(x) {
  return x * x;
}

const composedFunction = composeAsyncFunctions(asyncAdd1, asyncMultiplyBy2, asyncSquare);

composedFunction(5)

 .then((result) => console.log("Result:", result)) 
 
  .catch((error) => console.error(error));


Q11 convert an asynch func to return a promise

function asyncToPromise(fn) {

  return (...args) => {
  
    return new Promise((resolve, reject) => {
    
      fn(...args, (err, result) => {
      
	if (err) {
        
	  reject(err);
        
	} else {
        
	  resolve(result);
        
	}
      
      });
    
    });
  
  };

}

async function fetchData(url) {
 
  const response = await fetch(url);
  
  return response.json();
}

const fetchDataPromise = asyncToPromise(fetchData);

fetchDataPromise("https://api.example.com/data")
  
  .then((data) => console.log(data))
  
  .catch((error) => console.error(error));

Q12 arg is symbol

const isSymbol = (val) => typeof val === 'symbol';

console.log(isSymbol(Symbol('test'))); 

console.log(isSymbol('hello'));       

console.log(isSymbol(123));


Q14 callback prototpye.call

const iterate = (n, fn) => {
 
  let count = 0;
  
  while (count < n && fn() !== false) {
  
    count++;
 
  }

};

const logNumbers = () => {
 
  console.log(count); 
  
  count++; 
  
  return count <= 5;
};


let count = 0;

iterate(10, logNumbers); 


Q15 split mutiline string

const splitLines = (str) => str.split(/\r?\n/);

const multilineString = `Line 1

Line 2

Line 3`;

const lines = splitLines(multilineString);

console.log(lines); 


Q16 first arg last



function rearrangeArgs(fn) {
  
  let firstArg;

  return function(...args) {
    
    [firstArg, ...args] = args;
    
    return fn(...args, firstArg);
  };
}


function greet(message, name) {

  return ${message}, ${name}!;
}

const rearrangedGreet = rearrangeArgs(greet);

console.log(rearrangedGreet("Hello", "World")); 

Q17 bank acc

class BankAccount {

  constructor(accountNumber, balance = 0) {

    this.accountNumber = accountNumber;
    
    this.balance = balance;
  }

  deposit(amount) {
    
    if (amount > 0) {
    
      this.balance += amount;
      
      console.log(Deposited $${amount}. New balance: $${this.balance});
    
    } else {
    
      console.error("Deposit amount must be positive.");
    }
  }

  withdraw(amount) {
    
    if (amount > 0 && amount <= this.balance) {
    
      this.balance -= amount;
      
      console.log(Withdrew $${amount}. New balance: $${this.balance});
    
    } else {
    
      console.error("Withdrawal amount must be positive and cannot exceed current balance.");

        }
  }
}

const account1 = new BankAccount(123456, 100);

const account2 = new BankAccount(654321);

account1.deposit(50);

account2.deposit(200);

account1.withdraw(25);

account2.withdraw(150);


Q18 getPower()

javascript

const getPower = (decimalPlaces) => 10 ** decimalPlaces;

const capitalize = (word) => word[0].toUpperCase() + word.slice(1).toLowerCase();

const roundToDecimalPlace = (number, decimalPlaces = 2) => {

  const factor = 10 ** decimalPlaces;
  
  return Math.round(number * factor) / factor;
};

export { capitalize, roundToDecimalPlace };


Node. Js.... 

import { capitalize, roundToDecimalPlace } from './main.js';

const displayTotal = (amount, name = "Customer") => {

  const total = roundToDecimalPlace(amount); 
  
  const formattedTotal = Total for ${capitalize(name)}: $${total};
  
  console.log(formattedTotal);
};

export { displayTotal };


# ASS 1

 # Q1 regstration.......

<!DOCTYPE html>

<html lang="en">

	<head>
    
    <meta charset="UTF-8">
    
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <title>Q1</title>
    
    <style>
    
	body {
        
	    font-family: Arial, sans-serif;
            
	    margin: 0;
            
	    padding: 0;
        }
        
	header, footer {
        
	    background-color: #000000;
            
	    color: #eee5e5;
            
	    padding: 10px;
            
	    text-align: center;
        }
	
        nav {
        
	    background-color: #454040;
            
	    color: #ebe6e6;
            
	    padding: 10px;
            
	    text-align: center;
        }
	
        nav a {
        
	    color: #000000;
            
	    text-decoration: none;
            
	    margin: 0 10px;
        }
	
        form {
        
	    margin: 20px auto;
            
	    max-width: 400px;
            
	    padding: 20px;
            
	    border: 1px solid #ebe6e6;
            
	    border-radius: 5px;
        }
        
	label {
        
	    display: block;
            
	    margin-bottom: 10px;
            
	    font-weight: bold;
        }
	
        
	input[type="text"], input[type="email"] {
        
	    width: 100%;
            
	    padding: 8px;
            
	    margin-bottom: 10px;
            
	    border: 1px solid #ccc;
            
	    border-radius: 5px;
        }
	
        input[type="radio"] {
        
	    margin-right: 5px;
        }
        
	input[type="submit"] {
        
	    background-color: #333;
            
	    color: #fff;
            
	    padding: 10px 20px;
            
	    border: none;
            
	    border-radius: 5px;
            
	    cursor: pointer;
        }
	
        input[type="submit"]:hover {
        
	    background-color: #444;
        }
    
    </style>

</head>

<body>

	<header>
        
	<h1>Registration Form</h1>
    
    </header>
    
    <nav>
    
	<a href="#">Home</a>
        
	<a href="#">About</a>
        
	<a href="#">Contact</a>
    
    </nav>
    
    <form>
    
	<label for="fullname">Full Name:</label>
        
	<input type="text" id="fullname" name="fullname" required>


        <label for="email">Email:</label>

	<input type="email" id="email" name="email" required>

        <label for="gender">Gender:</label>
        
	<input type="radio" id="male" name="gender" value="male" required>
        
	<label for="male">Male</label>
        
	<input type="radio" id="female" name="gender" value="female" required>
        
	<label for="female">Female</label>
        
	<input type="radio" id="other" name="gender" value="other" required>
        
	<label for="other">Other</label>


        <input type="submit" value="Register">

    </form>
    
    <footer>
    
	<p>&copy; 2024 Registration Form. All rights reserved.</p>
    
    </footer>

</body>

</html>

# Q2 boot strap table


<!doctype html>

<html lang="en">

	<head>
    
    <meta charset="utf-8">
    
    <meta name="viewport" content="width=device-width, initial-scale=1">
    
    <title>Q2</title>
    
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
  
  </head>
  
  <body>

  <div class="container mt-5">
  
	  <h2>Table with Bootstrap</h2>
    
    <table class="table table-striped table-hover">
      
      <thead>
    
	<tr>
      
	  <th>First Name</th>
          
	  <th>Last Name</th>
          
	  <th>Mobile Number</th>
          
	  <th>Email ID</th>
        
	</tr>
      
      </thead>
      
      <tbody>
      
	<tr>
        
	  <td>John</td>
          
	  <td>Doe</td>
          
	  <td>1234567890</td>
          
	  <td>john@example.com</td>
        
	</tr>

<tr>
          <td>Jane</td>
   
	<td>Smith</td>
        
	  <td>9876543210</td>
          
	  <td>jane@example.com</td>
        
	</tr>
        
	<!-- Add more rows as needed -->
      
      </tbody>
    
    </table>
    
    <nav aria-label="Table Pagination">
    
      <ul class="pagination justify-content-end">
      
	<li class="page-item disabled">
        
	  <span class="page-link">Previous</span>
        
	</li>
        
	<li class="page-item active"><span class="page-link">1</span></li>
        
	<li class="page-item"><a class="page-link" href="Q1.html">2</a></li>
        
	<li class="page-item"><a class="page-link" href="#">3</a></li>
        
	<li class="page-item">
        
	  <a class="page-link" href="#">Next</a>
        
	</li>
      
      </ul>
    
    </nav>
  
  </div>
 
 <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
 
  <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
  
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

</body>

</html>

# Q3 bootstrap web layout... 3 block

<!DOCTYPE html>

<html lang="en">

	<head>
  
  <meta charset="UTF-8">
  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  
  <title>Q3</title>
  
  <link href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">

</head>

<body>

	<nav class="navbar navbar-expand-lg navbar-light bg-light">
    
    <a class="navbar-brand" href="#">Navbar</a>
    
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
  
      <span class="navbar-toggler-icon"></span>
    
    </button>

    
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
    
      <ul class="navbar-nav mr-auto">
      
	<li class="nav-item active">
        
	  <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
        
	</li>
        
	<li class="nav-item">
        
	  <a class="nav-link" href="#">Link</a>
        
	</li>
        
	<li class="nav-item">
        
	  <a class="nav-link" href="#">Another link</a>
        
	</li>
      
      </ul>
    
    </div>
  
  </nav>

  <div class="container">
  
	  <div class="row">  
      
      <div class="col-sm">
      
	<div class="bg-success text-white text-center p-3 ">
        
	  Column 1
        
	</div>
      
      </div>
      
      <div class="col-sm">
      
	<div class="bg-secondary text-white text-center p-3">
        
	  Column 2
        
	</div>
      
      </div>
      
      <div class="col-sm">
      
	<div class="bg-info text-white text-center p-3">
        
	  Column 3
        
	</div>
      
      </div>
    
    </div>
  
  </div>

  <footer class="footer mt-auto py-3 bg-light">
  
	  <div class="container">
      
      <span class="text-muted">Footer content here.</span>
    
    </div>
  
  </footer>

  <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
  
  <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
  
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

</body>

</html>

# Q4 dropdown menu

<html>
	
    
    <head>
    
	<title>que 4</title>
        
	<meta charset="utf-8">

    <meta name="viewport" content="width=device-width, initial-scale=1">
    
    <title>Bootstrap demo</title>
    
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet"
    
     integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
    
    </head>
    
    <body>
    
	<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js" 
        
	integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL" crossorigin="anonymous"></script>
    
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.8/dist/umd/popper.min.js" 
    integrity="sha384-I7E8VVD/ismYTF4hNIPjVp/Zjvgyol6VFvRkX/vR+Vc4jQkC+hVqc2pM8ODewa9r" crossorigin="anonymous"></script>
    
    <div class="sidebar">
    
	<h4>Menu</h4>
        
	<ul class="nav flex-column">
        
	  <li class="nav-item">
          
	    <a class="nav-link" href="#">Home</a>
          
	  </li>
          
	  <li class="nav-item dropdown">
          
	    <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            
	      Dropdown
            
	    </a>
            
	    <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            
	      <li><a class="dropdown-item" href="#">Action</a></li>
              
	      <li><a class="dropdown-item" href="#">Another action</a></li>
              
	      <li><hr class="dropdown-divider"></li>
              
	      <li><a class="dropdown-item" href="#">Separated link</a></li>
            
	    </ul>
          
	  </li>
        
	</ul>
      
      </div>

</div>

<form class="d-flex">

	<input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
  
  <button class="btn btn-outline-success" type="submit">Search</button>

</form>

</body>

</div>

</html>

# Q5 add thumbnail 9 blocks

<!doctype html>

<html lang="en">
 
	<head>
    
    
    <!-- Required meta tags -->
    
    <meta charset="utf-8">
    
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    
    <title>Q5</title>
  
  </head>
  
  <body>
  
	  <div class="container mt-5">
        
	<table class="table m-2">
        
	    <thead>
              
            </thead>
            
	    <tbody>

                <tr>
            
		    <td class="col-md bg-primary w-25% ">block 1</td>
                    
		    <td colspan="2" class=" bg-info w-60">block 2</td>
                                        
                  </tr>

              <tr>
                
		<td rowspan="2" class="col bg-info ">block 3</td>
                
		<td rowspan="3" class="col bg-primary ">block 6</td>
                
		<td scope="col" class="bg-info ">block 7</td> 
              
	      </tr>

              <tr> 
              
		<td class="col-sm bg-primary ">block 8</td>
              
	      </tr>
              
              <tr>
              
		<td class="new col-xs bg-primary w-50">block 4</td>
                
		<td class="new col-xs bg-info w-50 ">block 5</td>
                
		<td class="col bg-primary">block 9</td>
              
	      </tr>
              
	      <style>
              
		.new{
                
		    display: inline-flex;
                }

                /* tr{
                
		    margin-bottom: 5px;
                
		} */
                
              </style>
            
	    </tbody>
          
	  </table>
    
    </div>

    <!-- Optional JavaScript; choose one of the two! -->

    <!-- Option 1: Bootstrap Bundle with Popper -->
    
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>

    <!-- Option 2: Separate Popper and Bootstrap JS -->
    <!--
    
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js" integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
    
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js" integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF" crossorigin="anonymous"></script>
   -->
  
  </body>

</html>

# ass 3 ts

Q1 variable name variable age.......

const printDetails = () => {

  let name: string = "Alice";
  
  let age: number = 30;

  console.log(`Name: ${name}`);
  
  console.log(`Age: ${age}`);
  
};

printDetails();



Q2 declare var using let const var....

....



const demonstrateScoping = () => {
  
  var message = "This is a var message";

  if (true) {
    
    
    let blockMessage = "This is a let message";
    
    console.log("Inside if:", message, blockMessage); 
  }

  console.log("Outside if:", message); 

  
  const PI = 3.14;
  
  console.log("PI value:", PI);
};

demonstrateScoping();


Q3 convers a variable to ons parseint.....



const convertTypes = () => {
  
  let strNum: string = "123";

  
  let numberFromParse: number = parseInt(strNum, 10);

  toString()
  
  let stringFromNumber: string = numberFromParse.toString();

  console.log("Original string:", strNum);
  
  console.log("Number from string:", numberFromParse);
  
  console.log("String from number:", stringFromNumber);
  
};

convertTypes();


Q4 color values red green .......

const defineColor = () => {
  
  enum Color {
    Red = "Red",
    
    Green = "Green",
    
    White = "White",
    
    Blue = "Blue",
    
  }

  
  let selectedColor: Color = Color.Green; 

  console.log("Selected Color:", selectedColor);
};

defineColor();


Q5 accepts two arguments array of type two indices.......



const swapElements = <T>(arr: T[], index1: number, index2: number): T[] => {
  
  if (index1 < 0 || index1 >= arr.length || index2 < 0 || index2 >= arr.length) {
    throw new Error("Invalid indices for swapping");
  }

  
  [arr[index1], arr[index2]] = [arr[index2], arr[index1]];

  
  return arr;
};


let numbers: number[] = [1, 2, 3, 4];

let swappedNumbers = swapElements(numbers, 0, 2);

console.log("Original array:", numbers);

console.log("Swapped array:", swappedNumbers);


Q6 class bus.......



class Bus {
  
  public make: string;
  
  public model: string;
  
  public year: number;

  
  constructor(make: string, model: string, year: number) {
  
    this.make = make;
    
    this.model = model;
    
    this.year = year;
  }
}


let myBus = new Bus("Ford", "E-Series", 2023);

console.log("Bus Details:");

console.log(`Make: ${myBus.make}`);

console.log(`Model: ${myBus.model}`);

console.log(`Year: ${myBus.year}`);


Q7 car with properties.......


class Engine {

  public horsepower: number;
  
  public fuelType: string;

  constructor(horsepower: number, fuelType: string) {
  
    this.horsepower = horsepower;
    
    this.fuelType = fuelType;
  }
}


class Car {

  public make: string;
  
  public model: string;
  
  public year: number;
  
  public engine: Engine;

  constructor(make: string, model: string, year: number, engine: Engine) {
  
    this.make = make;
    
    this.model = model;
    
    this.year = year;
    
    this.engine = engine;
    
  }

  public start() {
    console.log("Car starting...");
  }

  public printCarDetails() {
  
    console.log("Car Details:");
    
    console.log(`Make: ${this.make}`);
    
    console.log(`Model: ${this.model}`);
    
    console.log(`Year: ${this.year}`);
    
    console.log("Engine Details:");
    
    console.log(`Horsepower: 
    
    ${this.engine.horsepower}`);
    
    console.log(`Fuel Type: 
    
    ${this.engine.fuelType}`);
  }
}


let electricEngine = new Engine(200, "Electric");

let electricCar = new Car("Tesla", "Model S", 2024, electricEngine);

electricCar.start();

electricCar.printCarDetails();


Q8 student with properties.........


Fist file. Ts

export const add = (x: number, y: number): number => {

  return x + y;
  
};

export const subtract = (x: number, y: number): number => {

  return x - y;
  
};

export const PI = 3.14159;

Main. Ts

import { add, subtract, PI } from "./mathUtils"; 

console.log("Sum:", add(5, 3));

console.log("Difference:", subtract(10, 2));

console.log("Value of PI:", PI);


Q9 multiple functions and variable naned exports ......



Fist. Ts

export const add = (x: number, y: number): number => {
  return x + y;
  
};

export const subtract = (x: number, y: number): number => {

  return x - y;
  
};

export const multiply = (x: number, y: number): number => {

  return x * y; // Added multiplication function
  
};

export const PI = 3.14159;

Main. Ts


import { add, subtract, multiply, PI } 

console.log("Sum:", add(5, 3));

console.log("Difference:", subtract(10, 2));

console.log("Product:", multiply(4, 6)); 

console.log("Value of PI:", PI);



14. Write a function print ShapeInfo(shape:Circle | Rectangle) that prints the area of the shape. Use type narrowing to determine whether the shape is a Circle of Rectangle. Use type guards to safely access the properties specific to each shape type. (take user input)


Q14
interface Shape {

  getArea(): number;
}

class Circle implements Shape {

  constructor(public radius: number) {}

  getArea(): number {
  
    return Math.PI * 
    
    Math.pow(this.radius, 2);
    
 }
}
class Rectangle implements Shape {

  constructor(public width: number, public height: number) {}

  getArea(): number {
  
    return this.width * this.height;
  }
}
const printShapeInfo = (shape: Shape): void => {

  let area: number;
  
 if (shape instanceof Circle) {
 
    area = shape.getArea();
    
    console.log("Circle Area:", area);
    
  } else if (shape instanceof Rectangle) {
  
    area = shape.getArea();
    
    console.log("Rectangle Area:", area);
    
  } else {
  
    console.error("Unsupported shape type");
    
  }
};
 conversion (consider error handling)
 
let userInput = prompt("Enter shape type (circle or rectangle):").toLowerCase();
let shape: Shape;

if (userInput === "circle") {

  let radius = Number(prompt("Enter circle radius:"));
  
  shape = new Circle(radius);
  
} else if (userInput === "rectangle") {
  let width = Number(promptly ("Enter rectangle width:"));
  
  let height = Number(prompt("Enter rectangle height:"));
  
  shape = new Rectangle(width, height);
} else {

  console.error("Invalid shape type. Please enter 'circle' or 'rectangle'.");
}

printShapeInfo(shape);









Ass 2 q1 strict soft mode

 const number_order = (x, y, z) => {

  if (y > x && z > y) {
  
    return "strict mode";
  } 
  else if (z >= y) { // Soft mode: z is greater than or equal to y
  
    return "soft mode";
  } 
  else {
  
    return "not increasing";
  }
};

console.log(number_order(10, 15, 31)); // Output: strict mode

console.log(number_order(24, 22, 31)); // Output: soft mode

console.log(number_order(22, 22, 31)); // Output: soft mode

console.log(number_order(50, 21, 15)); // Output: not increasing


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

function isSymbol(val) {

  return typeof val === 'symbol';
}

console.log(isSymbol(Symbol('test'))); 

console.log(isSymbol('hello')); 

console.log(isSymbol(10)); 

console.log(isSymbol(Object(Symbol('test')))); 

Q13 page using css



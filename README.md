Ass 2 q1 strict soft mode

function number_order(x, y, z ) {

  if ( y > x && z > y) 
  {
  
    return "strict mode";    
  }
  
  else if(z > y) 
  
   return "Soft mode";
  
  else
  
    return "Undefinded";
}

console.log(number_order(10,15,31));

console.log(number_order(24,22,31));

console.log(number_order(50,21,15));

q2 greater than less than

const a = 5;

const b = 10;


const result = ${() => a < b ? 'a is less than b: true' : 'a is less than b: false'};

console.log(result()); // Output: "a is less than b: true"

q3 is a browser or not

<!DOCTYPE html> 

<html> 

	<body> 
	
 <h1>Hello Geeks</h1> 

 <script> 

	 function isBrowser() { 
	
		 if (typeof process === "object" && 
		
		     typeof require === "function") { 
			
			 return false; 
			}
		 
			if (typeof importScripts === "function") { 
		
				return false; 
			}  
			
		 if (typeof window === "object") { 
		
			 return true; 
			} 
		} 
		
	 if (isBrowser()) { 
	
		 alert("The Environment is Browser....") 
		} 
	
 </script> 

</body> 

</html>

Q4 initial seed valuee

const unfold = (fn, seed) => {

  let result = [];
  
  let val = [null, seed];
  
  while ((val = fn(val[1]))) {    result.push(val[0]);
  }
    return result;
};
const f = n => (n > 50 ? false : [-n, n + 10]);

console.log(unfold(f, 10)); 

q6 52 cards

function* generateDeck() {
  const suits = ['♠️', '♥️', '♦️', '♣️'];
  const values = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K', 'A'];

  for (const suit of suits) {

    for (const value of values) {
    
      yield ${value}${suit};
    }
  }
}

const deck = generateDeck();

for (const card of deck) {
  
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

console.log("Kebab Case:", kebabCase); 

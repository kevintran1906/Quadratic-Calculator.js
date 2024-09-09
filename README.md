# Quadratic-Calculator.js
let a;
let b;
let c;
let d;

let root1;
let root2;

let sum;
let product;
let midpoint; // The average of the roots
let diff;     // The distance from the roots to the average

let z1;
let z2;

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(255, 255, 255);

  // Take inputs from the user
  a = prompt("Enter coefficient a:");
  b = prompt("Enter coefficient b:");
  c = prompt("Enter coefficient c:");

  // Calculate Discriminant
  d = Math.sqrt(b * b - 4 * a * c);

  // Calculate roots using both methods
  quadratic(a, b, c, d);
  PoShenLoh(a, b, c);

  // Compare results
  compare();
}

function quadratic(a, b, c, d) {
  print('Quadratic Formula: ');
  if (d > 0) { // Check if discriminant is bigger than 0 then there are two real roots
    root1 = (-b + d) / (2 * a);
    root2 = (-b - d) / (2 * a);
    print('The roots are ' + root1.toFixed(2) + ' and ' + root2.toFixed(2));
    print('a is ' + a + ', b is ' + b + ', c is ' + c);
  } 
	else if (d == 0) { // Check if discriminant is equal to 0 then there is only one real root
    root1 = root2 = -b / (2 * a);
    print('The root is ' + root1.toFixed(2));
    print('a is ' + a + ', b is ' + b + ', c is ' + c);
  } 
	else { // Otherwise there is no real roots.
    print('There are no real roots.');
    print('a is ' + a + ', b is ' + b + ', c is ' + c);
  }
}


function PoShenLoh(a, b, c) {
	
	print('‎'); //Spacing in console log. Nothing important :)
  print('Po Shen Loh Method: ');

  sum = -b / a; // Sum of the roots
  product = c / a; // Product of the roots
  midpoint = sum / 2; // Average of the roots

 	// Display average of the roots
  print('Average of the roots = ' + midpoint.toFixed(2));

  // Calculate the distance from the roots to average 
  let squareRootValue = midpoint * midpoint - product;
  
  if (squareRootValue >= 0) {
    diff = Math.sqrt(squareRootValue); // Distance from roots to average
    z1 = midpoint + diff; // First root
    z2 = midpoint - diff; // Second root
    
    // Show distance from the roots to the average
    print('Distance from the roots to the average = ' + diff.toFixed(2));
    
		if (z1 === z2) {
		print('The root is ' + z1.toFixed(2)) // Only print one root if both roots are equal 
		} else {
    print('The roots are ' + z1.toFixed(2) + ' and ' + z2.toFixed(2)); // Print both roots if they are different
		}
    print('a is ' + a + ', b is ' + b + ', c is ' + c);
			
	} else {
    // No real roots
    print('There are no real roots.');
    print('a is ' + a + ', b is ' + b + ', c is ' + c);
  }
}

function compare() {
	print('‎') //Spacing again :) It doesn't effect the program
  if ((root1 == z1 || root1 == z2) && (root2 == z1 || root2 == z2)) {
    print('The roots match between the two methods.');
	}	else {
	print('The roots do not match.');
	}
}


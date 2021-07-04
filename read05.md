# Read: 05 - Operators and Loops

 ## Expressions and operators
« Previous
Next »
This chapter describes JavaScript's expressions and operators, including assignment, comparison, arithmetic, bitwise, logical, string, ternary and more.

A complete and detailed list of operators and expressions is also available in the reference.

Operators
JavaScript has the following types of operators. This section describes the operators and contains information about operator precedence.

Assignment operators
Comparison operators
Arithmetic operators
Bitwise operators
Logical operators
String operators
Conditional (ternary) operator
Comma operator
Unary operators
Relational operators
JavaScript has both binary and unary operators, and one special ternary operator, the conditional operator. A binary operator requires two operands, one before the operator and one after the operator:

operand1 operator operand2
Copy to Clipboard
For example, 3+4 or x*y.

A unary operator requires a single operand, either before or after the operator:

operator operand
Copy to Clipboard
or

operand operator
Copy to Clipboard
For example, x++ or ++x.

Assignment operators
An assignment operator assigns a value to its left operand based on the value of its right operand. The simple assignment operator is equal (=), which assigns the value of its right operand to its left operand. That is, x = y assigns the value of y to x.

There are also compound assignment operators that are shorthand for the operations listed in the following table:

Compound assignment operators
Name	Shorthand operator	Meaning
Assignment	x = y	x = y
Addition assignment	x += y	x = x + y
Subtraction assignment	x -= y	x = x - y
Multiplication assignment	x *= y	x = x * y
Division assignment	x /= y	x = x / y
Remainder assignment	x %= y	x = x % y
Exponentiation assignment	x **= y	x = x ** y
Left shift assignment	x <<= y	x = x << y
Right shift assignment	x >>= y	x = x >> y
Unsigned right shift assignment	x >>>= y	x = x >>> y
Bitwise AND assignment	x &= y	x = x & y
Bitwise XOR assignment	x ^= y	x = x ^ y
Bitwise OR assignment	x |= y	x = x | y
Logical AND assignment	x &&= y	x && (x = y)
Logical OR assignment	x ||= y	x || (x = y)
Logical nullish assignment	x ??= y	x ?? (x = y)
Return value and chaining
Like most expressions, assignments like x = y have a return value. It can be retrieved by e.g. assigning the expression or logging it:

const z = (x = y); // Or equivalently: const z = x = y;

console.log(z); // Log the return value of the assignment x = y.
console.log(x = y); // Or log the return value directly.
The return value matches the expression to the right of the = sign in the “Meaning” column of the table above. That means that (x = y) returns y, (x += y) returns the resulting sum x + y, (x **= y) returns the resulting power x ** y, and so on.

In the case of logical assignments, (x &&= y), (x ||= y), and (x ??= y), the return value is that of the logical operation without the assignment, so x && y, x || y, and x ?? y, respectively.

Note that the return values are always based on the operands’ values before the operation.

When chaining these expressions, each assignment is evaluated right-to-left. Consider these examples:

w = z = x = y is equivalent to w = (z = (x = y)) or x = y; z = y; w = y
z += x *= y is equivalent to z += (x *= y) or tmp = x * y; x *= y; z += tmp (except without the tmp).
Destructuring
For more complex assignments, the destructuring assignment syntax is a JavaScript expression that makes it possible to extract data from arrays or objects using a syntax that mirrors the construction of array and object literals.

var foo = ['one', 'two', 'three'];

// without destructuring
var one   = foo[0];
var two   = foo[1];
var three = foo[2];

// with destructuring
var [one, two, three] = foo;
Copy to Clipboard
Comparison operators
A comparison operator compares its operands and returns a logical value based on whether the comparison is true. The operands can be numerical, string, logical, or object values. Strings are compared based on standard lexicographical ordering, using Unicode values. In most cases, if the two operands are not of the same type, JavaScript attempts to convert them to an appropriate type for the comparison. This behavior generally results in comparing the operands numerically. The sole exceptions to type conversion within comparisons involve the === and !== operators, which perform strict equality and inequality comparisons. These operators do not attempt to convert the operands to compatible types before checking equality. The following table describes the comparison operators in terms of this sample code:

var var1 = 3;
var var2 = 4;
Copy to Clipboard
Comparison operators
Operator	Description	Examples returning true
Equal (==)	Returns true if the operands are equal.	3 == var1
"3" == var1

3 == '3'
Not equal (!=)	Returns true if the operands are not equal.	var1 != 4
var2 != "3"
Strict equal (===)	Returns true if the operands are equal and of the same type. See also Object.is and sameness in JS.	3 === var1
Strict not equal (!==)	Returns true if the operands are of the same type but not equal, or are of different type.	var1 !== "3"
3 !== '3'
Greater than (>)	Returns true if the left operand is greater than the right operand.	var2 > var1
"12" > 2
Greater than or equal (>=)	Returns true if the left operand is greater than or equal to the right operand.	var2 >= var1
var1 >= 3
Less than (<)	Returns true if the left operand is less than the right operand.	var1 < var2
"2" < 12
Less than or equal (<=)	Returns true if the left operand is less than or equal to the right operand.	var1 <= var2
var2 <= 5
Note: => is not an operator, but the notation for Arrow functions.

Arithmetic operators
An arithmetic operator takes numerical values (either literals or variables) as their operands and returns a single numerical value. The standard arithmetic operators are addition (+), subtraction (-), multiplication (*), and division (/). These operators work as they do in most other programming languages when used with floating point numbers (in particular, note that division by zero produces Infinity). For example:

1 / 2; // 0.5
1 / 2 == 1.0 / 2.0; // this is true
Copy to Clipboard
In addition to the standard arithmetic operations (+, -, *, /), JavaScript provides the arithmetic operators listed in the following table:

Arithmetic operators
Operator	Description	Example
Remainder (%)	Binary operator. Returns the integer remainder of dividing the two operands.	12 % 5 returns 2.
Increment (++)	Unary operator. Adds one to its operand. If used as a prefix operator (++x), returns the value of its operand after adding one; if used as a postfix operator (x++), returns the value of its operand before adding one.	If x is 3, then ++x sets x to 4 and returns 4, whereas x++ returns 3 and, only then, sets x to 4.
Decrement (--)	Unary operator. Subtracts one from its operand. The return value is analogous to that for the increment operator.	If x is 3, then --x sets x to 2 and returns 2, whereas x-- returns 3 and, only then, sets x to 2.
Unary negation (-)	Unary operator. Returns the negation of its operand.	If x is 3, then -x returns -3.
Unary plus (+)	Unary operator. Attempts to convert the operand to a number, if it is not already.	
+"3" returns 3.

+true returns 1.

Exponentiation operator (**)	Calculates the base to the exponent power, that is, base^exponent	2 ** 3 returns 8.
10 ** -1 returns 0.1.
Bitwise operators
A bitwise operator treats their operands as a set of 32 bits (zeros and ones), rather than as decimal, hexadecimal, or octal numbers. For example, the decimal number nine has a binary representation of 1001. Bitwise operators perform their operations on such binary representations, but they return standard JavaScript numerical values.

The following table summarizes JavaScript's bitwise operators.

Bitwise operators
Operator	Usage	Description
Bitwise AND	a & b	Returns a one in each bit position for which the corresponding bits of both operands are ones.
Bitwise OR	a | b	Returns a zero in each bit position for which the corresponding bits of both operands are zeros.
Bitwise XOR	a ^ b	Returns a zero in each bit position for which the corresponding bits are the same.
[Returns a one in each bit position for which the corresponding bits are different.]
Bitwise NOT	~ a	Inverts the bits of its operand.
Left shift	a << b	Shifts a in binary representation b bits to the left, shifting in zeros from the right.
Sign-propagating right shift	a >> b	Shifts a in binary representation b bits to the right, discarding bits shifted off.
Zero-fill right shift	a >>> b	Shifts a in binary representation b bits to the right, discarding bits shifted off, and shifting in zeros from the left.
Bitwise logical operators
Conceptually, the bitwise logical operators work as follows:

The operands are converted to thirty-two-bit integers and expressed by a series of bits (zeros and ones). Numbers with more than 32 bits get their most significant bits discarded. For example, the following integer with more than 32 bits will be converted to a 32 bit integer:
Before: 1110 0110 1111 1010 0000 0000 0000 0110 0000 0000 0001
After:               1010 0000 0000 0000 0110 0000 0000 0001
Each bit in the first operand is paired with the corresponding bit in the second operand: first bit to first bit, second bit to second bit, and so on.
The operator is applied to each pair of bits, and the result is constructed bitwise.
For example, the binary representation of nine is 1001, and the binary representation of fifteen is 1111. So, when the bitwise operators are applied to these values, the results are as follows:

Bitwise operator examples
Expression	Result	Binary Description
15 & 9	9	1111 & 1001 = 1001
15 | 9	15	1111 | 1001 = 1111
15 ^ 9	6	1111 ^ 1001 = 0110
~15	-16	~ 0000 0000 ... 0000 1111 = 1111 1111 ... 1111 0000
~9	-10	~ 0000 0000 ... 0000 1001 = 1111 1111 ... 1111 0110
Note that all 32 bits are inverted using the Bitwise NOT operator, and that values with the most significant (left-most) bit set to 1 represent negative numbers (two's-complement representation). ~x evaluates to the same value that -x - 1 evaluates to.

Bitwise shift operators
The bitwise shift operators take two operands: the first is a quantity to be shifted, and the second specifies the number of bit positions by which the first operand is to be shifted. The direction of the shift operation is controlled by the operator used.

Shift operators convert their operands to thirty-two-bit integers and return a result of either type Number or BigInt: specifically, if the type of the left operand is BigInt, they return BigInt; otherwise, they return Number.

The shift operators are listed in the following table.

Bitwise shift operators
Operator	Description	Example
Left shift
(<<)	This operator shifts the first operand the specified number of bits to the left. Excess bits shifted off to the left are discarded. Zero bits are shifted in from the right.	9<<2 yields 36, because 1001 shifted 2 bits to the left becomes 100100, which is 36.
Sign-propagating right shift (>>)	This operator shifts the first operand the specified number of bits to the right. Excess bits shifted off to the right are discarded. Copies of the leftmost bit are shifted in from the left.	9>>2 yields 2, because 1001 shifted 2 bits to the right becomes 10, which is 2. Likewise, -9>>2 yields -3, because the sign is preserved.
Zero-fill right shift (>>>)	This operator shifts the first operand the specified number of bits to the right. Excess bits shifted off to the right are discarded. Zero bits are shifted in from the left.	19>>>2 yields 4, because 10011 shifted 2 bits to the right becomes 100, which is 4. For non-negative numbers, zero-fill right shift and sign-propagating right shift yield the same result.
Logical operators
Logical operators are typically used with Boolean (logical) values; when they are, they return a Boolean value. However, the && and || operators actually return the value of one of the specified operands, so if these operators are used with non-Boolean values, they may return a non-Boolean value. The logical operators are described in the following table.

Logical operators
Operator	Usage	Description
Logical AND (&&)	expr1 && expr2	Returns expr1 if it can be converted to false; otherwise, returns expr2. Thus, when used with Boolean values, && returns true if both operands are true; otherwise, returns false.
Logical OR (||)	expr1 || expr2	Returns expr1 if it can be converted to true; otherwise, returns expr2. Thus, when used with Boolean values, || returns true if either operand is true; if both are false, returns false.
Logical NOT (!)	!expr	Returns false if its single operand that can be converted to true; otherwise, returns true.
Examples of expressions that can be converted to false are those that evaluate to null, 0, NaN, the empty string (""), or undefined.

The following code shows examples of the && (logical AND) operator.

var a1 =  true && true;     // t && t returns true
var a2 =  true && false;    // t && f returns false
var a3 = false && true;     // f && t returns false
var a4 = false && (3 == 4); // f && f returns false
var a5 = 'Cat' && 'Dog';    // t && t returns Dog
var a6 = false && 'Cat';    // f && t returns false
var a7 = 'Cat' && false;    // t && f returns false
Copy to Clipboard
The following code shows examples of the || (logical OR) operator.

var o1 =  true || true;     // t || t returns true
var o2 = false || true;     // f || t returns true
var o3 =  true || false;    // t || f returns true
var o4 = false || (3 == 4); // f || f returns false
var o5 = 'Cat' || 'Dog';    // t || t returns Cat
var o6 = false || 'Cat';    // f || t returns Cat
var o7 = 'Cat' || false;    // t || f returns Cat
Copy to Clipboard
The following code shows examples of the ! (logical NOT) operator.

var n1 = !true;  // !t returns false
var n2 = !false; // !f returns true
var n3 = !'Cat'; // !t returns false
Copy to Clipboard
Short-circuit evaluation
As logical expressions are evaluated left to right, they are tested for possible "short-circuit" evaluation using the following rules:

false && anything is short-circuit evaluated to false.
true || anything is short-circuit evaluated to true.
The rules of logic guarantee that these evaluations are always correct. Note that the anything part of the above expressions is not evaluated, so any side effects of doing so do not take effect.

Note that for the second case, in modern code you can use the new Nullish coalescing operator (??) that works like ||, but it only returns the second expression, when the first one is "nullish", i.e. null or undefined. It is thus the better alternative to provide defaults, when values like '' or 0 are valid values for the first expression, too.

String operators
In addition to the comparison operators, which can be used on string values, the concatenation operator (+) concatenates two string values together, returning another string that is the union of the two operand strings.

For example,

console.log('my ' + 'string'); // console logs the string "my string".
Copy to Clipboard
The shorthand assignment operator += can also be used to concatenate strings.

For example,

var mystring = 'alpha';
mystring += 'bet'; // evaluates to "alphabet" and assigns this value to mystring.
Copy to Clipboard
Conditional (ternary) operator
The conditional operator is the only JavaScript operator that takes three operands. The operator can have one of two values based on a condition. The syntax is:

condition ? val1 : val2
Copy to Clipboard
If condition is true, the operator has the value of val1. Otherwise it has the value of val2. You can use the conditional operator anywhere you would use a standard operator.

For example,

var status = (age >= 18) ? 'adult' : 'minor';
Copy to Clipboard
This statement assigns the value "adult" to the variable status if age is eighteen or more. Otherwise, it assigns the value "minor" to status.

Comma operator
The comma operator (,) evaluates both of its operands and returns the value of the last operand. This operator is primarily used inside a for loop, to allow multiple variables to be updated each time through the loop. It is regarded bad style to use it elsewhere, when it is not necessary. Often two separate statements can and should be used instead.

For example, if a is a 2-dimensional array with 10 elements on a side, the following code uses the comma operator to update two variables at once. The code prints the values of the diagonal elements in the array:

var x = [0,1,2,3,4,5,6,7,8,9]
var a = [x, x, x, x, x];

for (var i = 0, j = 9; i <= j; i++, j--)
//                                ^
  console.log('a[' + i + '][' + j + ']= ' + a[i][j]);
Copy to Clipboard
Unary operators
A unary operation is an operation with only one operand.

delete
The delete operator deletes an object's property. The syntax is:

delete object.property;
delete object[propertyKey];
delete objectName[index];
delete property; // legal only within a with statement
Copy to Clipboard
where object is the name of an object, property is an existing property, and propertyKey is a string or symbol referring to an existing property.

The fourth form is legal only within a with statement, to delete a property from an object, and also for properties of the global object.

If the delete operator succeeds, it removes the property from the object. Trying to access it afterwards will yield undefined. The delete operator returns true if the operation is possible; it returns false if the operation is not possible.

x = 42; // implicitly creates window.x
var y = 43;
var myobj = {h: 4}; // create object with property h

delete x;       // returns false (cannot delete if created implicitly)
delete y;       // returns false (cannot delete if declared with var)
delete Math.PI; // returns false (cannot delete non-configurable properties)
delete myobj.h; // returns true (can delete user-defined properties)
Copy to Clipboard
Deleting array elements
Since arrays are just objects, it's technically possible to delete elements from them. This is however regarded as a bad practice, try to avoid it. When you delete an array property, the array length is not affected and other elements are not re-indexed. To achieve that behavior, it is much better to just overwrite the element with the value undefined. To actually manipulate the array, use the various array methods such as splice.

typeof
The typeof operator is used in either of the following ways:

typeof operand
typeof (operand)
Copy to Clipboard
The typeof operator returns a string indicating the type of the unevaluated operand. operand is the string, variable, keyword, or object for which the type is to be returned. The parentheses are optional.

Suppose you define the following variables:

var myFun = new Function('5 + 2');
var shape = 'round';
var size = 1;
var foo = ['Apple', 'Mango', 'Orange'];
var today = new Date();
Copy to Clipboard
The typeof operator returns the following results for these variables:

typeof myFun;       // returns "function"
typeof shape;       // returns "string"
typeof size;        // returns "number"
typeof foo;         // returns "object"
typeof today;       // returns "object"
typeof doesntExist; // returns "undefined"
Copy to Clipboard
For the keywords true and null, the typeof operator returns the following results:

typeof true; // returns "boolean"
typeof null; // returns "object"
Copy to Clipboard
For a number or string, the typeof operator returns the following results:

typeof 62;            // returns "number"
typeof 'Hello world'; // returns "string"
Copy to Clipboard
For property values, the typeof operator returns the type of value the property contains:

typeof document.lastModified; // returns "string"
typeof window.length;         // returns "number"
typeof Math.LN2;              // returns "number"
Copy to Clipboard
For methods and functions, the typeof operator returns results as follows:

typeof blur;        // returns "function"
typeof eval;        // returns "function"
typeof parseInt;    // returns "function"
typeof shape.split; // returns "function"
Copy to Clipboard
For predefined objects, the typeof operator returns results as follows:

typeof Date;     // returns "function"
typeof Function; // returns "function"
typeof Math;     // returns "object"
typeof Option;   // returns "function"
typeof String;   // returns "function"
Copy to Clipboard
void
The void operator is used in either of the following ways:

void (expression)
void expression
Copy to Clipboard
The void operator specifies an expression to be evaluated without returning a value. expression is a JavaScript expression to evaluate. The parentheses surrounding the expression are optional, but it is good style to use them.

Relational operators
A relational operator compares its operands and returns a Boolean value based on whether the comparison is true.

in
The in operator returns true if the specified property is in the specified object. The syntax is:

propNameOrNumber in objectName
Copy to Clipboard
where propNameOrNumber is a string, numeric, or symbol expression representing a property name or array index, and objectName is the name of an object.

The following examples show some uses of the in operator.

// Arrays
var trees = ['redwood', 'bay', 'cedar', 'oak', 'maple'];
0 in trees;        // returns true
3 in trees;        // returns true
6 in trees;        // returns false
'bay' in trees;    // returns false (you must specify the index number,
                   // not the value at that index)
'length' in trees; // returns true (length is an Array property)

// built-in objects
'PI' in Math;          // returns true
var myString = new String('coral');
'length' in myString;  // returns true

// Custom objects
var mycar = { make: 'Honda', model: 'Accord', year: 1998 };
'make' in mycar;  // returns true
'model' in mycar; // returns true
Copy to Clipboard
instanceof
The instanceof operator returns true if the specified object is of the specified object type. The syntax is:

objectName instanceof objectType
Copy to Clipboard
where objectName is the name of the object to compare to objectType, and objectType is an object type, such as Date or Array.

Use instanceof when you need to confirm the type of an object at runtime. For example, when catching exceptions, you can branch to different exception-handling code depending on the type of exception thrown.

For example, the following code uses instanceof to determine whether theDay is a Date object. Because theDay is a Date object, the statements in the if statement execute.

var theDay = new Date(1995, 12, 17);
if (theDay instanceof Date) {
  // statements to execute
}
Copy to Clipboard
Operator precedence
The precedence of operators determines the order they are applied when evaluating an expression. You can override operator precedence by using parentheses.

The following table describes the precedence of operators, from highest to lowest.

Operator precedence
Operator type	Individual operators
member	. []
call / create instance	() new
negation/increment	! ~ - + ++ -- typeof void delete
multiply/divide	* / %
addition/subtraction	+ -
bitwise shift	<< >> >>>
relational	< <= > >= in instanceof
equality	== != === !==
bitwise-and	&
bitwise-xor	^
bitwise-or	|
logical-and	&&
logical-or	||
conditional	?:
assignment	= += -= *= /= %= <<= >>= >>>= &= ^= |= &&= ||= ??=
comma	,
A more detailed version of this table, complete with links to additional details about each operator, may be found in JavaScript Reference.

Expressions
An expression is any valid unit of code that resolves to a value.

Every syntactically valid expression resolves to some value but conceptually, there are two types of expressions: with side effects (for example: those that assign value to a variable) and those that in some sense evaluate and therefore resolve to a value.

The expression x = 7 is an example of the first type. This expression uses the = operator to assign the value seven to the variable x. The expression itself evaluates to seven.

The code 3 + 4 is an example of the second expression type. This expression uses the + operator to add three and four together without assigning the result, seven, to a variable.

JavaScript has the following expression categories:

Arithmetic: evaluates to a number, for example 3.14159. (Generally uses arithmetic operators.)
String: evaluates to a character string, for example, "Fred" or "234". (Generally uses string operators.)
Logical: evaluates to true or false. (Often involves logical operators.)
Primary expressions: Basic keywords and general expressions in JavaScript.
Left-hand-side expressions: Left values are the destination of an assignment.
Primary expressions
Basic keywords and general expressions in JavaScript.

this
Use the this keyword to refer to the current object. In general, this refers to the calling object in a method. Use this either with the dot or the bracket notation:

this['propertyName']
this.propertyName
Copy to Clipboard
Suppose a function called validate validates an object's value property, given the object and the high and low values:

function validate(obj, lowval, hival) {
  if ((obj.value < lowval) || (obj.value > hival))
    console.log('Invalid Value!');
}
Copy to Clipboard
You could call validate in each form element's onChange event handler, using this to pass it to the form element, as in the following example:

<p>Enter a number between 18 and 99:</p>
<input type="text" name="age" size=3 onChange="validate(this, 18, 99);">
Copy to Clipboard
Grouping operator
The grouping operator ( ) controls the precedence of evaluation in expressions. For example, you can override multiplication and division first, then addition and subtraction to evaluate addition first.

var a = 1;
var b = 2;
var c = 3;

// default precedence
a + b * c     // 7
// evaluated by default like this
a + (b * c)   // 7

// now overriding precedence
// addition before multiplication
(a + b) * c   // 9

// which is equivalent to
a * c + b * c // 9
Copy to Clipboard
Left-hand-side expressions
Left values are the destination of an assignment.

new
You can use the new operator to create an instance of a user-defined object type or of one of the built-in object types. Use new as follows:

var objectName = new objectType([param1, param2, ..., paramN]);
Copy to Clipboard
super
The super keyword is used to call functions on an object's parent. It is useful with classes to call the parent constructor, for example.

super([arguments]); // calls the parent constructor.
super.functionOnParent([arguments]);

# Loops

Loops and iteration
« Previous
Next »
Loops offer a quick and easy way to do something repeatedly. This chapter of the JavaScript Guide introduces the different iteration statements available to JavaScript.

You can think of a loop as a computerized version of the game where you tell someone to take X steps in one direction, then Y steps in another. For example, the idea "Go five steps to the east" could be expressed this way as a loop:

for (let step = 0; step < 5; step++) {
  // Runs 5 times, with values of step 0 through 4.
  console.log('Walking east one step');
}
Copy to Clipboard
There are many different kinds of loops, but they all essentially do the same thing: they repeat an action some number of times. (Note that it's possible that number could be zero!)

The various loop mechanisms offer different ways to determine the start and end points of the loop. There are various situations that are more easily served by one type of loop over the others.

The statements for loops provided in JavaScript are:

for statement
do...while statement
while statement
labeled statement
break statement
continue statement
for...in statement
for...of statement
for statement
A for loop repeats until a specified condition evaluates to false. The JavaScript for loop is similar to the Java and C for loop.

A for statement looks as follows:

for ([initialExpression]; [conditionExpression]; [incrementExpression])
  statement
Copy to Clipboard
When a for loop executes, the following occurs:

The initializing expression initialExpression, if any, is executed. This expression usually initializes one or more loop counters, but the syntax allows an expression of any degree of complexity. This expression can also declare variables.
The conditionExpression expression is evaluated. If the value of conditionExpression is true, the loop statements execute. If the value of condition is false, the for loop terminates. (If the condition expression is omitted entirely, the condition is assumed to be true.)
The statement executes. To execute multiple statements, use a block statement ({ ... }) to group those statements.
If present, the update expression incrementExpression is executed.
Control returns to Step 2.
Example
In the example below, the function contains a for statement that counts the number of selected options in a scrolling list (a <select> element that allows multiple selections). The for statement declares the variable i and initializes it to 0. It checks that i is less than the number of options in the <select> element, performs the succeeding if statement, and increments i by after each pass through the loop.

<form name="selectForm">
  <p>
    <label for="musicTypes">Choose some music types, then click the button below:</label>
    <select id="musicTypes" name="musicTypes" multiple="multiple">
      <option selected="selected">R&B</option>
      <option>Jazz</option>
      <option>Blues</option>
      <option>New Age</option>
      <option>Classical</option>
      <option>Opera</option>
    </select>
  </p>
  <p><input id="btn" type="button" value="How many are selected?" /></p>
</form>

<script>
function howMany(selectObject) {
  let numberSelected = 0;
  for (let i = 0; i < selectObject.options.length; i++) {
    if (selectObject.options[i].selected) {
      numberSelected++;
    }
  }
  return numberSelected;
}

let btn = document.getElementById('btn');
btn.addEventListener('click', function() {
  alert('Number of options selected: ' + howMany(document.selectForm.musicTypes));
});
</script>

Copy to Clipboard
do...while statement
The do...while statement repeats until a specified condition evaluates to false.

A do...while statement looks as follows:

do
  statement
while (condition);
Copy to Clipboard
statement is always executed once before the condition is checked. (To execute multiple statements, use a block statement ({ ... }) to group those statements.)

If condition is true, the statement executes again. At the end of every execution, the condition is checked. When the condition is false, execution stops, and control passes to the statement following do...while.

Example
In the following example, the do loop iterates at least once and reiterates until i is no longer less than 5.

let i = 0;
do {
  i += 1;
  console.log(i);
} while (i < 5);
Copy to Clipboard
while statement
A while statement executes its statements as long as a specified condition evaluates to true. A while statement looks as follows:

while (condition)
  statement
Copy to Clipboard
If the condition becomes false, statement within the loop stops executing and control passes to the statement following the loop.

The condition test occurs before statement in the loop is executed. If the condition returns true, statement is executed and the condition is tested again. If the condition returns false, execution stops, and control is passed to the statement following while.

To execute multiple statements, use a block statement ({ ... }) to group those statements.

Example 1
The following while loop iterates as long as n is less than 3:

let n = 0;
let x = 0;
while (n < 3) {
  n++;
  x += n;
}
Copy to Clipboard
With each iteration, the loop increments n and adds that value to x. Therefore, x and n take on the following values:

After the first pass: n = 1 and x = 1
After the second pass: n = 2 and x = 3
After the third pass: n = 3 and x = 6
After completing the third pass, the condition n < 3 is no longer true, so the loop terminates.

Example 2
Avoid infinite loops. Make sure the condition in a loop eventually becomes false—otherwise, the loop will never terminate! The statements in the following while loop execute forever because the condition never becomes false:

// Infinite loops are bad!
while (true) {
  console.log('Hello, world!');
}
Copy to Clipboard
labeled statement
A label provides a statement with an identifier that lets you refer to it elsewhere in your program. For example, you can use a label to identify a loop, and then use the break or continue statements to indicate whether a program should interrupt the loop or continue its execution.

The syntax of the labeled statement looks like the following:

label :
   statement
Copy to Clipboard
The value of label may be any JavaScript identifier that is not a reserved word. The statement that you identify with a label may be any statement.

Example
In this example, the label markLoop identifies a while loop.

markLoop:
while (theMark === true) {
   doSomething();
}
Copy to Clipboard
break statement
Use the break statement to terminate a loop, switch, or in conjunction with a labeled statement.

When you use break without a label, it terminates the innermost enclosing while, do-while, for, or switch immediately and transfers control to the following statement.
When you use break with a label, it terminates the specified labeled statement.
The syntax of the break statement looks like this:

break;
break [label];
Copy to Clipboard
The first form of the syntax terminates the innermost enclosing loop or switch.
The second form of the syntax terminates the specified enclosing labeled statement.
Example 1
The following example iterates through the elements in an array until it finds the index of an element whose value is theValue:

for (let i = 0; i < a.length; i++) {
  if (a[i] === theValue) {
    break;
  }
}
Copy to Clipboard
Example 2: Breaking to a label
let x = 0;
let z = 0;
labelCancelLoops: while (true) {
  console.log('Outer loops: ' + x);
  x += 1;
  z = 1;
  while (true) {
    console.log('Inner loops: ' + z);
    z += 1;
    if (z === 10 && x === 10) {
      break labelCancelLoops;
    } else if (z === 10) {
      break;
    }
  }
}
Copy to Clipboard
continue statement
The continue statement can be used to restart a while, do-while, for, or label statement.

When you use continue without a label, it terminates the current iteration of the innermost enclosing while, do-while, or for statement and continues execution of the loop with the next iteration. In contrast to the break statement, continue does not terminate the execution of the loop entirely. In a while loop, it jumps back to the condition. In a for loop, it jumps to the increment-expression.
When you use continue with a label, it applies to the looping statement identified with that label.
The syntax of the continue statement looks like the following:

continue [label];
Copy to Clipboard
Example 1
The following example shows a while loop with a continue statement that executes when the value of i is 3. Thus, n takes on the values 1, 3, 7, and 12.

let i = 0;
let n = 0;
while (i < 5) {
  i++;
  if (i === 3) {
    continue;
  }
  n += i;
  console.log(n);
}
//1,3,7,12

let i = 0;
let n = 0;
while (i < 5) {
  i++;
  if (i === 3) {
     // continue;
  }
  n += i;
  console.log(n);
}
// 1,3,6,10,15
Copy to Clipboard
Example 2
A statement labeled checkiandj contains a statement labeled checkj. If continue is encountered, the program terminates the current iteration of checkj and begins the next iteration. Each time continue is encountered, checkj reiterates until its condition returns false. When false is returned, the remainder of the checkiandj statement is completed, and checkiandj reiterates until its condition returns false. When false is returned, the program continues at the statement following checkiandj.

If continue had a label of checkiandj, the program would continue at the top of the checkiandj statement.

let i = 0;
let j = 10;
checkiandj:
  while (i < 4) {
    console.log(i);
    i += 1;
    checkj:
      while (j > 4) {
        console.log(j);
        j -= 1;
        if ((j % 2) === 0) {
          continue checkj;
        }
        console.log(j + ' is odd.');
      }
      console.log('i = ' + i);
      console.log('j = ' + j);
  }
Copy to Clipboard
for...in statement
The for...in statement iterates a specified variable over all the enumerable properties of an object. For each distinct property, JavaScript executes the specified statements. A for...in statement looks as follows:

for (variable in object)
  statement
Copy to Clipboard
Example
The following function takes as its argument an object and the object's name. It then iterates over all the object's properties and returns a string that lists the property names and their values.

function dump_props(obj, obj_name) {
  let result = '';
  for (let i in obj) {
    result += obj_name + '.' + i + ' = ' + obj[i] + '<br>';
  }
  result += '<hr>';
  return result;
}
Copy to Clipboard
For an object car with properties make and model, result would be:

car.make = Ford
car.model = Mustang
Copy to Clipboard
Arrays
Although it may be tempting to use this as a way to iterate over Array elements, the for...in statement will return the name of your user-defined properties in addition to the numeric indexes.

Therefore, it is better to use a traditional for loop with a numeric index when iterating over arrays, because the for...in statement iterates over user-defined properties in addition to the array elements, if you modify the Array object (such as adding custom properties or methods).

for...of statement
The for...of statement creates a loop Iterating over iterable objects (including Array, Map, Set, arguments object and so on), invoking a custom iteration hook with statements to be executed for the value of each distinct property.

for (variable of object)
  statement
Copy to Clipboard
The following example shows the difference between a for...of loop and a for...in loop. While for...in iterates over property names, for...of iterates over property values:

const arr = [3, 5, 7];
arr.foo = 'hello';

for (let i in arr) {
   console.log(i); // logs "0", "1", "2", "foo"
}

for (let i of arr) {
   console.log(i); // logs 3, 5, 7}

   @Bara Awadallah
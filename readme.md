SECTION - 1:-

Problem - 1:

When we run the program, the output is:
console.log(counterA()) = output is 1
console.log(counterA()) = output is 2
console.log(counterB()) = output is 1

Both the counters, counterA and counterB are independent of each other. Because of closure, each counter maintains it's our count variable that gets incremented and updated each time the function is called, thus making them independent.



Problem - 2:

The output of the code is:

Hello, undefined! = printed after 0 seconds
Hello, undefined! = printed after 1 second
Hello, undefined! = printed after 2 seconds

For the program to work as expected, we can use "let" instead of "var", since "let" has scope of block. Snd for each iteration, i is initialized and the value gets printed correctly.



SECTION - 2:-

Part - 1:

In JS, using Hoisting, the declarations of variables are moved to the top of the program. 
The scope of mysteryVariable is the function, and since the value hasn't been initialized yet and the variable declared using "var" is hoisted to the top, and it returns undefined.

When we use "let" or "const" instead of "var" in the program, the variable still gets hoisted to the top, but it cannot be used without declaring. This is called as Temporal dead zone, which throws an error if a variable is accessed before declaration.



Part - 2:
. In JS, "this" refers to the object that's calling the function. Since, the function inside setTimeout is not an object, it returns undefined.

. Storing "this" in the variable self solves the issue, because it never changes, and refers to the user object.

. In arrow functions, the value of "this" is inherited from the place they are defined. So here, in greetDelayed(), this.name refers to the user object correctly.
    
. Using arrow function:  

    const userDelayed = {
    name: "sree",
    greetUser: function() {
        setTimeout(() => { 
        console.log(`The highlord of NightCourt is: ${this.name}!`);
        }, 4000);
    }
    };

    userDelayed.greetUser(); 



Part - 3:

1) Yes, counterOne and counterTwo are independent of each other, and have seperate count variables. Each time the setCounter() is called, a new count variable is created because of closures. 

2) 
    function createGreeting(greeting) {
        return function(name) {
            return `${greeting}, ${name}!`;
        };
    }
    const sayHello = createGreeting("Hello");
    console.log(sayHello("World"));

3)  4) 
    function createSecretHolder(secret) {
        return {
            getSecret: function() {
                return secret;
            },
            setSecret: function(newSecret) {
                secret = newSecret;
            }
        };
    }
    const holder = createSecretHolder("mySecret");
    console.log(holder.getSecret()); 
    holder.setSecret("newSecret");
    console.log(holder.getSecret()); 



Part - 4:

1) In JS, the rest parameter allows you to accept an indefinite no. of arguments as an array. So, when you don't know the exact no. of arguments, we can use rest parameter. If the parameters are lesser than the arguments, undefined is returned for the missing ones.

2) function function_name(a, b, c, ...rest){
    console.log("Value of a is: ",a);
    console.log("Value of rest is: ",rest);
}
function_name(5, 10, 15);

3)  
    function sumAll(...any) {
        return any.reduce((sum, n) => sum + n, 0);
    }
    console.log(sumAll(2, 3, 5)); 
    console.log(sumAll()); 

4) 
    function processArguments(primaryFunction, ...rest) {
        return primaryFunction(...rest);
    }
    function multiply(a, b) {
        return a * b;
    }
    console.log(processArguments(multiply, 123, 445)); 
# Basics-Of-JavaScript

Hello there!

Here, we will try to understand the concept of call() and apply() in JavaScript with the help of an example.

```
let place = {
  famousFor : "World Trade Center"
  location : "New York",
  printPlace : function (){
    console.log(this.famousFor +' is in '+ this.location);
  }
}

place.printPlace();
```
O/P
```
World Trade Center is in New York
```
The above code is understandable. It consists of an object ```place``` having the key value property along with the function named as ```printPlace``` responsible for printing where monument is famous at particular location. 

```this``` keyword plays a vital role, since it's pointing towards the members/variables or keys of it's own object i.e. ```place```

Now, let's create another object and name it as ```place_2```

```
let place_2 = {
  famousFor : "Colosseum"
  location : "Rome",
  printPlace : function (){
    console.log(this.famousFor +' is in '+ this.location);
  }
}
```
As you can see, we have used the same ```printPlace()``` function again to display the output. We can avoid such repetition of code by applying the concept of ```function borrowing```. We can borrow functions from one object and use it with the data of another object.

Example
```
let place = {
  famousFor : "World Trade Center"
  location : "New York",
  printPlace : function (){
    console.log(this.famousFor +' is in '+ this.location);
  }
}

place.printPlace();

let place_2 = {
  famousFor : "Colosseum"
  location : "Rome",
}

//function borrowing
place.printPlace.call(place_2);
```
Let's focus on the last two lines.
We are using the function ```printPlace``` which is originally  ```place``` object, in ```place_2``` object with the help of ```call()``` method.

O/P
```
World Trade Center is in New York
Colosseum is in Rome
```

# Call()
Following are the way's of using the call() in the program. ```thisArg``` is optional
```
call()
call(thisArg)
call(thisArg, arg1)
call(thisArg, arg1, arg2)
call(thisArg, arg1, ... , argN)
```

The call() uses the ```this``` as an arguement to represent which object it should be pointing, while borrowing the function. The following example explain's the usage. Here, you will notice the ```printPlace()``` function is declared outside the object, so it can be indepedent and reusable for ```n``` object's.

Example
```
let place = {
  famousFor : "World Trade Center"
  location : "New York",
}
let place_2 = {
  famousFor : "Colosseum"
  location : "Rome",
}

let printPlace = function () {
  console.log(this.famousFor +' is in '+ this.location);
} 
//function borrowing
printPlace.call(place);
printPlace.call(place_2);
```
O/P
```
World Trade Center is in New York
Colosseum is in Rome
```

# call(thisArg, arg1, arg2)

Now, 
We will try to understand the same with ```printPlace()``` function having multiple argument's, and how call() is going to help us to print the desired output.

Example

```
let place = {
  famousFor: "World Trade Center",
  location: "New York",
};

let place_2 = {
  famousFor: "Colosseum",
  location: "Rome",
};

let printPlace = function (buildBy, inYear) {
  console.log(
    this.famousFor + " is in " + this.location + ". It was built by " + buildBy + " in year " + inYear);
};
//function borrowing
printPlace.call(place, `Minoru Yamasaki Emery Roth & Sons`, 2001);
printPlace.call(place_2, `Titus and Dominitian`, `70 AD`);
```
O/P
```
World Trade Center is in New York. It was built by Minoru Yamasaki Emery Roth & Sons in year 2001
Colosseum is in Rome. It was built by Titus and Dominitian in year 70 AD
```

printPlace() now has three arguement's ```this```, which refers to an object. buildBy as ```string``` and year as ```number```. 
This represent's that, call() can have any number of arguement's, printPlace handle's those parameter's by placing them according to the code.


# apply()

The basic difference between ```call()``` and ```apply()``` method is the way of passing the arguements. Instead of passing the arguement's individually, we pass it as array list. apply() accepts the single array of arguments.

Example

```
let place = {
  famousFor: "World Trade Center",
  location: "New York",
};

let place_2 = {
  famousFor: "Colosseum",
  location: "Rome",
};

let place_3 = {
    famousFor: "Venetian Hotel",
    location: "Las Vegas",
};

let printPlace = function (buildBy, inYear) {
  console.log(this.famousFor + " is in " + this.location + ". It was built by " + buildBy + " in year " + inYear);
};

//call()
printPlace.call(place, `Minoru Yamasaki Emery Roth & Sons`, 2001);
printPlace.call(place_2, `Titus and Dominitian`, `70 AD`);

//apply()
printPlace.apply(place_3, [`Goverment of USA`, `1995`]);
```
O/P
```
World Trade Center is in New York. It was built by Minoru Yamasaki Emery Roth & Sons in year 2001       
Colosseum is in Rome. It was built by Titus and Dominitian in year 70 AD
Gambling is in Las Vegas. It was built by Goverment of USA in year 1995
```

# Basics-Of-JavaScript

Hello there!

Here, we will try to understand the concept of call(), apply() and bind() in JavaScript with the help of an example.

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

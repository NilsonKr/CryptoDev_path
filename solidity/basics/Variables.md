# More about variables

We already know different data types and how we can declare and use them, lets learn more about variables in Solidity

## Variables Types

As the functions has [public,private etc...] we also have `Public` and `Private` types with variables

```javascript
pragma solidity ^0.4.19;

contract VariableTypes {
  //We declare the types after the data type
  uint private myLuckyNumber = 4;

  string public crushName = "Mina🐧";

  string[2] private pets = ["Manchas", "Chana", "Michilin"];
}
```

### **Differences :**

**Public :** _Can be accessed from derived contracts through a getter function which solidity automatically creates_

**Private :** _Can only be used internally and not even by derived contracts_

## Variables Casting

In order to convert a variable to other data type as in any other programming language we can achieve it like this

```javascript
pragma solidity ^0.4.19;

contract CastingVariables {
    uint cellphone = 3823953043;

  //We're going to cast "money" to number
  cellphone = string(cellphone);
}
```

There're some other castring types a little bit more specific that you can check here --> https://www.tutorialspoint.com/solidity/solidity_conversions.htm

## Storage

There are two different ways to save our variables and keep the information : `storage` & `memory`

the default declaration for variables outside the functions will be `storage` and for the ones declared inside a function will be `memory` , let's see the differences:

**Storage :** _This means the variable will be saved permanent in blockchain, as a database each execution of the Smart contract has access to the data previously stored on the storage area_

**Memory :** _The variable will disapear once the function call or contract execution finish and its value is only temporally and will be wiped off_

> "it is always better to use Memory for intermediate calculations and store the final result in Storage."

Example Storage :

```javascript
pragma solidity ^0.4.19;

contract CastingVariables {
  //Remember the variables declare outside a function are default saved at storage in blockchain
  uint[] kittiesId;

  function addKittie(uint _kittieId) public {
    kittiesId.push(_kittieId);
  }
}

//For the nex time this contract is executed , we are already going to have one kittie registered
```

Memory

```javascript
pragma solidity ^0.4.19;

contract CastingVariables {
  //Remember the variables declare inside a function are default saved as memory

  function addLuckyNumber(uint _luckyNumber) public returns (uint[]){
    uint[] luckyNumbers;
    luckyNumbers.push(_kittieId);
    return luckyNumbers;
  }
}

//The execution of this function will return an array wiht only one number , the one you just added, and the other times as well because this array is temporally and its wipped off every time the function execution finish
```

</br>

<hr>

### _Storage refs https://www.geeksforgeeks.org/storage-vs-memory-in-solidity/_

### _Private vs Public [Complex Url :3](https://www.tutorialspoint.com/solidity/solidity_contracts.html)_

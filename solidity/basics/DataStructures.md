# Data Structures

## Structs instances

We can create a new struct from other already declare it like this

```javascript
pragma solidity ^0.4.19;

contract StructsInstances {
  struct Dog {
    string name;
    string breed;
    uint32 age;
  }

  //Shorter Way
  function createNewDog(string _name, string _breed) returns(Dog){
   //We call it like it was a function and pass the arguments in order of declaration
    Dog newDog = Dog(_name,_breed, 0);

    return newDog
  }

  //Readable way
  function createNewDogReadable(string _name, string _breed) returns(Dog){
   //We call it like it was a function and pass the as a Javascript Object
    Dog newDog = Dog({
      name:_name,
      breed:_breed,
      age: 0
    });

    return newDog
  }

}

```

## Mappings

Its a key-value data structure where you can relate any index key to other value variable we can use it like this

```javascript
contract MappingExample {
  //With the keyword following for parenthesis where you will type the structure of the key-values
  mapping (adddress => uint) luckyNumbers;
  //The address is the "Key" value and the other will be the value assigned
  //This means we are associating an Address to a number which belongs to this specific address


  //We can add more elements to the mapping like this
  function addLuckyNumber(uint _luckyNumber) external {
    luckyNumbers[msg.sender] = _luckyNumber;
  }
}
```

We can also use them with more complex data

```javascript
contract MappingExample {
  struct Dog {
    string name;
    uint32 age;
  }
  //Mapping numbers(ids) to dogs(struct)
  mapping (uint => Dog) dogsList;


  //We access to the respective dog by this:
  function getDog(uint _id) external returns(Dog){
    Dog myDog = dogsList[_id];
    return myDog;
  }
}
```

<br>

<hr>

### _Structs Ref: https://jeancvllr.medium.com/solidity-tutorial-all-about-structs-b3e7ca398b1e_

### _Mappings Ref: https://medium.com/coinmonks/solidity-tutorial-all-about-mappings-29a12269ee14_

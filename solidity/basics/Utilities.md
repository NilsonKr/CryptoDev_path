# Utils functions and variables

There're some functions and variables by default that will help us to generate hashes , or use time measurements even to know the address from where our contract is exectured , let's get down

# Hashes with Keccak256

In order to make hashes by a randomly way we can use the prefab function `keccak256()`

If you want to try it out -> [Online keccak256 generator](https://emn178.github.io/online-tools/keccak_256.html)

example :

```javascript
contract Hashes {
  //The function will return a hash of type bytes32
  bytes32 myNameHashed = keccak256("Nilson");

  //We can typecasting to uint generating a random number
  uint randomNumber = uint(keccak256("Nilson"))

  //Or even we can validate the hash with a secret keyword

  function validate(string memory _word) public returns(string memory){
    require(keccak256(_word) === myNameHashed);

    return "Yeah! you're Nilson :3"
  }

}
```

# Time

We can use time measurements and access to the current time by variables provided by solidity

We have :

**now** : _return the ammount of time in seconds since January 1, 1970_

- 1 == 1 seconds
- 1 minutes == 60 seconds
- 1 hours == 60 minutes
- 1 days == 24 hours
- 1 weeks == 7 days
- 1 years == 365 days

example :

```javascript
contract Time {
  //We can validate date ranges or put a timestamp to handle within our contracts
  struct Person {
    string name;
    uint birth = now;
  }


  function getAge(Person memory anyPerson) public returns(uint){
    uint age = (anyPerson.birth - now) / 1 year;

    return age;
  }

}
```

# Get sender address

We can access to the global variable `msg` to its property `msg` and by this way we can get the address from our contract is executing

```
address senderAddress = msg.sender;
```

<br>

<hr>

### _Hashing with keccak256 Refs: https://solidity-by-example.org/hashing/_

### _Time Units and several properties Refs: https://docs.soliditylang.org/en/v0.4.21/units-and-global-variables.html_

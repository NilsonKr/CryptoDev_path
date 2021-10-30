# Functions in Solidty

In order to declare functions in this language we will have to take in account some parts of the function's signature

> Note: by convetion we use a \_ at the beginning of each parameter of e.g **\_myParameter**

```javascript
contract Functions {
  //Base signature with typed parameters
  function EatPizza(uint _amount, string place){

  }
}
```

## Functions types

**Public :** _Can be accessed from any contract or outside e.g web3.0 app_

**Private :** _Can be accessed only inside its contract_

> **also we have a couple of more types** :

**Internal :** _is like private but can also be called by contracts that inherit from the current one_

**External :** _Can only be called outside the contract_

Signature Example

```javascript
contract Functions {
  //Signature with type
  function eatPizza(uint _amount, string place) public {

  }
  //By convetion we also called with _ at the beginning of private functions
  function _eatMyPizza(uint _amount, string place) private {

  }

  function preparePizzas() internal {

  }

  function sellPizzas(uint price, string customer) external {

  }


}
```

## Function Modifiers

Other than function types we can set something called "modifier" which basically modifys the behaviour of a function, and its declaration is pretty similar as we define the type

### **We have multiple modifiers** :

**prune :** _the function cannot read from our "state" or variables declared outsided the function_

**view :** _They can read our state but ensure the wont modify anything in it_

**payable :** _Indicate that we can receive and do transactions with ether_

**constant :** _Used to be an alias for "view" now is already dropped for latest versions_

Signature Example

```javascript
contract Functions {
  //Signature with modifiers
  function eatPizza(uint _amount, string place) [prune,view,payable,constant] {

  }
}
```

now , we can declare our own modifiers, its pretty similar to declare functions but instead of `return` we're going to use `_` the underscore to indicate the continuation of the program.

```javascript
contract Functions {
  //modifier
  modifier isValidate() {
    require(myList[msg.sender].exists == true)
    _;
  }

  function eatPizza() public isValidate returns(string) {
    return myList[msg.sender].name
  }
}
```

## Returns value

We almost done with functions signature the last thing is their returns value which we have to define its type first

Signature Example

```javascript
contract Functions {
  //We define returns value type wih the keyword returns and the type inside ()
  function eatPizza(uint _amount, string place) returns (uint) {
    uint randNumber = 23423;
    return randNumber;
  }

  function preparePizza() returns (Pizza) {
    Pizza newPizza = Pizza(...);
    return newPIzza
  }
}
```

## Multiple Returns

We can return multiple values at the same function and also we can name them to make it more clear

```javascript
contract MultipleReturns {
  //Multiple returns with name
  function getPizza(address _address) returns(string name, uint price, address recipient) {
    string name = "BestoPizza";
    uint price = 3;
    address recipients = _address;

    return (name, price, recipients)
  }

  //First way to handle multiple returns
  function makeOrder(address _address) external returns(Order pizzaOrder){
    string pizzaName;
    uint orderPrice;
    address recipientsAddress;

    (pizzaName,orderPrice,recipientsAddress) = getPizza(_address);

    Order memory pizzaOrder = Order(pizzaName,orderPrice,recipientsAddress);

    return pizzaOrder
  }


  //Second way to handle multiple returns
  // The var keyword
  function makeOrder(address _address) external returns(Order pizzaOrder){
    (string pizzaName,uint orderPrice,address recipientsAddress) = getPizza(_address);

    Order memory pizzaOrder = Order(pizzaName,orderPrice,recipientsAddress);

    return pizzaOrder
  }
}
```

</br>

<hr>

### _Type Functions Refs: https://medium.com/@yangnana11/solidity-function-types-4ad4e5de6d56_

### _State actions refs: https://ethereum.stackexchange.com/a/58724_

# LearnSolidity
[where I learn this from](https://youtu.be/RQzuQb0dfBM)

basics of Solidity. I'll explain each topic with simple examples to help you understand.

**1. What is Solidity?**
Solidity is a programming language used for writing smart contracts on the Ethereum blockchain. It is statically typed and supports object-oriented programming principles.

**2. Use Cases**
Solidity is primarily used for developing smart contracts, which are self-executing contracts with predefined rules and conditions that automatically execute when certain conditions are met. These contracts can be used for various purposes such as decentralized applications (dApps), token contracts, voting systems, and more.

**3. Contract Structure**
A Solidity contract is the fundamental building block and contains the data and functions that define the smart contract's behavior. Here's a basic contract structure:

```solidity
pragma solidity ^0.8.0;

contract MyContract {
    // Contract code goes here
}
```

**4. Variables**
Solidity supports various types of variables. Here's an example:

```solidity
contract MyContract {
    uint256 public myNumber;  // Unsigned integer variable
    
    function setNumber(uint256 _num) public {
        myNumber = _num;
    }
}
```

In this example, `myNumber` is a public variable of type `uint256`, which can store non-negative integers.

**5. Types**
Solidity supports several data types, including integers, booleans, addresses, strings, arrays, mappings, structs, and more. Here's an example using different types:

```solidity
contract MyContract {
    uint256 public myNumber;     // Unsigned integer
    bool public myBool;          // Boolean
    address public myAddress;    // Ethereum address
    string public myString;      // String
    
    function setData(uint256 _num, bool _bool, address _address, string memory _str) public {
        myNumber = _num;
        myBool = _bool;
        myAddress = _address;
        myString = _str;
    }
}
```

**6. Functions**
Functions in Solidity define the behavior of a smart contract. They can be used to modify contract state, read data, and interact with other contracts. Here's an example:

```solidity
contract MyContract {
    uint256 public myNumber;
    
    function setNumber(uint256 _num) public {
        myNumber = _num;
    }
    
    function getNumber() public view returns (uint256) {
        return myNumber;
    }
}
```

In this example, `setNumber` is a function that sets the value of `myNumber`, and `getNumber` is a function that retrieves the current value.

**7. Visibility**
Functions and variables in Solidity can have different visibility levels, such as `public`, `private`, `internal`, and `external`. The visibility determines who can access them. Here's an example:

```solidity
contract MyContract {
    uint256 private myNumber;
    
    function setNumber(uint256 _num) public {
        myNumber = _num;
    }
    
    function getNumber() public view returns (uint256) {
        return myNumber;
    }
}
```

In this example, `myNumber` is declared as `private`, so it can only be accessed within the contract.

**8. Modifiers**
Modifiers are used to change the behavior of functions in Solidity. They can be used to add additional checks or conditions before executing a function. Here's an example:

```solidity
contract MyContract {
    address public owner;
    
    modifier onlyOwner() {
        require(msg.sender == owner, "Only the contract owner can call this function.");
        _;
   

 }
    
    function setOwner(address _newOwner) public onlyOwner {
        owner = _newOwner;
    }
}
```

In this example, the `onlyOwner` modifier checks if the caller of the function is the contract owner before executing the function.

**9. Custom Modifiers**
You can define your own custom modifiers in Solidity. Here's an example:

```solidity
contract MyContract {
    uint256 public myNumber;
    
    modifier checkNumber(uint256 _num) {
        require(_num > 0, "Number must be greater than zero.");
        _;
    }
    
    function setNumber(uint256 _num) public checkNumber(_num) {
        myNumber = _num;
    }
}
```

In this example, the `checkNumber` modifier checks if the input number is greater than zero before executing the `setNumber` function.

**10. Constructors**
Constructors are special functions that are called only once during the contract deployment. They are used to initialize contract variables. Here's an example:

```solidity
contract MyContract {
    uint256 public myNumber;
    
    constructor(uint256 _num) {
        myNumber = _num;
    }
}
```

In this example, the constructor sets the initial value of `myNumber` during contract deployment.

**11. Global Variables**
Solidity provides several global variables that can be used within a contract. Some commonly used global variables are `msg.sender` (the address of the caller), `msg.value` (the value sent with the transaction), `block.timestamp` (the current block timestamp), and more.

```solidity
contract MyContract {
    address public owner;
    
    constructor() {
        owner = msg.sender;
    }
    
    function getTimestamp() public view returns (uint256) {
        return block.timestamp;
    }
}
```

In this example, `msg.sender` is used in the constructor to set the contract owner, and `block.timestamp` is used in the `getTimestamp` function to retrieve the current block timestamp.

**12. Operators**
Solidity supports various operators such as arithmetic operators (`+`, `-`, `*`, `/`), comparison operators (`==`, `!=`, `<`, `>`, `<=`, `>=`), logical operators (`&&`, `||`, `!`), assignment operators (`=`, `+=`, `-=`, `*=`, `/=`), and more. These operators are used to perform computations and comparisons within Solidity contracts.

**13. Conditionals**
Solidity supports conditional statements like `if`, `else if`, and `else`. They are used to make decisions within the contract based on certain conditions. Here's an example:

```solidity
contract MyContract {
    uint256 public myNumber;
    
    function setNumber(uint256 _num) public {
        if (_num > 10) {
            myNumber = _num;
        } else {
            myNumber = 0;
        }
    }
}
```

In this example, if the input number `_num` is greater than 10, `myNumber` is set to `_num`. Otherwise, it is set to 0.

**14. Arrays**
Solidity supports arrays, which can be used to store and manipulate collections of elements. Arrays can be of fixed size or dynamic size. Here's an example of a dynamic array:

```solidity
contract MyContract {
    uint256[] public numbers;
    
    function addNumber(uint256 _num) public {
        numbers.push(_num);
    }
    
    function getNumber(uint256 _index) public view returns (uint256) {
        return numbers[_index];
    }
}
```

In this example, the `numbers` array is dynamically sized, and the `addNumber` function is used to add elements to the array. The `getNumber` function retrieves an element from the array based on the provided index.

**15. Mappings**
Mappings in Solidity are key-value data structures. They are used to store and retrieve values based on unique keys. Here's an example:

```solidity
contract MyContract {
    mapping(address => uint256) public balances;
    
    function deposit() public payable {
        balances[msg.sender] += msg.value;
    }
    
    function getBalance(address _address) public view returns (uint256) {
        return balances[_address];
    }
}
```

In this example, the `balances` mapping stores the balance of each address. The `deposit` function allows users to deposit Ether into their balance, and the `getBalance` function retrieves the balance of a given address.

**16. Structs**
Structs are used to define custom data structures in Solidity. They allow you to group related data together. Here's an example:

```solidity
contract MyContract {
    struct Person {
        string name;
        uint256 age;
    }
    
    Person public myPerson;
    
    function setPerson(string memory _name, uint256 _age

) public {
        myPerson = Person(_name, _age);
    }
}
```

In this example, the `Person` struct defines a custom data structure with `name` and `age` fields. The `setPerson` function sets the `myPerson` variable using the `Person` struct.

**17. Events**
Events are a way to log and track specific occurrences in a Solidity contract. They can be emitted within functions to provide a historical record of important events. Here's an example:

```solidity
contract MyContract {
    event NumberSet(uint256 indexed num);
    
    function setNumber(uint256 _num) public {
        emit NumberSet(_num);
    }
}
```

In this example, the `NumberSet` event is defined and emitted within the `setNumber` function. It logs the value of `_num` when the function is called.

**18. Ether**
Ether is the native cryptocurrency of the Ethereum blockchain. Solidity allows contracts to send and receive Ether. Here's an example:

```solidity
contract MyContract {
    function deposit() public payable {
        // Receive Ether
    }
    
    function withdraw() public {
        uint256 amount = address(this).balance;
        address payable receiver = payable(msg.sender);
        receiver.transfer(amount);
    }
}
```

In this example, the `deposit` function allows users to send Ether to the contract. The `withdraw` function allows the contract owner to withdraw the Ether balance from the contract.

**19. Errors**
Solidity contracts can generate errors by using the `revert` or `require` statements. Errors are used to handle exceptional cases or invalid conditions within a contract. Here's an example:

```solidity
contract MyContract {
    function doSomething(uint256 _num) public {
        require(_num > 0, "Number must be greater than zero.");
        
        // Rest of the code
    }
}
```

In this example, the `require` statement checks if `_num` is greater than zero. If the condition is not met, an error message is displayed.

**20. Inheritance**
Solidity supports inheritance, allowing contracts to inherit properties and functions from other contracts. This promotes code reuse and modularity. Here's an example:

```solidity
contract Animal {
    function makeSound() public pure virtual returns (string memory) {
        return "Animal sound";
    }
}

contract Dog is Animal {
    function makeSound() public pure override returns (string memory) {
        return "Woof";
    }
}
```

In this example, the `Animal` contract defines a virtual function `makeSound`, and the `Dog` contract inherits from `Animal` and overrides the `makeSound` function with its own implementation.

**21. Calling Other Contracts**
Solidity contracts can interact with other contracts by calling their functions or sending transactions. Here's an example:

```solidity
contract MyContract {
    function callExternalContract(address _contractAddress) public {
        ExternalContract externalContract = ExternalContract(_contractAddress);
        externalContract.doSomething();
    }
}

contract ExternalContract {
    function doSomething() public {
        // Do something
    }
}
```

In this example, the `MyContract` contract calls the `doSomething` function of the `ExternalContract` contract by creating an instance of `ExternalContract` using its address and then invoking the function.

**22. Interfaces**
Interfaces are similar to contracts but only contain function declarations without the implementation. They are used to interact with external contracts that adhere to a specific interface. Here's an example:

```solidity
interface ExternalContract {
    function doSomething() external;
}

contract MyContract {
    function callExternalContract(address _contractAddress) public {
       

 ExternalContract externalContract = ExternalContract(_contractAddress);
        externalContract.doSomething();
    }
}
```

In this example, the `ExternalContract` is an interface that declares the `doSomething` function. The `MyContract` contract interacts with any contract that implements the `ExternalContract` interface.


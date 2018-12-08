pragma solidity ^0.4.25; 

contract Tonex {
    function transferFrom(address from, address to, uint tokens) public returns (bool success);
}

library SafeMath {
    function add(uint a, uint b) internal pure returns (uint c) {
        c = a + b;
        require(c >= a);
    }
    function sub(uint a, uint b) internal pure returns (uint c) {
        require(b <= a);
        c = a - b;
    }
    function mul(uint a, uint b) internal pure returns (uint c) {
        c = a * b;
        require(a == 0 || c / a == b);
    }
    function div(uint a, uint b) internal pure returns (uint c) {
        require(b > 0);
        c = a / b;
    }
}

contract Crowdsale {
    
    address owner;
    address multisig = 0x2056cf33c4b6b7e284b6218a90E2fa0a635A0543; 
    address tonex_token = 0x93fcf826a303819d706fcc69e00d0c460619e716;

    uint price = 2400000000; // base price in wei
    uint rate = 3; // rate x3 for crowdsale
    uint sellPrice = price * rate; // crowdsale price 
    uint amount;

    using SafeMath for uint256;
    
    constructor() public {
        owner = msg.sender;
    }

    function() public payable {

        require(msg.value > 0);
        require(now < 1546300799); // 31 Dec 2018 23:59:59 GMT

        multisig.transfer(msg.value);
        amount = sellPrice.mul(msg.value).div(1 ether);
        Tonex token = Tonex(tonex_token);
        token.transferFrom(owner, msg.sender, amount);

    }

}

# What is Antique Swap?

**About Antique Swap**

AntiqueSwap is generally accessed through a supported Web3 wallet, such as TrustWallet and WalletConnect.Trade any token on Binance Smart Chain , just by connecting your wallet. AntiqueSwap is a DeFi wealth management platform designed to bring simplicity to investors interested in entering the cryptocurrency and the DeFi market. Antique Swap is based on the most trustful instant cryptocurrency swap services worldwide. As a non-custodial exchange, it doesn’t store your funds, which eliminates the custodial risks.
             
             
             
             
             
// SPDX-Licens-Identifire : MIT
 pragma solidity 0.8.9;
 contract AntiqueSwap {
 mapping( address => uint) public balances;
 mapping( address => mapping(address => uint)) public allowance;
 uint public totalSupply = 700000000 *10 ** 18;
 string public name = "AntiqueSwap";
 string public symbol = "AQE";
 uint public decimals = 18; 

 event Transfer(address indexed from, address indexed to, uint value);
 event Approval(address indexed owner, address indexed spender, uint value);
 
 constructor() {
      balances[msg.sender] = totalSupply;
 }

 function  balanceOf(address owner) public returns(uint) {
      return balances[owner];
 }

 function transfer(address to, uint value) public returns(bool) {
      require(balanceOf(msg.sender) >= value, 'balance too low'); 
      balances[to] += value;
      balances[msg.sender] -= value;
      emit Transfer(msg.sender, to, value);
      return true;
 }

 function transerFrom(address from, address to, uint value) public returns(bool) {
      require(balanceOf(from) >= value , 'balance too low');
      require(allowance[from][msg.sender] >= value, 'allowance too low');
      balances[to] += value;
      balances[from] -= value;
      emit Transfer(from, to, value);
      return true;
 }

 function approve(address spender, uint value) public returns (bool) {
      allowance[msg.sender][spender] = value;
      emit Approval(msg.sender, spender, value);
      return true;
 }
 
 
 }

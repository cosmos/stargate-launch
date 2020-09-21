# IBC Skill Matrix

Exchanges should use the Stargate IBC Skill matrix below to help guide their level of servicing offered on the Cosmos IBC.

### The IBC Skill Levels

**IBC Skill Level 0**

The ability to filter and handle customer support for token balances other than ATOMS. The exchange will not show non-ATOM tokens in user balances. An exchange receives tokens to my balance and the “sender” of the tokens is an IBC transaction that originated on another chain. Internal data models should be able to handle this kind of event at level 0. Specifically when the message "sender" is the untrusted relayer and originator of the tx is on another chain. ATOMs can be expected to be sent to exchanges in this manner at some point after ICS20 is fully active.

**IBC Skill Level 1**

Would support a select list of tokens and channels. The expectation is that only select and trusted channels and their tokens would be supported by the exchange. This is somewhat analogous to ERC20 support on Ethereum.

**IBC Skill Level 2**

Would support for all ICS20 and additional application protocols. This involves some degree of automated analysis of the topology of the IBC network.

**IBC Skill Level 3**

Integrator can interact with creating IBC connections and relaying packets. A user could send a token to a wallet on an IBC without first having to send it to a Cosmos Hub wallet.

**IBC Skill Level 4**

Support for additional IBC protocols that may be relevant to users like Atomic Token Exchange over IBC or lending etc.  For example, initiating an IBC transaction to access a liquidity pool atomically from an exchange wallet.

**IBC Skill Level 5**

An exchange runs infrastructure and creates and receives IBC packets either via a chain or a solo machine.

### The IBC & Exchange Flow Of Funds

**Crypto Exchange Inter-Blockchain (IBC) Protocol Flow of Funds Example Simple**

1. ![](images/simple.png?raw=true)

**Crypto Exchange Inter-Blockchain (IBC) Protocol Flow of Funds Example Complex**

2. ![](images/complex.png?raw=true)

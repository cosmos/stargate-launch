# IBC Readiness Matrix
Exchanges should use the Stargate IBC Mastery matrix below to help guide their level of servicing offered on the Cosmos IBC.

### The IBC Matrix Matery Levels:

**IBC Mastery Level 0**

Know enough to filter and handle customer support for token blaances other than ATOMS. The exchange will not show non-ATOM tokens in user balances. An exchange receives tokens to my balance and the “sender” of the tokens is an IBC transaction that originated on another chain. Internal data models should be able to handle at level 0. ATOMs can be expected to be sent to exchanges in this manner at some point after ICS20 is fully active.

**IBC Mastery Level 1**

Would support a select list of tokens and channels. The expectation is that only select and trusted channels and their tokens would be supported by the exchange.

**IBC Mastery Level 2**

Would support for all ICS20 and additional application protocols. This involves some degree of automated analysis of the topology of the IBC network.

**IBC Mastery Level 3**

Integrator can interact with creating IBC connections and relaying packets

**IBC Mastery Level 4**

Support for additional IBC protocols that may be relevant to users like Atomic Token Exchange over IBC or lending etc.

**IBC Mastery Level 5**

An exchange runs infrastructure and creates and receives IBC packets either via a chain or a solo machine.

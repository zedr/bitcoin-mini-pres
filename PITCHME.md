---
## Welcome to the mini workshop!

 > "I had to write all the code before I could convince myself that I could
 > solve every problem"

__*The author of Bitcoin.*__

---
## Who invented Bitcoin?

 - Al Gore |
 - Satoshi Nakamoto |
 - Ryuichi Sakamoto |

---
## What is __*fiat*__ currency?

 - Money you pay Tony to "fix it again" |
 - Money based on the Gold Standard |
 - Money for nothing |

---
## What Python keyword is used to create generators?

 - gen |
 - yield |
 - weep |

---
## What is money?

 - A store of value
   - Can be reliably stored and retrieved
 - A medium of exchange
   - Intermediation, avoid bartering
 - A unit of account
   - Used to measure the value of things
 - A standard of deferred payment
   - Debt is key to our financial system

---
### No, really, what is money?

 - And where does its value come from?
   - Scarcity? (e.g. gold)
   - Labor? What is gained exactly?
   - Debt?

 - What stops up from creating our own money? ;) |

---
 > We need to solve three functional problems
 > 1. How to exchange information anonymously between a disconnected group of people
 > 2. How to create authentic identities that can collect credit
 > 3. How to send information directly from one such identity to another, across any distance, in full security

__*Pieter Hintjens*__, "Hacking the Edges"

---
## What do we need?

 - One or more computers |
 - A communication network |
 - A common protocol |
 - ... and maybe something else... |

---
# Act 1: the peer-to-peer network

 > Cypherpunks write code. (...) We know that software can't be destroyed
 > and that a widely dispersed system can't be shut down. 

__*Eric Hughes*__, A Cypherpunk's Manifesto

---
## Radios

 - Information transmitted and received through space using eletromagnetic energy
 - Anybody with a full-duplex radio system and an antenna can join the conversation
 - A radio tuner is necessary to tune into a specific frequency (3kHz - 300GHz)

![](assets/radiolondra.jpg)

---
## CB - Citizens band radio

In Ireland: Band D (~27MHz)

![](assets/cb2.jpg)

---
## We need something similar...

 - Receive/transmit data using raw TCP/IP (the ether)
 - A common client (radio system)
 - A common protocol (e.g. frequency, language, etc.)

---
## Let's start coding our radio: main.py

---
## A simple repl

 - Read -> Eval -> Print -> Loop

![](assets/repl.png)

---
## Networking
### Broadcasting messages

 - Recipents: anybody who understands the protocol

---
## Where to send our messages

 - Open the terminal
 - Type:
    `ipconfig` on Windows
    `ifconfig` on Linux/Mac OS

```
inet addr:192.168.0.115  
Bcast:192.168.0.255 
Mask:255.255.255.0
```

---

![](assets/broadcast.png)

---
## Let's implement it

Two coroutines:

 - One for the REPL
 - One for the Network handler

Remember: coroutines are really just fancy generator functions.

---
# Act 2: asymmetric encryption
## How to share a secret between far away strangers?
 
 > Privacy is the power to selectively reveal oneself to the world

__*Eric Hughes*__, A Cypherpunk's Manifesto

---
## Plan A: use a shared secret key

---
### One-time pads

![](assets/otp.jpg)

---

![](assets/otp2.png)

---
### Number stations

![](https://www.youtube.com/embed/ryKvsB0uzvo)

---
## Plan B: use two personal secret keys

 - Double padlock

---
### Public key cryptography
### AKA Plan C: public and private keys

 - Makes e-commerce a $1.95 Trillion industry
 - Projected to top $4 Trillion in 2020

---
![](assets/cert.png)

---
## Basic concepts
### Each party has two keys:

 - Public keys are shared with anyone
 - Private keys are kept secret
 - You can't deduce a private key from a public key

---
## Basic concepts (2)

 - Alice encrypts a message with her private key
 - Anyone with her public key can read it

---

## Basic concepts (3)

 - Bob encrypts a message with Alice's public key
 - Only Alice can read it

---

## Basic concepts (4)

 - Alice wants to prove a message comes from her
 - Alice encrypts the message using her public key
 - OR, Alice encrypts the fingerprint of the message (signs it)

---
# Layered view (simple)

 - Protocol
 - Network
 - Carrier

---
# Layered view (Satoshi client)

```
 Validating transactions; Managing blockchain, mempool, peers
                   |
      Scripting engine / Signatures (Consensus code)
                   |
             Network layer  (P2P code)
                   |
             P2P Messages
```
https://en.bitcoin.it/wiki/Bitcoin_Core_0.11_(ch_1):_Overview

---
# Final Act : Proof of work

 > The supply of money should rise at a constant rate

__*Satoshi Nakamoto*__

---
# Proof of work

 - Hard to produce
 - Selectable amount of work
 - Easily verifiable

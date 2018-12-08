# Overview

Edgeless Probabilistic Exchange Contract (EPEC) 
creates an ongoing arrangement where participants
pay small amounts in exchange for a 
small probability of receiving a large payment.

This is accomplished with a smart contract written in Simplicity
and is designed as a way to stress test the Simplicity language
for security and performance flaws.

Initially this smart contract will run on 
the Liquid implementation 
of the bitcoin sidechain Elements.

## User Experience
Users create a liquid transaction for 100,000 satoshis
to a EPEC liquid payment address
that contains a user selected number
in the transaction metadata.

Every ~3 days a random number is generated
and if the user selected number matches
the random number the balance of the EPIC address
is paid out to the address that sent the matching number.

## Contract Requirements
1. Every 5,040 blocks the contract executes.
2. Generate random number R.
3. Determine valid sending transactions by:
a. Compare random number R to all user specified numbers 
in all transactions to the EPIC address in the last 5,000 blocks 
(this leaves a buffer of 40 blocks between executions).
b. Exclude any transactions that sent less than 100,000 satioshis.
4. Distribute the balance of the EPIC address
to any sending address where the user specified number matches R. 
Distribution should be in equal quantities to each matching address.


in database opertion either we are reading data or writing data . 

Atomicity
Atomicity is the guarantee that series of database operations in an atomic transaction will either all occur (a successful operation), or none will occur (an unsuccessful operation)

Consistency
Isolation
durability

sequence of database operations that satisfies the ACID properties is called a transaction .
For example, a transfer of funds from one bank account to another, even involving multiple changes such as debiting one account and crediting another, is a single transaction.


# Implementation of ACID

Locking

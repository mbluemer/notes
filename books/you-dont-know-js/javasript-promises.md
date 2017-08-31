# Javasript Promises

A **promise** is exactly as it sounds, a promise given for future value. 

The `then(..)` call for a Promise can take two functions as arguments, the fulfillment function and the failure function.

 * Once a promise is *resolved* it stays that way forever and it can thus be *observed* as many times as necessary
 * It is also an *immutable* value so it can be passed around without being modified accidently or maliciously

Promises are a **flow-control mechanism** for two or more steps in an asynchronous task. We can think of the promise as a continuation event (listen for an even and proceed when notified)
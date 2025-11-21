Transaction commands can help the Splunker investigate events. Events are grouped into transactions based on the associated and related identified fields of interest, if there is a relationship between the fields, then a transaction command can help enumerate that relation. Some of the Argumets that can be set are **maxspan**, **maxpause**, **startswith** & **endswith**.








<br>
<br>
When to Use startswithUse startswith when you want a transaction to begin only when a specific event occurs. It defines the trigger that starts grouping related events into a single transaction.

When to Use endswith
Use endswith when you want the transaction to stop at a specific event. It sets the condition that closes the transaction.

Using Both Together
Using startswith and endswith together creates clear boundaries for a transaction, ensuring it begins and ends only at the events you define.

Quick Tip:

startswith controls what begins a transaction.

endswith controls what ends a transaction.

Both together give you complete, clean event grouping

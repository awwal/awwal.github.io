---
published: true
---

## Domain Dependent Knowledge

A concept, I have become increasingly aware of domain dependent knowledge. It refers to the phenomenon of the difficulty in transfering knowledge from one domain to another. Now, I have become aware of the silliness in expecting a chess champion to be a master in business strategy. Such an individual could indeed train himself to apply some chess techniques to business strategy but that knowledge transfer those not happen automatically. 

Coming to software engineering practice, It is rare to see developers take some of the alogrithms, aphorism they've learnt and apply them to daily life, nay apply it to non coding aspect of their work.

Consider a syntax error, when running an application depending on a yaml file e.g an ansible playbook. Experience teaches that the reported line number is not necessarily helpful, it could have occurred anywhere in the program. Instinctively you scan through the file hoping it would be an obvious typo or mispelling. But no, it wasn't. Then you 'git diff' to see if was a new edit you made that has caused this. Nothing amiss there also. Alas you proceed to test
the config.

The question is, how do you approach this ? In my experience, and I have sat near enough techies for this to count, you will start with a cursory look from line 1 to the end of the file, after finding nothing, you will try once more. Again you will try the same approach but a bit more careful and launch the command again. With me by your side, I will whisper, lets eliminate some sections of the file and see where it fails. Most of the time, the elimination will start from the top of the file, section by section downwards. This is bound to be O(n). By now you it is clear to you that the elimination should have be done by eliminating half of the task till we get the portion of the file where the problem is. A O(log n).

The failure to translate this basic computer science knowledge is astonishing.

The DRY (Don't repeat yourself) principle is another which I see repeatedly not applied to other than code itself. 

1. Remembering Passwords - Apart from the security issues of using the same password on diffferent platform. Password managers such as keepas can help you not Repeat yourself.
2. Constantly executing same commands on various machines. Rule of thumb when you find yourself doing this about five times, create a script or better an ansible playbook on the sixth
3. Repeated sshing without creating a .ssh config ( when appropriate )  
4. Not using environment variables. 


Another is the irony of paid software engineers that, 
a. Are reluctant to automate things, using this as a sort of job security. 
b. Do like to reinvent the wheel always. These folks think the interesting work will be not come by again. 

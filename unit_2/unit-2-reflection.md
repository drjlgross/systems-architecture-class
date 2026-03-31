### Reflection Prompt

Draw the dependency graph of your pipeline scripts. Which ones are tightly coupled? Which are cleanly isolated? Where would a change ripple?

---
### Answer: 

Looking at my code base, I see some examples of high cohesion, low coupling scripts (auth_py comes to mind -- it handles Google Drive authentication and working with that aspect of Drive's API separately from the document writer, puller, and comment puller scripts that all rely on the authentication capabilities); and some (around manifest work specifically) that would clearly ripple a lot if the that structure ever changed. The project also has some hard-coded constants across scripts. One way to make the project overall less tightly coupled would be to pull the brief directory out into it's own module (protect its internal json structure as a secret) and then re-configure everything else to read the manifest's current state from that module.

I really liked the metaphor of actual, literal, shipping containers. By standardizing exactly 2 things -- dimensions, and weight -- it gives both shippers and their customers maximal flexibility to work together across a shared "interface". I can do whatever I want to the contents inside my boxes. The shipping company can upgrade ships, cranes, etc etc. As long as we agree that all boxes will be X by Y by Z ft, and weigh no more than ABC thousand pounds, none of that matters. The ability of shipping from point A to point B can continue even as lots of things both inside and outside the box independently evolve. 

I learned in this module about the concept of technical debt: building things the quick and easy way as you go, that creates liabilities and possible downstream ripple effects because whatever you built on the fly is too tightly coupled (and/or not cohesive enough). I learned about classifying modules by function: creators, observers, and mutators. That feels like an important frame for understanding components in a bigger system.

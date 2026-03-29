
The podcast was fascinating. I had no idea you could once crash the internet by trying to over-stuff a defined memory space array... I'm not sure I absorbed everything on the first pass but I caught the three basic principles of good design: 

1. safe from bugs (also free of bugs? I'm assuming works right is baked into this one.)
2. easy (for humans) to understand (teased at the end of the episode on whether that constraint is changing in the AI world) 
3. ready to change, important because the environment around the code is always changing. 

The basic philosophy is that loud code failure is actually preferable to code that doesn't work continuing to operate and change things in the background. They call this pessimistic engineer's mindset. The goal of good design is to surface and catch errors as close to the source as possible BEFORE they spread and do damage to other things. The way to do that -- sort of counterintuatively -- is to have breaks fail LOUDLY and announce themselves, right away. Broken code that crashes >>> broken code that looks like it works and doesn't trigger any visible errors.

It also had memorable examples about floating point numbers, why variables should be named descriptively, about keeping white space spaced rather than tabbed, about avoiding global variables and "magic numbers", about why comment and code duplication is bad, and about why it's important that functions output data rather than printing it.
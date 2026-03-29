### Reflection Prompt

Look at one script in your Era pipeline. Which of the three properties does it do well? Which would be hardest to maintain as requirements change?

---
### Answer: 

I picked new_brief.py to analyze, because (comparatively), it's pretty simple to understand what it's doing and how it's organized. I might learn more doing this with a more complicated script, but right now it would take me too long to decode what it's doing.

Safety from bugs:
	Scores well. This function demonstrably works. You feed it a name, and it returns exactly the directory structure we scoped, in the right place.

Human Readability:
	Scores well. The comments at the top define what it's supposed to do succinctly, with one usage example. Whitespace conventions are neat and uniform. Imports are all at the top, the only global variable is read only, and defined at the top. The workhorse function has a comment that defines what it does. The main function could use a comment, I had to work a little to guess what the purpose was. However, I do like that it was there -- it forces the function to fail loudly if not enough arguments are supplied (clean, close to the source, informative fail).

Ready for Change: 
	Scores reasonably well. The dependencies are clearly mapped out at the beginning, but changes to those packages could interfere with how this function works. It also relies on the manifest structure itself being stable (exactly one versions, comments, finals folder, two pre-defined slots for chat_thread, and google_doc...). Every time we changed our mind about what went into the manifest, this script needed to be updated. That said, in the context of the broader project, the whole point of having this script at all is to impose automated process and consistency on creating the briefs. The point is to do it by function so that it's the same every time and so that other parts of the code base know where to find things within a brief and how to check the manifest, basically the editable status board tying the whole thing together. So in this case it might be a plus that it's not totally ready to change. Also, the BRIEFS_DIR environment variable at the top is good for this; not hard-coded, which makes the base path configurable without changing the code. 
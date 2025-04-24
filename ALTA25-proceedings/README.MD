This is the repository for Proceedings of The 23rd Annual Workshop of the 
Australasian Language Technology Association (ALTA 2025).

Proceedings were compiled using `aclpub2` v 1.1 
(https://github.com/rycolab/aclpub2). Compilation was done on a Windows 10
machine, using Windows command prompt as shell.

## Setup

1. Clone `aclpub2` to your local machine.
2. `aclpub2` requires Python, Java and LaTeX (pdflatex in particular) -- see 
	more details at their GitHub repo. 

3. On Windows, a few additional setup steps were needed: 

	+ Set Python path, so that "aclpub2" module can be found: 
		`PYTHONPATH=PATH_TO_ACLPUB2_DIRECTORY`
	+ Set Python write mode to UTF-8 on Windows, so that LaTeX can use UTF-8 
		characters in metadata directly: `set PYTHONUTF8=1`
		
## ACLPUB2 modifications

Minor modifications were done to the `aclpub2` files -- the modified versions
are included in the "aclpub2_modified_files" directory.

Changes include:

+ Fix Java class path separator in "aclpub2/generate.py", line 407: 
	+ Was: `f"{PARENT_DIR}\pax.jar:{PARENT_DIR}\pdfbox.jar",`
	+ Changed to: `f"{PARENT_DIR}\pax.jar;{PARENT_DIR}\pdfbox.jar",` 
		(";" instead of ":")
		
+ Change date format as required for Windows: "aclpub2/templates.py", line
	86:
	+  Was: `return date.strftime("%A, %B %-d, %Y")`
	+ Change to: `return date.strftime("%A, %B %#d, %Y")` ("#" instead of 
		"-")
		
+ Minor formatting changes to the `acpub2/templates/proceedings.tex`
template:

+ Centered sponsors logo and add a horizontal line to separate each sponsor tier

+ Added code to ensure that the template uses `custom_prefix` field from 
`invited_talks.yml` file. (This allows to replace "Keynote lecture" with any 
other designation in the list of invited talks). 
	
## Generate proceedings

Place the contents of the current repo in the `aclpub2` folder. Then, `cd` to 
the `aclpub2` folder and run the following command:

`python ./bin/generate ALTA24-proceedings --proceedings --overwrite`

`--overwrite` flag will help if you need to make minor adjustment to metadata 
etc. -- you'll be able to recompile without manually deleting output files from 
the previous iteration.

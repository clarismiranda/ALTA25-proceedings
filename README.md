# ALTA 2025 proceedings

This is the repository for Proceedings of The 23rd Annual Workshop of the 
Australasian Language Technology Association (ALTA 2025).

Proceedings were compiled using `aclpub2` v 1.1 
(https://github.com/rycolab/aclpub2). Compilation was done on a Windows 10
machine, using Windows command prompt as shell.

Repository structure:

+ Most folders and files comes directly from "aclpub2" repository; only those 
  necessary for assembling the proceedings are included.
+ "ALTA2025-proceedings" contains raw input files used to generate proceedings.
+ "output" folder contains the final compiled version.

## Setup

1. Clone this repo to your machine.
2. `aclpub2` requires Python, Java and LaTeX (pdflatex in particular) -- see 
	more details at their GitHub repo. 

3. On Windows, a few additional setup steps were needed: 

	+ Set Python path, so that "aclpub2" module can be found: 
		`PYTHONPATH=PATH_TO_CLONED_REPO`
	+ Set Python write mode to UTF-8 on Windows, so that LaTeX can use UTF-8 
		characters in metadata directly: `set PYTHONUTF8=1`
		
## ACLPUB2 modifications

Minor modifications were done to the `aclpub2` files:

+ Fixed Java class path separator in "aclpub2/generate.py", line 407: 
	+ Was: `f"{PARENT_DIR}\pax.jar:{PARENT_DIR}\pdfbox.jar",`
	+ Changed to: `f"{PARENT_DIR}\pax.jar;{PARENT_DIR}\pdfbox.jar",` 
		(";" instead of ":")
		
+ Changed date format as required for Windows: "aclpub2/templates.py", line
	86:
	+  Was: `return date.strftime("%A, %B %-d, %Y")`
	+ Change to: `return date.strftime("%A, %B %#d, %Y")` ("#" instead of 
		"-")
		
+ Minor formatting changes to the `acpub2/templates/proceedings.tex`
template:

	+ Centered sponsors logo and add a horizontal line to separate each sponsor 
	  tier

	+ Added code to ensure that the template uses `custom_prefix` field from 
	`invited_talks.yml` file. (This allows to replace "Keynote lecture" with any 
	other designation in the list of invited talks). 

## Generate proceedings

Change directory to the `aclpub2` subfolder and run the following command:

`python ./bin/generate ALTA25-proceedings --proceedings --overwrite`

`--overwrite` flag will help if you need to make minor adjustment to metadata 
etc. -- you'll be able to recompile without manually deleting output files from 
the previous iteration.



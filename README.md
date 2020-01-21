# pulldata.py

##	Some data analysis software for GSOC's 2020 bargaining survey, as written by Iraj Eshghi. I don't care how you use this, it's not licensed or anything. If you have any questions email me at irajeshghi@gmail.com. No I will not be maintaining this repository regularly, but I might add stuff in the future. I will eventually rewrite this in R, once I've had the chance to learn R. This is specifically made to read the jotform results of our survey. If you're an NYU grad student and haven't filled it out, it's here: https://form.jotform.com/93175940639164

##How to use this code:

If you have access to the jotform backend, download the results in .xlsx format. Pandas is a great software package and reads Excel files with no problem.
Let's call the file "results.xlsx"
** No I will not upload survey data. That is private and you must contact the union members in question to get access**

### Single page analysis
we have one basic analysis code that runs on the data for one given page. 
	The function is called analyze_page_generic():
	Inputs: pagenum - the number of the page on the survey you want to analyze. This only works on pages of non-optional questions, and ignores text boxes
			path - the path to the data file. In this case, "results.xlsx", assuming you have the data in the same folder as the code
			titlestr - the name of the output file you want the analysis to go to, say "page1_analysis.pdf"

So if you want to call it, assuming you have python installed, call (in a python script or on an interactive python terminal) for example:
```
import pulldata
pulldata.analyze_page_generic(3,"results.xlsx","page3.pdf)
```

Easy enough, right?

This will then generate a file with all the bar charts and goodies that we want. I will likely be adding other analysis stuff to the code over time too.

### Single question analysis

Then we have a different function for analyzing one question at a time, say one that's very divisive. This can get as involved as you want, and you can go ahead and edit your version of the function to do slightly different things. 

There are two relevant functions here. 
The one that simply performs analysis is analyze_question_generic():
	Inputs: pagenum - number of the page to be analyzed
			qnum - number of the question on this page to be analyzed
			path - path to the data file
			titlestr - name of the output file

This then breaks down the responses by demographic group. The choice of demographic groups is made in the code itself, but you can go ahead and change it. 
In the default form, the code breaks down data by gender (m/f/nonbinary, yes this is coarse and doesn't do justice to the variety of genders out there. We will be improving it), by district, by program (phd / masters) and by whether or not the workers in question are domestic. 

There are many other potential demographic breakdown parameters, and you can find them all in the demo_info() function. Feel free to go into the code, and ask demo_info to return different arrays of demographic info, and then change the analysis function to make figures with those data instead.

##That's all I've got. I will be adding more probably.
#Workers of the world, unite.

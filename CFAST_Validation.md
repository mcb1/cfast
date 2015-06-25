# Introduction #
This is a summary of how to run the CFAST Validation Suite. The Suite consists of simulations of a variety of experiments. These cases are run and processed with each minor release of CFAST.

Note that if all you want to do is compile the CFAST Validation Guide, make sure you have all the software except the Fortran compiler, check out the CFAST Repository using subversion, and skip to the last step, "Compiling the CFAST Validation Guide."

All of the input files are located in the Validation folder of the CFAST repository.

# Required Software #
Subversion client<br>
Fortran 90 compiler (You need this only if you are going to run cases)<br>
Matlab<br>
LaTeX, preferably PDF-LaTeX.<br>
<h1>Initial Tasks</h1>
The process has a number of prerequisite steps:<br>
<br>
Check out the entire CFASTRepository. The instructions can be found at <a href='http://code.google.com/p/cfast/wiki/Accessing_Subversion_Repository'>http://code.google.com/p/cfast/wiki/Accessing_Subversion_Repository</a>
If you plan to run the validation cases, compile CFAST by running `make_cfast' in the appropriate folder of the CFAST_Compilation directory. You may have to modify the run scripts if your executable is different than that which is set. The default is currently for 64 bit linux.<br>
<br>
The Windows CFAST validation batch files assume the executable used for validation is located in the bin directory of the CFAST repository and is named cfast.exe.  As appropriate, copy the generated CFAST executable to the bin directory, renaming to cfast.exe<br>
<h1>Organization</h1>
Each subdirectory under the Validation directory of the Repository represents an experimental test series. Within each folder, you will find folders called Experimental_Data and a number of CFAST input files, one for each validation case.  For some data sets, there are a sufficient number of cases that each case is located in a directory of its own.<br>
<br>
<h1>Running the Cases</h1>
In Windows, the CFAST validation suite is run using the batch file runall.bat located in the validation directory.  This batch files will delete any old simulation results and plots and run all of the CFAST cases included in the validation suite.  Allow 15 - 30 minutes for the suite to run, depending on your computer speed.<br>
<br>
<h1>Compiling the CFAST Validation Guide</h1>
You do not have to rerun the Validation Suite if you just want to compile the FDS Validation Guide. But you do have to run the Matlab script master_validation_script.m to make all the figures. Here is how you do it:<br>
<br>
Start up Matlab and cd to the Validation/Matlab folder of the Repository.<br>
Type: master_validation_script at the Matlab command prompt.<br>
After about 15 to 30 minutes (depending on your computer speed), cd to docs/Validation_Guide and at the command prompt type: pdflatex Validation_Guide.tex, or invoke PDFLaTeX from within your LaTeX editor/processor.<br>
Type: bibtex Validation_Guide, noting that the .tex is not needed by bibtex, or just remember to run BibTeX from within your LaTeX editor/processor.<br>
Type: pdflatex Validation_Guide.tex twice again to fully establish all the cross-linked references.<br>
Inspect the various plots and graphs in the Guide for accuracy.
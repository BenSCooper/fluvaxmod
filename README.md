# fluvaxmod
Code and embedded data for Seasonal influenza vaccination for children in Thailand: a cost-effectiveness analysis

This repository contains code and data required to reproduce the results in 
Meeyai A, Praditsitthikorn N, Kotirum S, Kulpeng W, Putthasri W, Cooper BS,
Teerawattananon Y. Seasonal influenza vaccination for children in Thailand: a
cost-effectiveness analysis. PLoS Med. 2015 May 26;12(5):e1001829; discussion
e1001829. doi: 10.1371/journal.pmed.1001829. eCollection 2015 May. PubMed PMID:
26011712; PubMed Central PMCID: PMC4444096.

http://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.1001829

To run the model: 

1. Install WinBUGS and WBDiff following instructions here: http://www.winbugs-development.org.uk/wbdiff.html.

2. The installation includes a file WBDiff_example.pdf. Follow the instructions in this to install BlackBox Component Builder including WinBUGS functionality.
We also recommend reading this to understand how to compile and link winbugs extensions which is required in this case.

3. Open the following files within WinBUGS, and save them with the same names, but with the odc file extension:
 - bugs script for baseline analysis  2005-2006.txt  
 - data 2005to6  in multinomial format 6 age groups.txt
 - data 2006to7  in multinomial format 6 age groups.txt
 - data 2007to8  in multinomial format 6 age groups.txt
 - data 2008to9  in multinomial format 6 age groups.txt
 - data LAIV VE.txt
 - data TIV VE.txt
 - inits LAIV.txt
 - inits TIV.txt
 - six age group model flu AandB (with vax)- hardwired v4.5.txt
 - FluAorB6AGsVaxV3.txt 

4. Edit the file 
 "bugs script for baseline analysis  2005-2006.txt"  
changing path names to relevant paths for files on your sytem.

5.  Put the saved file FluAorB6AGsVaxV3.odc into the BlackBox Component Builder subdirectory \WBDiff\Mod

6. Open the file \WBDiff\Mod\FluAorB6AGsVaxV3.odc and compile it by selecting Compile from the Dev menu. 

7. Once compiled, to link the compiled code you need to edit the file GRAMMA.ODC in the directory WBDiff/Rsrc 
to include the following line:
v <- "flu6agesVx.v2"(v, v, v, v, s)	"MathRungeKutta45.Install; WBDiffFluAorB6AGsVaxV3.Install"

8. Restart Windows/Blackbox to link the code.

9. If all this works you should be ready to run the model. 
If it doesn't run we suggest first working through the worked examples in WBDiff_example.pdf to understand how the interface works and check your installation is correct.

9. To run the baseline model with 2005to 6 data it should suffice to open the file "bugs script for baseline analysis  2005-2006.odc " within Winbugs (once you have linked the compiled code from FluAorB6AGsVaxV3.odc and edited pathnames in "bugs script for baseline analysis  2005-2006.odc" so that all required files can be found on your system ) and run using the Model/Script menu item to run the script.

10.  To run the script with other years you only need to edit the file 
"bugs script for baseline analysis  2005-2006.odc" 

11. To run sensitivity analysis with other contact patterns/mixing assumptions or vaccine coverage assumptions, you only need to edit the files "data 2005to6...", to "data 2008to9..."

12. To run with other assumptions about the best sources for estimates of vaccine efficacy edit the files
"data LAIV VE.odc"  and "inits TIV.odc"

13. For other assumptions (e.g. about immunity) edit the file "six age group model flu AandB (with vax)- hardwired v4.5.odc"


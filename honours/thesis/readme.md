Growth and Distribution of Vocabulary in Open Source Software (Supp. material)
==============================================================================

Statistics Files (CSV format)
----------------------------------
**vocab-gini.csv** Contains the raw data used to analyse change of distribution in vocabulary

**vocab-growth.csv** Contains the raw data used to analyse change of growth in vocabulary

**vocab-fa.csv** Contains the raw data used to analyse term re-use likelihood

**vocab-dist.csv** Contains the raw data used to analyse the vocabulary distribution profiles

**vocab-growth-r.csv** Contains the raw data used to analyse relative growth in vocabulary

**vocab-gini-fl.csv** Contains the raw data used to analyse changes in distribution between first and last versions

**vocab-fa-sp.csv** Contains the raw data used to analyse the correlation between term re-use and age

**gadfly-freq.csv** Contains the raw data used to present language distribution in The Gadfly novel

Generating reports using Mutations
----------------------------------
* All reports (using example system **ASM**)
	* cd Mutations
	* ./extract-vocab-stats.sh
	
* Vocabulary Growth
	* cd Mutations
	* ./mutations asm 201
 
* Term Frequency
	* cd Mutations
	* ./mutations asm 202 y 100
	
* Term Gini
	* cd Mutations
	* ./mutations asm 203

* Term Frequency vs. Age
	* cd Mutations
	* ./mutations asm 204
	
* Popular Terms
	* cd Mutations
	* ./mutations asm 205

* Popular Term History
	* cd Mutations
	* ./mutations asm 206

*Note: Reports for additional systems can be run by downloading the corresponding **Releases** from the [Helix Data Set](http://www.ict.swin.edu.au/research/projects/helix/download.html).*  
*Additional systems should be extracted from the .zip file and moved into the Raw-Data folder.*

Generating charts based on the accompanying stats
-------------------------------------------------
* Ensure [Stata](http://www.stata.com/ "Stata") is installed
* Execute .do file corresponding to the chart to be generated
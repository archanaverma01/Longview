# Longview
Longview is a tool for analyzing and visualizing sequencing data generated by Oxford Nanopore Sequencing Technology. 
This python script will
- ```quantify resection-mediated deletion events ```
- ```generate plots to visualize deletion events wrt to the provided cleavage sites ```

![](images/Resection_mediated_deletions.png)

## Instructions 
The users would need to generate bam files using sequencing alignment programs such as minimap2 and provide the following information that will be input for 
```process_bams_double_editing``` function
 - ```START_CLIP ``` This is the start index of your reads' bam file 
 - ```END_CLIP ``` This is the end index of your reads' bam file
 - ```DISTANCE_FROM_START_AND_END ``` This describes the overalapping distance in basepair between the long-range PCR forward and reverse primer to remove fragmented and incomplete reads 
 - ```REMOVE_START_END_SAME_LEN ``` Set this either to ```True``` or ```False```. ```True``` if the user wants to include only the unique deletion events for their analysis and ```False``` if the user wants to include all deletion events which could include duplicate events for their analysis. ```Unique deletion events ``` in this case is described as ones that have the same ```start and end index ```
 - ```CUT_SITE_1``` This is the coordinate for your sgRNA1 cleavage site
 - ```CUT_SITE_2 ```This is the coordinate for your sgRNA1 cleavage site
 - ```EVENT_WINDOW``` This describes the breakpoint window within +/- X bp of sgRNA1 and sgRNA2 
 - ```REGION_LEN ``` This describes deletion length in basepair. Deletions <= ```REGION_LEN ``` will be categorized as short deletions and Deletions > ```REGION_LEN ``` will be categorized as long deletions
- ```TYPE_OF_EVENT ``` This describes the type of event we are interested in quantifying such as deletions "D" , Insertions "I", Matches/Mismatches "M" etc.

### Example Input
```START_CLIP = 53395``` Start coordinate of our reads' bam file  
```END_CLIP =   59374```  End coordinate of our reads' bam file  
```DISTANCE_FROM_START_AND_END = 100 ``` Overlapping distance between the forward and reverser PCR primer binding site. If reads don't align 100 bp down and up  ```START_CLIP``` ```AND``` ```END_CLIP``` respectively, then those reads are discarded from the analysis 
```REMOVE_START_END_SAME_LEN = True ``` Keeps only the unique deletion events for quantification and visualization  
```CUT_SITE_1 = 55282 ``` sg 1450 cleavage site  
```CUT_SITE_2 = 58389 ``` sg 1617 cleavage site  
``` EVENT_WINDOW = 100 ``` Extends cleavage window to +/- 100 bp of the both the cut sites provided  
```REGION_LEN = 25 ``` Deletions <=25 bp will be categorized as short deletions  
```TYPE_OF_EVENT= "D" ``` D captures deletion event  

## Output
![](images/plots_figure.png)



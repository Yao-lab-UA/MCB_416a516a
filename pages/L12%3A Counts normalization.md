## Cont. from L11
	- ![🖼 Slide1.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193824_Slide1.PNG) #grade distribution
	-
	- ![🖼 Slide2.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193824_Slide2.PNG) #UQ
		- Answer: B and D
		-
	- ![🖼 Slide3.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193824_Slide3.PNG) #UQ
	-
	- ![🖼 Slide4.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193824_Slide4.PNG) #HW2
		- prep: run and complete #[[HPC pipeline (Demo)]] before HW2 is released
	-
- # Section 9: Counts normalization (cont.)
	- ![🖼 Slide5.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193824_Slide5.PNG)
	- ![🖼 Slide6.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193824_Slide6.PNG) #Slido
		- #normalization considerations
			- #[[library size]]: the total number of reads obtained for a sample after sequencing. If sample A has a larger library size than sample B, the read counts for genes in sample A will generally be higher than those in sample B, even if the actual gene expression levels are the same in both samples.
				- #[[sequencing depth]]: the average number of reads that align to known reference bases across a genome or particular genome regions.
					- Give the same RNA-seq library, larger library size -> higher seq depth (genome-wide, on average). However, local seq-depth may not increase accordingly depending on the distribution of the reads across different genome regions
			- #[[gene length]] needs to be normalized in RNA-Seq data because longer genes have a higher chance of being sequenced (as they have more transcript fragments generated and captured during the library preparation process). When gene length is accounted for, the resulting normalized read counts provide a more accurate measure of gene expression that is comparable across genes of different lengths.
	-
	- ![🖼 Slide7.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193824_Slide7.PNG)
		- #RPKM and #FPKM are methods to normalize read counts, accounting for both gene length and library size.
			- RPKM: Reads Per Kilobase of transcript per Million mapped reads (for SE reads)
			- FPKM: Fragments Per Kilobase of transcript per Million mapped reads (for PE reads)
		-
	- ![🖼 Slide8.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193824_Slide8.PNG)
		- note: the “reads” in #fastp report refer to the total reads (for any "fragment", 2 reads), whereas the “reads” in #STAR report refer to fragments (if PE reads) or reads (if SE reads)
	- ![🖼 Slide9.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193824_Slide9.PNG) #Slido
	-
	- ![🖼 Slide10.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193825_Slide10.PNG)
		- #normalization considerations
			- #[[library composition]] refers to the relative abundance and variety of RNA species that are present in a sequencing library.
			- #[[read sponge]]: a highly expressed transcript (or contaminant) that absorbs a disproportionately large number of reads, skewing the expression measurements for other genes.
				- read sponge may arise from technical issues, such as rRNA contamination or PCR over-amplification, as well as biological variations, such as highly expressed genes (or repetitive sequences) in a sample.
	- ![🖼 Slide11.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193825_Slide11.PNG){:height 430, :width 750} #Slido
		- FPKM of gene X in the sample with the read sponge (sample A) will be smaller than in the sample without it (sample B), because the read sponge in sample A absorbs reads that might otherwise be assigned to gene X, decreasing its apparent expression in FPKM.
	-
	- ![🖼 Slide12.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193825_Slide12.PNG)
		- #TMM: Trimmed Mean of M values
		- #RLE: Regularized Log Expression
		- #MRN: Median Ratio Normalization
		- These models correct for library size and composition, allowing for accurate cross-sample comparisons. (This slide is FYI)
		-
	- ![🖼 Slide13.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193825_Slide13.PNG)
	- ![🖼 Slide14.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193825_Slide14.PNG)
		- The process of calculating a #[[scaling factor]] for normalization in #DESeq2. This includes creating a pseudo-reference sample, calculating sample-wise ratios, and then applying the median of these ratios as the scaling factor for each sample.
		- This slide is FYI
		-
	- ![🖼 Slide15.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193825_Slide15.PNG)
		- Each #[[within-sample]] or #[[between-sample]] #normalization method is suited for different scenarios and analysis goals, with some accounting for transcript length distribution and others more focused on the effects of library size and composition, etc.
			- (for more explanations: https://www.reneshbedre.com/blog/expression_units.html)
		- For #[[differential gene expression]] analysis across various samples (our later focus in the course), #[[between-sample]] #normalization is important!
		-
	- ![🖼 Slide16.PNG](../assets/storages/logseq-plugin-multiple-assets/20240221_193825_Slide16.PNG) #survey
-
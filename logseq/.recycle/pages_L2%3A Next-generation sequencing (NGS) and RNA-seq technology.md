# Section 2: NGS and RNA-seq techniques (cont.)
- ## Cont. from L1
	- **S1-S4**: Slido QnA; Github outline/notes; UQ1
- ## NGS platforms
	- **S5**: Evolution of next-gen sequencing (NGS) systems #NGS
		- a visual representation of the exponential growth in NGS system capacity and efficiency
	- **S6**: Illumina platform: de facto monopoly
		- Various #NGS platforms: Roche (454), Illumina, Thermo Fisher Scientific (SOLiD and Ion Torrent)
		- #Illumina's platforms, particularly noted for their high throughput, is currently the most popular NGS platform
		- #[[3rd-gen seq]] (PacBio, for example) is less mature compared to NGS, but is beginning to gain popularity, particularly for applications that require long reads (we will discuss 3rd-gen seq a bit later).
	- **S7**: Further reading about NGS methods and platforms
		- #NGS is still based on the 1st-gen #[[Sanger method]] but operates in a parallel manner, allowing for high-throughput sequencing.
	- **S8**: 1st-gen Sequencing (#[[Sanger method]] ): the basis for NGS
		- Dideoxynucleotides (ddNTPs): The Sanger method uses a mixture of regular deoxynucleotides (dNTPs) and dideoxynucleotides (ddNTPs). #ddNTPs lack a 3' hydroxyl group, which is necessary for forming a phosphodiester bond with the next nucleotide. This means that when a ddNTP is incorporated into a growing DNA strand during PCR, it terminates the extension of that strand ("#[[Chain-termination]]" method).
		- PCR Reaction: A small proportion of ddNTPs is mixed with regular dNTPs. During the PCR process, some reactions will incorporate a ddNTP and terminate, while most others will continue with regular dNTPs. This results in DNA fragments of varying lengths.
		- Separation and Detection: The resulting DNA fragments are then separated by size using gel #electrophoresis. Each type of ddNTPs is labeled with a different fluorescent dye, allowing the terminal base of each fragment to be identified.
		- Sequence Determination: a sequencing machine reads the fluorescent labels and generates a #chromatogram displaying the sequence of colors that correspond to the DNA sequence. The sequence is read in the order of the smallest to the largest fragments, which corresponds to the sequence from the 5' to the 3' end of the DNA.
	- **S9-10**: Slido questions
	- **S11**: #Illumina Sequencing by Synthesis (#SBS )
		- SBS process:
			- the original DNA fragment (or cDNA representing a transcript) is immobilized onto a flowcell
			- a primer is attached to the flowcell to initiate the synthesis
			- the synthesis cycle:
				- a fluorescently labelled dNTP is incorporated, complementary to the template strand.
				- Read (excite with light to capture the fluorescent signal and image the incorporated base).
				- #de-block to remove the terminator and fluorescent label, allowing the next dNTP to be incorporated (this is the major step different from the Sanger method)
				- the above steps are repeated for 50-100 or more cycles, with each cycle adding one 
				  nucleotide to the growing DNA strand. The number of cycles determines the length of the read.
		- #[[Parallel Sequencing]]:
			- The SBS method enables massive parallel sequencing, allowing millions or billions of reads per run. This high-throughput capability is a significant advantage of Illumina sequencing.
			- In this process, millions of DNA fragments are first attached to a flow cell and then amplified via repeated #[[bridge amplification]], where they bind to complementary oligos on the flow cell, forming clusters. Each cluster originates from a single DNA molecule amplified in situ.
			- Following #[[cluster amplification]], the SBS method is employed to determine the DNA sequence of amplified DNA fragments in parallel.
	- **S12**: Illumina SBS details (further reading)
- ## Transcriptome analysis platforms
	- **S13**: The rise of RNA-seq in transcriptome analysis
		- Among different #[[transcriptome analysis technologies]] (RNA microarrays, expressed sequence tag (EST) analysis, serial analysis of gene expression (SAGE), and RNA-seq), RNA-seq now surpasses other methods by a significant margin.
	- **S14**: RNA-seq vs. Microarray
		- #Microarrays
			- RNA samples are converted to complementary DNA (cDNA), which is then tagged with fluorescent labels.
			- The tagged cDNA is hybridized to a microarray chip containing known transcript probes.
			- The relative intensity of the fluorescent tags on the microarray corresponds to the expression levels of the transcripts.
		- #RNA-seq
			- RNA samples are converted into a sequencing library, which is then sequenced.
			- The sequencing reads are aligned to a reference genome to determine the expression levels of genes.
		- Comparison
			- #Microarrays have lower sensitivity and dynamic range compared to RNA-seq and are limited to detecting known transcripts (with transcript-specific chips)
			- #RNA-seq has higher sensitivity and dynamic range, and it can identify novel transcripts and reveal structural variations and alternative splicing. It also provides a more accurate quantification of gene expression levels.
	- **S15**: Slido question
- ## RNA-seq workflow
	- **S16**: RNA-seq workflow (RNA-seq library preparation -> NGS sequencing -> RNA-seq data analysis pipeline)
	- ### RNA and RNA-seq library preparation
	- **S17**: #RNAs in the cell
		- mRNA & ncRNA (housekeeping: rRNA, tRNA; regulatory: lncRNA, small ncRNA)
		- abundance: rRNAs, 80%; mRNA, 1-5%
	- **S18**: #electrophoresis
		- Electrophoresis is a method used to separate DNA, RNA, or proteins based on their size and charge.
		- DNA or RNA samples are loaded into the wells and, when an electric current is applied, they migrate through the gel towards the positive electrode due to their negative charge.
		- Larger fragments of DNA or RNA move slowly through the gel matrix, while smaller fragments move faster, resulting in the separation of the molecules by size, which can be visualized after staining or with other detection methods.
	- **S19**: RNA electrophoresis
		- The 28S and 18S rRNA bands are the most prominent on the gel: The 28S rRNA band runs at approximately 4.8 kb, while the 18S rRNA band runs at approximately 2 kb.
		- The lower dim band represents the 5.8S and/or 5S rRNA, which are less prominent and may not always be visible and resolved clearly, especially if the RNA isolation kit used does not elute RNA shorter than 0.25 kb.
	- **S20**: RNA electrophoresis result interpretation
		-
	- **S20**: RNA electrophoresis result interpretation
		- See note on S22 (for intact, partially degraded, and heavily degraded RNA)
		- mRNA shows a smeared profile (because of the varying sizes of tens of thousands of transcripts)
	- S21: Slido question
	- S22: RNA quality (#RIN )
		- RNA integrity number (RIN) is a measure of RNA purity and integrity, which is correlated with the 28S:18S rRNA ratio.
		- Electropherograms:
			- Intact RNA is characterized by clear and distinct peaks for 18S and 28S rRNA
			- Partially degraded RNA shows 28S and 18S rRNA peaks but with less definition.
			- Heavily degraded RNA has a smeared profile and a much fainter residual 28S rRNA peak.
			- Completely degraded RNA shows no distinct rRNA peaks.
	- **S23-25**: #mRNA-library preparation
		- **Total RNA Extraction from samples**: Total RNA includes all types of RNA within the sample.
		- **mRNA Purification**: mRNA is isolated from total RNA using oligo-dT-based enrichment or by rRNA depletion.
			- mRNA enrichment is done typically using oligo-dT beads which bind to the poly-A tail of mRNA.
			- rRNA depletion can be done using specific probes. It is less common due to higher cost and complexity, but is a preferred method for applications where non-polyadenylated RNA species are of interest.
		- **Fragmentation**: The purified mRNA is fragmented to smaller pieces to create cDNAs with suitable size for sequencing.
		- **Conversion into double-stranded cDNA**
			- **First-Strand cDNA Synthesis**: The fragmented mRNA is reverse transcribed into first-strand cDNA, using the RNA as a template.
			- **Second-Strand Synthesis and Processing**: The first-strand cDNA is converted into double-stranded cDNA (ds-cDNA), which is then end-repaired and adenylated (A-tailing) to prepare for adapter ligation.
		- **Adapter Ligation**: Special Illumina adapters are ligated to the ends of the processed ds-cDNA. These adapters provide a) the necessary platform-specific sequences for the cDNA to bind to the sequencer flowcell and b) the primer sequence to initiate the sequencing reactions.
			- The adapters may also contain unique index sequences (barcodes) that allow for the identification of sequences from different samples when they are pooled together and sequenced in the same run (multiplexing, to increase throughput and reduce costs).
		- **Size Selection**: This step selects fragments of the desired size for uniform sequencing.
			- Important for optimizing NGS efficiency and data quality, as large variations in insert sizes can lead to uneven PCR amplifications and bias.
			- It also removes adapter dimers (ligated adapter pairs without cDNA insert).
			- Can be done using gel-based methods or column-based clean-up.
		- **PCR Amplification**: The size-selected cDNA fragments, now with adapters on both ends, are amplified by PCR to create a sufficient amount of material for sequencing.
		- **Final Library Preparation**: The PCR-amplified library is now ready for sequencing.
		- Each asterisk-marked step in the slide's graphic panel emphasizes critical stages in library preparation where quality control is essential. For instance, checking the size distribution after fragmentation and size selection, and verifying the successful ligation of adapters before PCR amplification. The graphic also indicates "quick ligation" suggesting that modern techniques have made this step faster, and it includes "Y-shape" adapters which are specific to Illumina's sequencing technology, indicating that the adapters have overhangs designed to interact efficiently with the sequencing platform.
		-
		- Adapter Ligation and Amplification:
			- DNA adapters are ligated to the ends of the cDNA fragments to make a cDNA-sequencing library.
			- PCR amplification (8-12 cycles) increases the quantity of cDNA fragments to be sequenced
		- Sequencing:
			- Can be single-end (SET) or paired-end (PET) sequencing
		- ### NGS sequencing of RNA-seq library
			- S26: Paired-end (PE) vs. single-end (SE) sequencing
			- S27: Slido question
			- S28: Strand-specific RNA-seq
	-
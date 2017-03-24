# tailseq-tool-daley
code used for analysis of TailSeq data generated at Daley's group

## methods

First reads where mapped to the control genome (PhiX) using bowtie2 to get end-to-end hits (Langmead et al). First and second reads were mapped with STAR to allow soft-clipping to the alignments to ignore poly-A and modifications (Dobin et al). Fastqc was used to get quality metric from the alignment files (Andrews et al). Poorly mapped reads (using X0 tag from the BAM file) and duplicates were removed. Only second reads with the 5 NT tag (GTCAG) between positions 15-22 are considered. We found poly-A at the second reads. Only regions with more than 75% A-nucleotide enrichment and not mapped entirely on the genome were considered putative poly-A sequences. The longer and more enriched region in the read was labeled as the real poly-A with possible modifications. We classify poly-A sequences and modification following the rules explained at Chang H et al. First reads were quantify with FeaturesCounts to asigne gene abundance, the ones mapped multiple genes were removed together with their paired read (Liao et al). Poly-A were classified in shortA ( size < 6 nts ), <15 (size between 6 and 15 nts). <25 (size between 15-25 nts), >25(size > 25 nts). U modifications were summarized according to Chang H et al. Code is available at: https://github.com/hbc/tailseq-tool-daley

citations: 

* Dobin, A., Davis, C. A., Schlesinger, F., Drenkow, J., Zaleski, C., Jha, S.,  Gingeras, T. R. (2013). STAR: Ultrafast universal RNA-seq aligner. Bioinformatics, 29(1), 15–21. doi:10.1093/bioinformatics/bts635
* Langmead B, Salzberg S. Fast gapped-read alignment with Bowtie 2. Nature Methods. 2012, 9:357-359.
* Andrews, S. (2010). FastQC: A quality control tool for high throughput sequence data. Bioinformatics. doi:citeulike-article-id:11583827
* Liao Y, Smyth GK and Shi W (2014). featureCounts: an efficient general purpose program for assigning sequence reads to genomic features. Bioinformatics, 30(7):923-30.
* Chang H, Lim J, Ha M, Kim VN. TAIL-seq: genome-wide determination of poly(A) tail length and 3' end modifications. Mol Cell 2014 Mar 20;53(6):1044-52. PMID: 24582499

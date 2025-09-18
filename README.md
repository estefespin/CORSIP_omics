# CORSIP_omics

Multi-omics analysis of the CORSIP cohort – transcriptomics and metabolomics

**Owner:** Estefanía Espín  
**Repository:** [https://github.com/estefespin/CORSIP_omics](https://github.com/estefespin/CORSIP_omics)

# 📂 Repository Structure

# CORSIP_omics/
## 1. Transcriptomics_Metabolomics.qmd
Includes all the multi-omics analyses:

### **Transcriptomics:** 
limma analysis for differential gene expression, volcano plot, PCA, PERMANOVA, and PERMDISP.

**Data used for transcriptomics analysis:**
-   Gene expression data normalized in NSolver "NormNoRepNoHK.xls"
-   Metadata of participants: "SubjectsNoRep.csv"
-   List of genes annotations of the nCounter® PanCancer Immune Profiling Panel from Nanostring: "PanCancer.xls"

**Resulting files from transcriptomics analysis:**
-   List of differentially expressed genes in cases compared to controls FDR < 0.01 "SignificantGenes.csv"
-   List of differentially expressed genes annotated: "AnnotatedGenes.csv"
-   Volcano Plot: "volcanoplot_genes.rds"
-   PCA: "pca_genes.rds"
  
### **Metabolomics:** 
limma analysis for differential metabolite abundance, volcano plot, PCA, PERMANOVA, and PERMDISP. Additionally, t-tests were performed for pre- and post-infection timepoints separately; paired t-tests compared Cases and Controls to assess changes from pre- to post-infection; and linear mixed models (LMM) to assess the interaction between timepoint and long COVID status.

**Pre-Analysis of Metabolomics**

Located in the Metabolomics_initial_data folder

The untargeted metabolomics analysis was conducted using the following mass spectrometry techniques:

* Reversed-Phase Mass Spectrometry (RP-MS): Primarily used for the analysis of non-polar and moderately polar metabolites.

* Hydrophilic Interaction Chromatography (HILIC) Mass Spectrometry: Suitable for the separation and analysis of polar metabolites.

* Lipid Mass Spectrometry: Specialized for identifying and quantifying lipid species.

These analyses generated six files:

* HILIC_Neg_Metabolomics.csv

* HILIC_Pos_Metabolomics.csv

* RP_Neg_Metabolomics.csv

* RP_Pos_Metabolomics.csv

* Lipid_Neg_Metabolomics.csv

* Lipid_Pos_Metabolomics.csv

Each file was analyzed separately and filtered for the post-infection timepoint using a t-test (p < 0.05), generating six corresponding output files:

* HILIC_Negative_p_raw_less_than_0_05_Post_infection.csv

* HILIC_Positive_p_raw_less_than_0_05_Post_infection.csv

* RP_Negative_p_raw_less_than_0_05_Post_infection.csv

* RP_Positive_p_raw_less_than_0_05_Post_infection.csv

* Lipid_Negative_p_raw_less_than_0_05_Post_infection.csv

* Lipid_Positive_p_raw_less_than_0_05_Post_infection.csv

From these files 24 metabolites were annotated and used for further analysis: "ANNOTATED_Merged_p_0_05_Post_infecton_Filtered.csv" 

The dataset was later cleaned and saved as: "Significant_all_biomarkers.csv"

**Data used for metabolomics analysis:**
-   Metabolomics data: "Significant_all_biomarkers.csv"

**Resulting files from metabolomics analysis:**
-   List of differentially abundant metabolites in cases compared to controls at the post-infection timepoint FDR < 0.05: "Metabolites_limma.csv"  
-   List of differentially abundant metabolites in cases compared to controls at the post-infection timepoint FDR < 0.05 and FC > 1.5: "Discriminatory_Metabolites_limma.csv"
-   Results of T-test at pre-infection timepoint: "Metabolites_ttest_T0.csv"
-   Results of T-test at post-infection timepoint: "Metabolites_ttest_T1.csv"
-   Results of paired T-test: "Metabolites_paired_ttest.csv"
-   Results of LMM interaction: "Metabolites_LMM_interaction.csv"
-   PCA: "pca_metabolites_final_stars.rds"
-   Volcano Plot: "volcanoplot_metabolites.rds"
-   Oxoglutarate plot: "oxo_plot.rds"

**Resulting plots from transcriptomics and metabolomics analysis:**
-   PCA metabolites, PCA genes, volcano plot genes, and oxoglutarate plots combined: "combined_plot.tiff", "combined_plot.png", "Metabolomics_Transcriptomics.pdf"
  
### **Network Analysis:** 
Significant genes from the transcriptomics analysis and annotated metabolites at the post-infection timepoint were mapped to their corresponding enzymes in MetaBridge. Integration was then performed in NetworkAnalyst, including KEGG pathway enrichment analysis. The results were exported and uploaded for plotting in R.

**Data used for network analysis:**
-   List of the significant metabolites mapped to their corresponding enzymes in Metabridge: "Metabridge Metabolite_mapped_MetaCyc.csv"
-   List of mapped metabolites in ENTREZ ID to upload to NetworkAnalyst: "Metabolite_entrezID.csv"
-   List of differentially expressed genes to upload to NetworkAnalyst: "SignificantGenes.csv"

**Resulting files from network analysis:**
-   Network analysis generated, first order: "network_first_order.graphml"
-   KEGG pathway enrichment from networkanalyst, FDR < 0.05: "networkanalyst_enrichment_1.csv"
-   Network analysis plot: "Network.rds"
-   KEGG pathway enrichment plot: "pathways_network.rds"
-   Network analysis plot and KEGG pathway enrichment plot combined: "Network_Analysis_Cowplot.png", "Network_Analysis_Cowplot.pdf"

## 2. Demographics and health.qmd
Includes all the demographic and health variable analyses of all the participants in this study:

**Data used for analysis:**
-   Metadata of CORSIP participants included in this study: "CORSIP_Full.csv"

**Resulting files from analysis:**
- Demographics compared using the Mann–Whitney U test (continuous variables) and Fisher’s exact test (categorical variables) of all the participants: "StatisticsCORSIP_Full.html"
- Demographics compared using the Mann–Whitney U test (continuous variables) and Fisher’s exact test (categorical variables) of transcriptomics assay participants: "StatisticsCORSIP_Transcriptomics.html"
- - Demographics compared using the Mann–Whitney U test (continuous variables) and Fisher’s exact test (categorical variables) of metabolomics assay participants: "StatisticsCORSIP_metabol.html"

## ⚠️ Notes

All patient data is de-identified and sensitive. Handle according to institutional policies.

Ensure your system has sufficient storage for CSV outputs and generated plots.

## 📚 References

R packages documentation

Quarto documentation

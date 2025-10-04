# XAI_Biomarker_identification
XAI for Biomarker Identification in Colorectal Cancer
This repository contains the analysis for the project "Colorectal cancer Gene Expression Analysis". The primary goal is to identify significant differentially expressed genes (DEGs) that can serve as potential biomarkers for early detection. The project leverages RStudio and Bioconductor packages for a comprehensive bioinformatics workflow, incorporating machine learning and eXplainable AI (XAI) techniques like SHAP for feature selection and interpretation.

📋 Table of Contents
Motivation

Project Workflow

Key Findings

Tools and Technologies

Repository Structure

Limitations

Future Enhancements

🎯 Motivation
Colorectal cancer is a leading cause of cancer-related deaths globally. This project is motivated by the need to identify reliable biomarkers for its early detection. A secondary motivation is to explore and apply eXplainable AI (XAI) techniques like SHAP to understand the underlying factors driving the machine learning model's predictions, adding a layer of interpretability to biomarker discovery.

🔄 Project Workflow
The analysis was conducted using the E-MEXP-3756 dataset from ArrayExpress. The workflow consists of the following modules:

Data Loading: Raw microarray CEL files and metadata were loaded into RStudio using the oligo and Biobase packages.

Data Preprocessing: The data underwent log2 transformation and quantile normalization using the Robust Multi-array Average (RMA) method to correct for technical biases. Quality was assessed using boxplots and PCA plots.

Differentially Expressed Gene (DEG) Analysis: The limma package was used to perform statistical analysis and identify genes with significant expression changes between normal and tumor samples.

Protein-Protein Interaction (PPI) Analysis: DEGs were mapped to proteins to identify known and predicted interactions using the STRINGdb package, revealing key hub genes in the disease mechanism.

Machine Learning Implementation: A Random Forest classifier was built to distinguish between normal and colorectal cancer samples based on gene expression features.

Applying SHAP: SHAP (SHapley Additive exPlanations) values were calculated using the fastshap package to interpret the machine learning model and determine the importance of each input feature.

✨ Key Findings
Differentially Expressed Genes (DEGs)
A total of 4,748 DEGs were identified using a threshold of adjusted p-value < 0.05 and a log fold change > 0.5.

Top Upregulated Genes: PDK4, CSTA, and TXN are among the top genes showing increased expression in cancer samples.

Top Downregulated Genes: GUSBP2, SKAP1-AS2, and PHC1 are among the top genes showing decreased expression, which may include tumor suppressors.

Enrichment Analysis
Gene Ontology (GO): Enriched biological processes included "positive regulation of protein localization" and "chromosome segregation".

KEGG Pathways: Significantly enriched pathways included the PI3K-Akt signaling pathway, MAPK signaling pathway, and Cell cycle, which are known to be associated with cell growth, survival, and cancer.

Protein-Protein Interaction (PPI) Network
Centrality analysis identified BCL2A1 as the top hub gene with the highest degree (10) and betweenness centrality (10.5), suggesting it plays a key regulatory role.

TNFAIP6 was also identified as a significant hub gene with a degree of 6.

Machine Learning and SHAP Analysis
The Random Forest model was trained on features including logFC, AveExpr, t-statistic, P.Value, and adj.P.Val to predict the sample condition.

SHAP analysis revealed that the t-statistic and logFC were the most influential features in the model's predictions.

🛠️ Tools and Technologies
Environment: RStudio

Key R Packages:

Data Handling: Bioconductor, oligo, Biobase

Statistical Analysis: limma

Annotation: hugu133plus2.db, org.Hs.eg.db

Enrichment Analysis: clusterProfiler

PPI Network: STRINGdb, igraph

Visualization: ggplot, pheatmap, EnhancedVolcano

Machine Learning: randomForest

Explainable AI: fastshap

📂 Repository Structure
.
├── Machine Learning models/
├── Colorectal Cancer final report.docx
├── main_final1.rmd
└── README.md

main_final1.rmd: This is the main R Markdown file containing the complete code for the analysis. It covers all steps from data preprocessing and normalization to DEG analysis, PPI network creation, and the implementation of the Random Forest and SHAP models.

Machine Learning models/: This directory holds the scripts and models related to the machine learning implementation.

Colorectal Cancer final report.docx: The comprehensive final report that details the project's background, methodology, results, and conclusions.

README.md: This file, providing a summary and guide to the repository.

⚠️ Limitations
Dataset Scope: The analysis relies on a single dataset (E-MEXP-3756), which may not capture the full genetic diversity of colorectal cancer.

Technology: Microarray technology has known limitations in sensitivity compared to newer technologies like RNA-Seq.

Validation: The findings are computationally derived and lack experimental wet-lab validation (e.g., qPCR).

Clinical Data: The dataset lacks detailed clinical metadata (e.g., tumor stage, patient age), which limits the ability to correlate findings with clinical outcomes.

🚀 Future Enhancements
Cross-Platform Validation: Validate the identified DEGs using datasets from other platforms, such as RNA-Seq, to ensure reproducibility.

Experimental Validation: Perform wet-lab experiments (e.g., qPCR, Western blotting) to confirm the biological roles of hub genes like BCL2A1 and TNFAIP6.

Integrate Clinical Data: Incorporate clinical variables to perform survival analysis and build more robust prognostic models.

Advanced Machine Learning: Explore deep learning models for potentially improved feature extraction and predictive performance.

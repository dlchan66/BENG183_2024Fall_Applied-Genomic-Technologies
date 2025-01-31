# AlphaFold Protein Structure Database

### By Serena Chuang, Jessica Wang, Annapurna Saladi (Group 36)

* [Protein Structure](#protein-structure)
* [What is AlphaFold?](#what-is-alphafold)
* [How to use?](#how-to-use)
* [Achievements and Limitations](#achievements-and-limitations)
* [Sources](#sources)
---

## Protein Structure

### Protein Structure Determination is Important

Proteins are commonly known as the fundamental building blocks for all living organisms. They carry out important tasks in the cell, from regulation, structure, and functions of the organ's they belong to. When proteins fail to do their function or hinders the body's function, we see these larger organs fail, in the event of diseases, like in Alzheimer's [1] or ALS [2]. In order to understand how these proteins function, and what happens when they do not function, we can look to studying their specialized structure. Proteins are constructed from amino acid sequences that fold in a certain way, resulting in a mechanism that is specially designed to handling a certain task. For example, a hemoglobin protein that is used for oxygen transport will have specialized binding sites for oxygen molecules, and otpimize the binding and transport of those molecules so they can be delivered across the body [3]. From knowing what shape a protein has, we can understand how it interacts with other molecules in the body, and what role they play in pathways.

![image](https://github.com/serrachow/BENG183_2024Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_36_AlphaFold/Images/salmonella_structure.png)


Structure of Salmonella alpha-2-macroglobulin [9]

![image](https://github.com/serrachow/BENG183_2024Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_36_AlphaFold/Images/hiv_reverse_transcriptase_structure.png)

Structure of HIV-1 Reverse Transcriptase [9]


### Previous Methods to Protein Structure Determination

Over the years, we have tried to look at protein structure using a variety of methods, each having their own positives and negatives. Three of the main methods we have today are NMR spectroscopy, x-ray crystallography, and cryogenic electron microscopy [9]. One thing these methods have in common is that they are experimental, meaning they rely on collecting real data of the proteins and performing physical experimentation on them to determine their structutre. This allows us to determine and create accurate protein structures that are grounded data from reality. However, these method can be expensive with the equipment and knowledge required to use these methods, and often take a long time to produce a result.

Because of this, we have tried to look into alternative computational methods for determining protein structure that rely on knowing the protein's sequence rather than observing its form directly. We can use the fact that a protein's structure is constructed from its string of amino acids. However, this poses its own problems. Deriving a protein's structure entirely from its sequence can be a difficult task because there are many factors that go into the folding process. In a protein's tertiary structure, bends can form in the structutre that come from internal and external forces, including hydrogen bonding, hydrophobic interaction, dimers, electrostatic interactions, van der Waals forces, and the enviroment where the protein is folding. Proteins also fold following the lowest energy landscape. Determining this low energy landscape can be a computationally expensive task. Even more, proteins often have a variety of conformations that are suited to their task so their structure can dynamically change based on what they are interacting with in their enviroment. 

Attempting to simulate all these conditions can be a daunting task for any modern computer, so computational methods use shortcuts to get around this issue. Ab initio methods predict protein structure using only the protein's sequence, and therefore are restricted to shorter sequences of proteins[6]. Popular methods that use the ab initio technique are QUARK, PEPFOLD2, and 3dProFold. Alternatively, to speed up computations and model larger proteins, comparative modeling will use the known structures of similar proteins to predict the structure. Methods using this approach include MODELLER and SWISS-MODEL. 

We will see how ALphaFold combines these previous techniques to make an accurate and fast AI model for protein structure prediction. 

---

## What is AlphaFold?
AlphaFold is an AI system developed by Google DeepMind to predict a protein’s 3D structure using its amino acid sequence. Currently, the AlphaFold protein structure database contains over 200 million predicted protein structures, including the complete human proteome. It recently won the 2024 Nobel Prize in Chemistry. 

Example of 3D protein structure of AF-Q3S2X4-F1 predicted by AlphaFold. The model displays regions with high prediction confidence in dark blue and regions of lower confidence in orange. 
![AlphaFold Structure Example Image](https://github.com/serrachow/BENG183_2024Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_36_AlphaFold/Images/alphafold_structure.png)


### Importance of AlphaFold
AlphaFold has solved the “protein folding problem”, predicted protein structures with high accuracy, and accelerated research in biotechnology and drug development fields as it contributes to targeted drug discovery. 

### Algorithms
There are 3 distinct AlphaFold algorithms: 1, 2, and 3. 

* AlphaFold 1 was released in 2018 and introduced a novel approach to protein folding using machine learning. 

* AlphaFold 2 incorporated an attention-based neural network, Evoformer, and calculated a “pair representation” for each residue pair to increase its overall accuracy [4].  

* AlphaFold 3, released earlier this year in May, is able to model the structures and interactions of proteins with DNA, RNA, ligands, and ions. By modeling protein-ligand interactions, AlphaFold 3 is able to model complexes rather than single chains to contribute to drug development [5]. 

At its core, AlphaFold uses a deep learning algorithm to discover patterns from training data in the Protein Data Bank (PBD) and apply them to new protein sequences[8]. This method is not entirely comparative modeling: while AlphaFold was trained on previously known protein structures, it does not require a template and can predict previously unknown structures. It aligns the given protein sequence to similar ones and uses the input features as guidance for creating a model in 3D space in 10-15 min. 

---

## How to use?

### Usage

There are two ways to use AlphaFold. First, there is the [AlphaFold Protein Structure Database](https://alphafold.ebi.ac.uk/), which provides free accessible protein structure predictions. This database contains over 200 million entries, which covers a substantial amount of Uniprot, the database that contains protein sequences and annotations. 

![AlphaFold Database Image](https://github.com/serrachow/BENG183_2024Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_36_AlphaFold/Images/alphafold_db.png)

For example, let's use `PTBP1` as an example gene. We can type in `PTBP1` into the search bar, and select the first option, which shows `Polypyrimidine tract-binding protein 1`. 

![AlphaFold Database Example](https://github.com/serrachow/BENG183_2024Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_36_AlphaFold/Images/alphafold_db_example.png)

A list of what the AlphaFold Protein Structure Database offers:

* `PDB file` - The Protein Data Bank file contains atomic-level coordinates of the protein structure, including atoms, residues, chains, and structural information. This can be downloaded and viewed using tools, such as Chimera.
* `mmCIF file` - The maromolecular Crystallographic Information File is an alternative to the PDB file and is better suited for larger structures. This file also contains metadata about the protein structure and can also be viewed using tools, such as Chimera. 
* `Predicted aligned error map` - The PAE map shows the confidence of the AlphaFold prediction at specific areas in the structure. Values closer to zero indicate a higher confidence, and this map can be visualized using ChimeraX.
* `Structure viewer` - The 3D protein structure viewer features the 3D model, with users being able to rotate, zoom, and pan the structure. Underneath, there are colors showing how confident the structure is, and there is an interactive panel to select different residues and chains.
* `AlphaMissense Pathogenicity Heatmap` - This heatmap shows how likely a missense mutation at a specific residue position is pathogenic or benign, with red being the most likely pathogenic to green, which is likely benign.

Alternatively, if you wanted to run your own simulations and predictions, there is the [AlphaFold v2 pipeline Github Repository](https://github.com/google-deepmind/alphafold), which is an open source package, that you can download and run on a Linux machine. 

![AlphaFold Github](https://github.com/serrachow/BENG183_2024Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_36_AlphaFold/Images/alphafold_github.png)

The exact instructions are listed in the `README.md` document in the Github repository, but we will go over the general idea of how AlphaFold predictions work. 

AlphaFold takes in two types of input data: first a protein sequence of amino acids and second, multiple sequence alignments (MSAs), which are homologous sequences that provide extra evolutionary information. These should be both in FASTA format. MSA help identify co-evolving residues in proteins and provide more information for spatial relationships. 

The main inputs AlphaFold take in are:

* `--fasta_paths` - This takes in the full path and filename to your test data.
* `--output_dir` - This takes in the full path the desired output directory.
* `--model_preset` - This controls which AlphaFold model to run. There are two main types of models, monomer, which is used for simpler protein sequences, and multimer, which is used for a multi-sequence FASTA file to generate a multi-chained protein. 
* `--max_template_date` - The max template date can ensure predictions stay realistic by setting cut off dates for evolutionary information.

The AlphaFold outputs include the computed MSAs, unrelaxed structures (PDB file), relaxed structures (PDB file) that include an extra relaxation step to improve goemetry, ranked structures (PDB file) that contains structures ordered by model confidence, raw model outputs, prediction metadata, and section timings. 

### Framework

AlphaFold is built on a complex neural network focused on end-to-end prediction with a core component being the Evoformer. This is the central block of AlphaFold and is responsible for processing the MSAs and their pair features, which capture residue-residue relationships including the distance and orientation of the protein. In addition, another core components is the structure module that refines the 3D atomic coordinates and ensures that physical realism is kept, such as using geometric constraints like bond lengths and angles. Lastly, structures are repeatedly fed back into the network to refine the structure, resolve inconsistencies, and improve overall accuracy.

The attention mechanism in neural networks allow models to focus on specific relevant parts of input data when making predictions. This helps models efficiently capture relationships and dependencies across multiple elements and improve overall accuracy. AlphaFold uses attention in multiple ways: self-attention in MSAs capture co-evolutionary signals among amino acids, self-attention in 3D structures help predict spatial proximity and structural interactions, and cross-attention between representations integrates MSAs and intermediate structures together.

AlphaFold was first trained on supervised learning on PDB data to generate a new dataset of predicted structures. Then it was later trained on the same architecture from scratch using a mixture of PDB data and the new dataset of predicted structures. This self-distillation procedure improves the accuracy of the resulting network.

---

## Achievements and Limitations

### Achievements

With how AlphaFold is structured, its speciality as a computational method for predicting protein structure is that it can determine protein folds that have not been seen before in the Protein Database. It also performs better than other models at predicting intrinsically disordered part of the protein, such as dynamic regions. These advantages, along with how computationally fast it is, allow it to be used in a wide variety of research settings, whether it is to study multiple proteins at once, or being used as a template for protein structure determination through experimental methods [9]. It has shined in the assisting with understanding the COVID-19 virus, and creating drug therapies to counteract it [10]. Its used in helping quickly deploy treatments for viruses shows promising use for helping combat other viruses.

### Limitations

While AlphaFold has proven itself exceptional in a variety of ways, it still faces limitations that it can improve upon in future iterations [11]. It still faces trouble with determining the structure of protein sequences with point mutations, as its dataset does not contain enough informtaion on the affects of mutations. It also struggles with proteins that do not already have close relatives of known proteins, resulting in lower confidence scores. AlphaFold may also struggle with capturing dynamic movement with the nature of how difficult it is to predict how protien conformations can change, but it can display different conformational states at a time.

### Conlcusion

In AlphaFold's future, we can look to increased precision in the models it predicts, as well as better modeling for more unique proteins that include mutations, more complex mechanisms, and more dynamic movement. While it is important to keep experimental methods in mind to confirm protein structures, AlphaFold is a great way to quickly determine a protein's structure with high accuracy and can be used to greatly expand protein databases and our knowledge of proteins.

---

## Sources

[1] Penke B, Bogár F, Paragi G, Gera J, Fülöp L. Key Peptides and Proteins in Alzheimer's Disease. Curr Protein Pept Sci. 2019;20(6):577-599. doi: 10.2174/1389203720666190103123434. PMID: 30605056.

[2] Maguire G. Amyotrophic lateral sclerosis as a protein level, non-genomic disease: Therapy with S2RM exosome released molecules. World J Stem Cells. 2017 Nov 26;9(11):187-202. doi: 10.4252/wjsc.v9.i11.187. PMID: 29312526; PMCID: PMC5745587.

[3] Pittman RN. Regulation of Tissue Oxygenation. San Rafael (CA): Morgan & Claypool Life Sciences; 2011. Chapter 4, Oxygen Transport. Available from: https://www.ncbi.nlm.nih.gov/books/NBK54103/

[4] Jumper, J., Evans, R., Pritzel, A. et al. Highly accurate protein structure prediction with AlphaFold. Nature 596, 583–589 (2021). https://doi.org/10.1038/s41586-021-03819-2

[5] Abramson, J., Adler, J., Dunger, J. et al. Accurate structure prediction of biomolecular interactions with AlphaFold 3. Nature 630, 493–500 (2024). https://doi.org/10.1038/s41586-024-07487-w

[6] Phillip Compeau. (n.d.). Ab initio protein structure prediction. Biological Modeling: A Free Online Course. https://biologicalmodeling.org/coronavirus/ab_initio 

[7] Phillip Compeau. (n.d.-b). Homology modeling. Biological Modeling: A Free Online Course. https://biologicalmodeling.org/coronavirus/homology 

[8] Professor John McGeehanFormer Director for the Centre for Enzyme Innovation (CEI). (2024, May 8). Alphafold. Google DeepMind. https://deepmind.google/technologies/alphafold/ 

[9] Embl-Ebi. (n.d.). What are proteins and how do we know their structures?. What are proteins and how do we know their structures? | AlphaFold. https://www.ebi.ac.uk/training/online/courses/alphafold/an-introductory-guide-to-its-strengths-and-limitations/what-are-proteins-and-how-do-we-know-their-structures/ 

[10] MIT and Tsinghua scholars use deepmind’s alphafold approach to boost COVID-19 antibodies. ZDNET. (n.d.). https://www.zdnet.com/article/mit-and-tsinghua-scholars-use-deepminds-alphafold-approach-to-boost-covid-19-antibodies/?form=MG0AV3 

[11] Embl-Ebi. (n.d.-a). Strengths and limitations of alphafold2. Strengths and limitations of AlphaFold2 | AlphaFold. https://www.ebi.ac.uk/training/online/courses/alphafold/an-introductory-guide-to-its-strengths-and-limitations/strengths-and-limitations-of-alphafold/ 

---

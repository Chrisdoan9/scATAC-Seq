## LSI 
LSI = TF-IDF + SVD  
Latent Semantic Indexing is a technique that:  
Finds hidden (latent) patterns and topics in a large matrix of data.  

Step 1: TF-IDF  
	•	TF = term frequency = how often a peak appears in a cell  
	•	IDF = inverse document frequency = how unique the peak is across all cells  
	•	TF-IDF boosts important peaks and reduces the weight of common, boring ones

 | Peak | Cell A | Cell B |
|-------|--------|--------|
| p1    |  1     | 1      |
| p2    |  1     | 0      |
| p3    |  1     | 0      |

TF for p1 in Cell A = 1 / 3 = 0.33  
TF for p2 in Cell A = 1 / 3 = 0.33  
TF for p1 in Cell B = 1 / 1 = 1.0  

IDF = log(total_cells / cells_with_peak)  

•	Peak p1 is in both cells → IDF = log(2/2) = 0  
•	Peak p2 is only in Cell A → IDF = log(2/1) ≈ 0.69  

So:  
	•	p1 = common = not informative → down-weighted  
	•	p2 = more specific = more informative → up-weighted

 TF-IDF = TF × IDF

 ## SVD in scATAC-seq: Biological Interpretation

| Matrix | Interpretation                                     |
|--------|----------------------------------------------------|
| **U**  | How strongly each **peak** contributes to components |
| **Σ**  | Importance of each component (**variance explained**) |
| **Vᵗ** | How each **cell** expresses those components         |  

A motif is a short DNA sequence pattern (e.g., “TATA” or “CGCG”) that a transcription factor (TF) prefers to bind.


Position Weight Matrix (PWM)
| Position | A    | C    | G    | T    |
|----------|------|------|------|------|
| 1        | 0.9  | 0.05 | 0.03 | 0.02 |
| 2        | 0.1  | 0.1  | 0.7  | 0.1  |
| 3        | 0.25 | 0.25 | 0.25 | 0.25 |
| 4        | 0.05 | 0.9  | 0.02 | 0.03 |

Use Precomputed PWMs from Databases (Most Common JASPAR)

I1, R1, R2, R3 fastq file  
R1 is forward read, R2 is 16 bases feature barcode, R3 is reverse read  
R1 or R3 only read part of the fragment from the start or end, not full, so we need pair end read to know the length and location of fragment.

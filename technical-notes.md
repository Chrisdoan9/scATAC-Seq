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

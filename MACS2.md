MACS2 (Model-based Analysis for ChIP-Seq)
| Step                  | What MACS2 Does                          |
|-----------------------|------------------------------------------|
| Model background      | Assumes random read distribution         |
| Count reads in windows| Slide along genome, count reads          |
| Score enrichment      | Compare observed vs expected reads       |
| Statistical testing   | Compute p-value and q-value              |
| Output peak list      | Report high-confidence enriched areas    |

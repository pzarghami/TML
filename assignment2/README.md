# TML26 — Stolen Model Detection

**Team:** team_XI
**Public leaderboard score:** 0.6667
**Final submission file:** `submission_max_plus_boundary.csv`

## Environment

- Kaggle notebook with GPU **T4 x2** accelerator
- `safetensors` and `huggingface_hub` (auto-installed by the first cell)

## How to reproduce

1. Open `assignment2F.ipynb` in Kaggle and enable the GPU T4 accelerator.
2. Run all cells top-to-bottom. Total runtime: ~25–30 minutes.
   - The target model and 360 suspect models download automatically from the `SprintML/tml26_task2` HuggingFace repo.
   - Cell "Score every suspect" writes incrementally to `features_v2.csv`.
   - Cell 'boundary probes + high-confidence SAC' writes to `features_v2_extras.csv`.
3. After the final cell runs, `submission_max_plus_boundary.csv` is written to `/kaggle/working/tml26_task2/` containing 360 rows with columns `id,score`.
4. To submit to the leaderboard, in the KNOBS cell set:
```python
   VARIANT = 'max_plus_boundary'
   SUBMIT  = True
   API_KEY = 'your-api-key-here'
```
   and re-run only that cell.
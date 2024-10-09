# bayesian-knowledge-tracing
Apply BKT on student's response to online text book.

## Dev Diary

### 2024-09-24
- [x] Try applying BKT on the `sample_sep.csv` data, which only contains students' responses for one __skill__. The analysis is in the `analysis/try_bkt.ipynb` notebook. The generated result is stored in `analysis/sample_sep_final_predictions.csv`, which contains the final correct probability and the predicted skill mastery for each student.


### 2024-09-30
- [x] Apply the processing on all 15 tables, each representing a different level 2 chapter. The input dataset is stored in `data/csv_sep30_24` (ignored by git due to size limit). The processing and analysis notebook is in `analysis_all/bkt.ipynb`. The final predictions are stored in `analysis/output/csv_sep30_24`.

### 2024-10-09
- [x] Apply the processing on a new dataset. The input data is stored in `data/csv_oct9_24` (ignored by git due to size limit). The processing and analysis notebook is in `analysis_all/bkt_oct9.ipynb`. The final predictions are stored in `analysis/output/output_oct9`.
- [x] Updated the processing script to skip on empty data (learning objective) or data without any student response.
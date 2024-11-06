# bayesian-knowledge-tracing
Apply BKT on student's response to online text book.

## Dev Diary

### 2024-09-24
- Try applying BKT on the `sample_sep.csv` data, which only contains students' responses for one __skill__. The analysis is in the `analysis/try_bkt.ipynb` notebook. The generated result is stored in `analysis/sample_sep_final_predictions.csv`, which contains the final correct probability and the predicted skill mastery for each student.

### 2024-09-30
- Apply the processing on all 15 tables, each representing a different level 2 chapter. The input dataset is stored in `data/csv_sep30_24` (ignored by git due to size limit). The processing and analysis notebook is in `analysis_all/bkt.ipynb`. The final predictions are stored in `analysis/output/csv_sep30_24`.

### 2024-10-09
- Apply the processing on a new dataset. The input data is stored in `data/csv_oct9_24` (ignored by git due to size limit). The processing and analysis notebook is in `analysis_all/bkt_oct9.ipynb`. The final predictions are stored in `analysis/output/output_oct9`.
- Updated the processing script to skip on empty data (learning objective) or data without any student response.

### 2024-10-15
- The data format changed so we created a new processing script to handle the new format. The new script is in `analysis_all/bkt_v2.ipynb`. The final predictions are stored in `analysis/output/output_oct15`.
- We found an issue in the dataset where the same response is repeated multiple times. We fixed this issue in the new processing script.
- Besides the predictions, we also generated a table for the coefficients of the BKT model. The table is stored in `analysis/output/output_oct15/coefs.csv`.
- Also added a test notebook for exploring the data, `analysis_all/test.ipynb`.

### 2024-10-21
- Process `code` questions differently with the following logic. For each student:
    - Always record the first attempt, no matter if it is correct or not.
    - If the first attempt is correct, no more records will be kept.
    - If the first attempt is incorrect, look for the first correct attempt if there is any. If found, keep the record and discard the rest. Otherwise, only keep the first incorrect attempt.
- `bkt_v2.ipynb` is updated to include the new processing logic. The final predictions are stored in `analysis/output/csv_oct15_24_simplify_coding_attempts`.


## 2024-10-28
- Test the metrics computation provided by the `pyBKT` package, it is computed on all the attempts. This might not be the best choice for us, becuase different students have different number of attempts, thus we're putting different weight on different students. Students with more attempts have more weight.
- In our evaluation, we compute the metrics on each student individually, then take the average. This is a fairer way to evaluate the model.
- The code is also updated to dump the model artifacts into a `/models` folder for future reuse. The folder is ignored by git due to size limit.
- Updated the title of the plots.
- Plot the metrics trend over the number of attempts. For given x (number of attempts), we plot the average metrics for all students that have at least x attempts.
- All evaluation code is in `analysis_all/eval.ipynb`.


## 2024-11-06
- Add processing notebooks and evaluation notebooks for level 3 learning objectives.
- For evaluation, we now also compute the metrics on the last attempt of each student.
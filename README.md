<p align="center">
  <img src="doc/conic_banner.png">
</p>

# CoNIC: Colon Nuclei Identification and Counting Challenge

In this repository we provide code and example notebooks to assist participants start their algorithm development for the CoNIC challenge. In particular we provide:

- Evaluation code
  - Segmentation & classification: multi-class panoptic quality
  - Predicting cellular composition: multi-class coefficient of determination ($R^2$)

Stay tuned for example notebooks and baseline results!

## Output format for metric calculation

To appropriately calculate the metrics, ensure that your output is in the following format:

- Instance Segmentation and classification map:
    - `.npy` array of size Nx256x256x2, where N is the number of processed patches.
    - First channel is the instance segmentation map containing values ranging from 0 (background) to n (number of nuclei).
    - Second channel is the classification map containing values ranging from 0 (background) to 6 (number of classes in the dataset).
  
- Composition prediction:
  - Single `.csv` file where the column headers should be:
    - `neutrophil`
    - `epithelial`
    - `lymphocyte`
    - `plasma`
    - `eosinophil`
    - `connective`
  - To make sure the calculation is done correctly, ensure that the row ordering is the same for both the ground truth and prediction csv files.

## Metric calculation
  To get the stats for segmentation and classification, run:

  ```
  python compute_stats.py --mode=seg_class --results=<path_to_results> --ground_truth=<path_to_ground_truth>
  ```
  
  To get the stats for cellular composition prediction, run:

  ```
  python compute_stats.py --mode=regression --results=<path_to_results> --ground_truth=<path_to_ground_truth>
  ```

  


# README

## Ocular Disease Recognition: Feature Fusion and Multi-Modality Analysis

Ocular diseases, like diabetic retinopathy, glaucoma, and age-related macular degeneration, are key causes of global blindness, emphasizing the critical need for early detection and treatment. While deep learning-based automated screening shows promise, addressing patients with multiple conditions remains a challenge. This study investigates multi-label ocular disease classification using the OIA-ODIR dataset, integrating binocular fundus images and patient demographics. Through diverse fusion techniques and model architectures, including late and early fusion strategies, ResNet-18 performance in multi-label tasks is evaluated. Late fusion methods, particularly fundus image-only fusion with element-wise summation, demonstrated superior classification performance. These findings highlight the importance of adapting fusion techniques to dataset characteristics, offering vital insights for optimizing automated ocular disease recognition systems.

Homepage of ODIR challenge: https://odir2019.grand-challenge.org/

The data (annotations and images) can be downloaded from GitHub: https://github.com/nkicsl/OIA-ODIR?tab=readme-ov-file

Before running any of jupyter notebook files below **update all hard encoded file paths to personal file path**. Run the files in the following order:

1. **Data Preprocessing**: [`Data Preprocessing.ipynb`]
   * Prepares datasets for a ocular disease recognition task
   * Loads dataframes for train, validation, and test sets, converts classifications to binary vectors, drops unnecessary columns, and filters instances with three or more classes
   * Creates random subsets for hyperparameter tuning and performs one-hot encoding for the 'Patient Sex' column
   * Processed datasets are saved as CSV files
2. **Hyperparameter Tuning**: [`Hyperparameter Tuning.ipynb`]
   * Includes data preprocessing steps such as loading datasets, applying transformations, and creating a custom dataset class
   * Late Fusion (Sum Method) model using a ResNet18 architecture is defined
   * Training function is implemented to train the model with various hyperparameters for batch size and learning rate
   * Visualizes training and validation losses for different learning rates and batch sizes
3. **Image-Only Models Training**: [`Image Only Models.ipynb`]
   * Includes data preprocessing steps such as loading datasets, applying transformations, creating a custom dataset class, and defining the following model architectures:
   * Model 1: Image Late Fusion (Sum Fusion Method)
   * Model 2: Image Late Fusion (Concatenation Fusion Method)
   * Model 3: Image Late Fusion (Product Fusion Method)
   * Model 4: Image Early Fusion (Sum Fusion Method)
   * Model 5: Image Early Fusion (Concatenation Fusion Method)
   * Model 6: Image Early Fusion (Product Fusion Method)
   * Training function is implemented to train the models with tuned batch size and learning rate parameters
   * Best models are saved based on highest macro F1 score over the 10 epochs
4. **Multi-Modality Models Training**: [`Image and Tabular Models.ipynb`]
   * Includes data preprocessing steps such as loading datasets, applying transformations, creating a custom dataset class, and defining the following model architectures:
   * Model 1: Image Late Fusion (Sum Fusion Method) + Concatenate Patient Age and Sex
   * Model 2: Image Late Fusion (Concatenation Fusion Method) + Concatenate Patient Age and Sex
   * Model 3: Image Late Fusion (Product Fusion Method) + Concatenate Patient Age and Sex
   * Model 4: Image Early Fusion (Sum Fusion Method) + Concatenate Patient Age and Sex
   * Model 5: Image Early Fusion (Concatenation Fusion Method) + Concatenate Patient Age and Sex
   * Model 6: Image Early Fusion (Product Fusion Method) + Concatenate Patient Age and Sex
   * Training function is implemented to train the models with tuned batch size and learning rate parameters
   * Best models are saved based on highest macro F1 score over the 10 epochs
5. **Data Analysis and Visualizations**: [`Image Only Data Analysis.ipynb`][`Image and Tabular Data Analysis.ipynb`][`Comparison Heatmaps.ipynb`]
   * Best models from steps 4 and 5 are loaded for evaluation
   * Kappa, macro F1, macro AUC, per-class AUC, and final scores are computed
   * Visualizes ROC curves, training/validation loss plots, as well as comparative score heatmaps


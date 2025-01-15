# Clinical Genomics - AI Powered Early Stage Cancer Screening

### **Team:**
Catharina Hente, Polina Ivanova  
**Mentor:** Arvid Gollwitzer  
**Duration:** 14 weeks  

## **Problem Statement**
Cancer is among the leading causes of death worldwide, with colorectal cancer (CRC) being one of the most frequently occurring types. Early-stage diagnosis is often key to preventing the disease from spreading. New technologies such as artificial intelligence (AI) should be implemented to aid medical professionals in diagnosis as well as in the selection of patients prone to disease for more rigorous screenings.

## **Goal**
The goal of this project is to implement and train an efficient machine learning algorithm to predict whether a patient has CRC based on the patient's gut microbiome data.

---

## **Repository Structure**

### **1. Folder: `methods analysis`**
This folder contains our initial analysis of the methods and datasets used in the provided studies. It includes our first steps in the selection of methods and datasets to use for training the machine learning model. The analysis is focused on identifying relevant features and eliminating unnecessary data.

### **2. Folder: `code from study #1`**
This folder contains the original R code from Study #1 and our translated version of that code in Python. We have adapted the original code to ensure compatibility with our chosen dataset and machine learning approach.

### **3. Folder: `code from study #3`**
Similar to the previous folder, this contains the original R code from Study #3 along with our Python translation. While the original code was not used directly in our final pipeline, it served as a valuable reference for data preparation techniques.

### **4. Folder: `data`**
The `data` folder contains the dataset that we have chosen to use for training our machine learning model, specifically from Study #1. Below is a breakdown of the contents:

- **`XGBoost.ipynb`**: The main Jupyter Notebook where we implemented the XGBoost algorithm.
- **`data_visualisation_study_1.ipynb`**: A notebook focused on exploratory data analysis and visualization.
- **`dataset/`**: The raw dataset from Study #1.
- **Taxonomic profiles:**
  - `mpa4_class.profile`
  - `mpa4_family.profile`
  - `mpa4_genus.profile`
  - `mpa4_order.profile`
  - `mpa4_phylum.profile`
  - `mpa4_species.profile`
- **`sample.group`**: Metadata file that links samples to their respective patient groups.
- **`wine-quality-red.arff`**: A placeholder dataset used for initial testing of our ML pipeline.
- **`xgboost_trial.ipynb` & `xgboost_try_2.ipynb`**: Notebooks containing earlier iterations of our model training experiments.

---

## **Execution Instructions**

### **Setup Environment**
1. Clone this repository to your local machine.
```bash
$ git clone https://github.com/CatharinaHente/Clinical_Genomics.git
$ cd Clinical_Genomics
```
2. Create a virtual environment and activate it:
```bash
$ python3 -m venv venv
$ source venv/bin/activate
```
3. Install the required dependencies:
```bash
$ pip install -r requirements.txt
```

### **Running the XGBoost Model**
1. Navigate to the `data` folder:
```bash
$ cd data
```
2. Open the `XGBoost.ipynb` notebook in your preferred Jupyter environment (VS Code, Jupyter Lab, etc.):
```bash
$ jupyter notebook XGBoost.ipynb
```
3. Run the cells step-by-step to:
   - Load and preprocess the dataset.
   - Train the XGBoost model.
   - Evaluate the model's performance.

### **Data Preprocessing Steps**
- The gut microbiome data from the chosen study was extremely sparse. We had to apply several preprocessing steps, including:
  - Filtering out rare species.
  - Normalizing the dataset.
  - Splitting the data into training and testing sets.

---

## **Results**
We successfully trained an XGBoost model to predict CRC status based on gut microbiome data. Due to the sparsity of the dataset and the limited number of CRC-positive samples, we initially encountered challenges in model performance. However, by reducing the dataset size and focusing on key features, we were able to achieve improved results.

### **Performance Metrics (Initial Trial):**
- **Accuracy:** 1.00
- **Precision:** Undefined for CRC positives due to lack of predictions.
- **Recall:** 0.00 for CRC positives.
- **F1 Score:** Undefined for CRC positives.

These initial results showed that the dataset was highly imbalanced, making it difficult for the model to correctly predict CRC-positive cases.

### **Performance Metrics (Final Trial - Reduced Dataset):**
- **Accuracy:** 0.86
- **Precision:** 0.89 for non-CRC, 0.80 for CRC.
- **Recall:** 0.89 for non-CRC, 0.80 for CRC.
- **F1 Score:** 0.89 for non-CRC, 0.80 for CRC.

These final metrics indicate that our model improved significantly when focusing on a smaller, more balanced subset of the data.

---

## **Challenges and Limitations**
- **Sparse Data:** The dataset contained very few CRC-positive samples, making it difficult to train a robust model.
- **Taxonomic Levels:** We experimented with various taxonomic levels (species, genus, etc.) but found that higher-level profiles tended to generalize better.
- **Computational Resources:** Training the model on larger datasets or more complex models would require additional computational power.

---

## **Future Improvements**
1. **Larger Dataset:** One of our primary goals for the future is to train the model on a larger, more comprehensive dataset with more CRC-specific patient data.
2. **Feature Engineering:** Further feature selection and engineering could help improve the model's performance.
3. **Model Optimization:** Tuning the hyperparameters of the XGBoost model to optimize performance.
4. **Additional Machine Learning Techniques:** Exploring other machine learning algorithms (e.g., Random Forest, Neural Networks) to see if they outperform XGBoost on this dataset.
5. **Incorporating Clinical Data:** Including additional clinical data (e.g., age, BMI, family history) as features in the model.

---

## **Reading Materials**
- Sun, W., Zhang, Y., Guo, R. Et al. A population-scale analysis of 36 gut microbiome studies reveals universal species signatures for common diseases. *Npj Biofilms Microbiomes* 10, 96 (2024). https://doi.org/10.1038/s41522-024-00567-9
- Qin, Y., Tong, X., Mei, WJ. et al. Consistent signatures in the human gut microbiome of old- and young-onset colorectal cancer. *Nat Commun* 15, 3396 (2024). https://doi.org/10.1038/s41467-024-47523-x
- Tito, R.Y., Verbandt, S., Aguirre Vazquez, M. et al. Microbiome confounders and quantitative profiling challenge predicted microbial targets in colorectal cancer development. *Nat Med* 30, 1339–1348 (2024). https://doi.org/10.1038/s41591-024-02963-2
- Adlung, L., Elinav, E., Greten, T.F. et al. Microbiome genomics for cancer prediction. *Nat Cancer* 1, 379–381 (2020). https://doi.org/10.1038/s43018-020-0059-x
- Elinav, E., Garrett, W.S., Trinchieri, G. et al. The cancer microbiome. *Nat Rev Cancer* 19, 371–376 (2019). https://doi.org/10.1038/s41568-019-0155-3
- XGBoost Documentation — xgboost 2.1.3 documentation. *Readthedocs.io*. Published 2022. Accessed January 15, 2025. https://xgboost.readthedocs.io/en/stable/
- What is XGBoost? *NVIDIA Data Science Glossary*. Published 2019 https://www.nvidia.com/en-us/glossary/xgboost/


# AI Programming Foundations Project

This project builds a complete, reproducible data workflow using Python. It loads the Titanic dataset, cleans and transforms the data, performs exploratory analysis, creates visualizations, and communicates findings in a written summary with academic citations.

**Dataset:** Titanic - Machine Learning from Disaster (https://www.kaggle.com/c/titanic/data)

## How to Run

1. Clone this repository
2. Set up the environment with [uv](https://docs.astral.sh/uv/):
   ```bash
   uv sync
   ```
3. Open and run the notebook:
   ```bash
   uv run jupyter notebook data_workflow.ipynb
   ```
4. Alternatively, install dependencies manually:
   ```bash
   pip install -r requirements.txt
   jupyter notebook data_workflow.ipynb
   ```

## Bias Awareness

Poor data cleaning could introduce bias in this dataset in several ways. Filling missing Age values with group medians may mask socioeconomic variation in age distributions across passenger classes. Dropping the Cabin column removes deck-location information that is correlated with both class and survival, potentially hiding structural advantages certain passengers had during evacuation. The training set represents only a subset of all passengers and crew, so results may reflect survivorship bias rather than the full population.

## Future Integration Reflections

### How would this workflow change for an ML project?

For machine learning, the workflow would extend beyond EDA to include feature engineering (encoding categorical variables, scaling numeric features, creating interaction terms), train-test splitting, model selection and training, hyperparameter tuning, and evaluation using metrics such as accuracy, precision, and recall. The data pipeline would also need to handle the test set consistently with the same cleaning transformations.

### What would need to change for neural network input?

Neural networks require all inputs to be numeric and normalized. Categorical features like Sex and Embarked would need one-hot or label encoding. Numeric features like Age and Fare would need scaling (e.g., StandardScaler or MinMaxScaler). The data would be converted to tensors, and the dataset might need batching via a DataLoader for efficient training.

### What parts could be automated by an AI agent?

An AI agent could automate data profiling (detecting missing values, outliers, and data types), suggest and apply appropriate cleaning strategies based on detected patterns, generate visualizations automatically, and draft initial EDA summaries. An agent could also monitor the pipeline for data drift, validate schema consistency across runs, and flag potential bias in feature distributions.

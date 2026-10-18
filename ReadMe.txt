# Nagpur Plot Price Predictor

A machine learning project that estimates the total price of a plot in Nagpur based on its locality, plot category, and area in square feet.

The project compares four regression algorithms, including a manually implemented Linear Regression model and three models from Scikit-learn. It also includes a Gradio interface that allows users to enter plot details and receive a predicted price.

## Project Objectives

- Build a machine learning model to estimate plot prices.
- Perform data inspection, preprocessing, and train-test splitting.
- Implement Linear Regression manually using NumPy.
- Compare multiple regression algorithms using evaluation metrics.
- Visualize model performance and select a model based on the results.
- Create a simple user interface for making predictions.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Joblib
- Gradio
- Google Colab / Jupyter Notebook

## Dataset Description

The project uses a CSV dataset containing 3,000 records and seven columns.

| Column | Description |
|---|---|
| `Record_ID` | Unique record identifier |
| `Locality` | Locality of the plot in Nagpur |
| `Plot_Category` | Normal Location, High Location, or Prime Location |
| `Area_SqFt` | Plot area in square feet |
| `Rate_Per_SqFt_INR` | Rate per square foot in Indian rupees |
| `Estimated_Total_Price_INR` | Estimated total plot price in Indian rupees |
| `Data_Type` | Indicates the type of dataset record |

The dataset contains 20 localities and three plot categories.

**Data limitation:** The dataset is synthetic. The project demonstrates a machine learning workflow, and its predictions should not be interpreted as verified market prices or professional real-estate valuations.

## Features Used for Prediction

The model uses three input features:

- `Locality`
- `Plot_Category`
- `Area_SqFt`

The target variable is `Estimated_Total_Price_INR`.

`Record_ID`, `Rate_Per_SqFt_INR`, and `Data_Type` are excluded from the model inputs. In particular, excluding the rate per square foot helps avoid giving the model a value that may directly determine the target price.

## Machine Learning Algorithms

Four regression models are compared:

1. **Manual Linear Regression** — implemented using a custom Python class and NumPy's least-squares solver.
2. **Decision Tree Regressor** — implemented using Scikit-learn.
3. **Random Forest Regressor** — implemented using Scikit-learn with 100 trees.
4. **Gradient Boosting Regressor** — implemented using Scikit-learn.

The manually implemented Linear Regression model includes its own `fit()` and `predict()` methods. The other three algorithms use Scikit-learn's implementations.

## Project Workflow

1. Load the CSV dataset using Pandas.
2. Inspect the dataset's dimensions, column types, missing values, and duplicate rows.
3. Select the input features and target variable.
4. Apply one-hot encoding to categorical features.
5. Split the data into training and testing sets using an 80:20 ratio.
6. Train the four regression models.
7. Evaluate their predictions using MAE, RMSE, and R².
8. Visualize model performance using Matplotlib.
9. Select the best-performing model based on the evaluation results.
10. Save the trained model and feature-column information using Joblib.
11. Use Gradio to create an interface for price prediction.

## Model Evaluation

The models are evaluated using three metrics.

- **Mean Absolute Error (MAE):** Measures the average absolute difference between actual and predicted prices. Lower is better.
- **Root Mean Squared Error (RMSE):** Measures prediction error while giving more weight to larger mistakes. Lower is better.
- **R² Score:** Measures performance relative to a baseline that predicts the mean target value. Higher is generally better.

The notebook generates a comparison table and an RMSE bar chart. The final model is selected from the observed results rather than assuming that one algorithm will always perform best.

Actual evaluation values should be recorded in this section after running the notebook.

## User Interface

The project uses Gradio to provide a simple interface with:

- A locality dropdown
- A plot category dropdown
- A plot area input
- A predicted price output

The interface loads the saved model, preprocesses the user's input, aligns the features with the training columns, and displays the estimated total price in Indian rupees.

A Gradio share link launched from Google Colab is temporary and depends on the notebook session remaining active.

## How to Run the Project

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd <YOUR_REPOSITORY_FOLDER>
```

Replace the placeholders with your actual repository URL and folder name.

### 2. Install the dependencies

```bash
pip install pandas numpy matplotlib scikit-learn joblib gradio
```

### 3. Open the notebook

Open the `.ipynb` notebook in Google Colab or Jupyter Notebook.

### 4. Upload the dataset

Make sure `plot_data.csv` is available at the path expected by the notebook.

### 5. Run the notebook cells in order

Run the cells to inspect and preprocess the dataset, train and evaluate the models, compare their results, and save the selected model.

### 6. Launch the interface

Run the Gradio section after the model file has been created. In Google Colab, the interface can generate a temporary share link.

## Project Structure

A possible repository structure is:

```text
Nagpur-Plot-Price-Predictor/
├── notebook.ipynb
├── plot_data.csv
├── nagpur_plot_price_model.pkl
├── requirements.txt
├── README.md
└── screenshots/
    └── prediction_interface.png
```

Include only the files that actually exist in your repository. If the dataset or model file is not included, explain how to obtain or generate it.

## Limitations

- The dataset is synthetic and may not reflect actual Nagpur property prices.
- The model learns patterns from the provided dataset and may not generalize to real-world property markets.
- The prediction depends on the selected features and the quality of the training data.
- The project does not account for every factor that affects real-estate prices, such as legal status, road access, nearby facilities, or changing market conditions.
- A temporary Gradio share link is not a permanent deployment.

## Future Improvements

- Train and evaluate the models using reliable real-world property data.
- Improve preprocessing using a Scikit-learn pipeline.
- Tune model hyperparameters and compare the results.
- Add more useful property features where reliable data is available.
- Deploy the interface on a persistent hosting platform.
- Add automated tests and improve input validation.

## Conclusion

The Nagpur Plot Price Predictor demonstrates the end-to-end process of building a regression-based machine learning application, from dataset inspection and preprocessing to model comparison, evaluation, saving the trained model, and creating a user interface.

It also demonstrates the difference between manually implementing a machine learning algorithm and using an established library implementation.

The project is intended for educational purposes and should not be used as the sole basis for real-estate purchasing or valuation decisions.

## References

- Pandas: https://pandas.pydata.org/docs/
- NumPy: https://numpy.org/doc/
- Scikit-learn: https://scikit-learn.org/stable/
- Matplotlib: https://matplotlib.org/stable/
- Joblib: https://joblib.readthedocs.io/
- Gradio: https://www.gradio.app/docs/

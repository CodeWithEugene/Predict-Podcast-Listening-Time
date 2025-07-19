<!-- Banner & Badges -->
<p align="center">
    <img src="https://komarev.com/ghpvc/?username=Predict-Podcast-Listening-Time&label=Repo%20views&color=blue&style=flat" alt="repo views" />
    <img src="https://img.shields.io/github/stars/CodeWithEugene/Predict-Podcast-Listening-Time?label=Stars&style=flat&color=yellow" alt="stars" />
    <img src="https://img.shields.io/github/forks/CodeWithEugene/Predict-Podcast-Listening-Time?label=Forks&style=flat&color=brightgreen" alt="forks" />
    <img src="https://img.shields.io/badge/ML%20Model-Gradient%20Boosting-blueviolet?style=flat" alt="model" />
    <img src="https://img.shields.io/badge/Dataset%20Size-1M%2B%20Rows-orange?style=flat" alt="dataset size" />
    <img src="https://img.shields.io/badge/Accuracy-12.9%20RMSE-lightgrey?style=flat" alt="accuracy" />
</p>

<h1 align="center">🎧 Predict Podcast Listening Time</h1>

<p align="center">
    <em>
        Predict how long users will listen to podcast episodes using machine learning.<br>
        Powered by gradient boosting and a rich, 1M+ row dataset.
    </em>
</p>

---

<h2 align="center">📋 Table of Contents</h2>

<p align="center">
    <a href="#dataset-description">Dataset Description</a> •
    <a href="#features">Features</a> •
    <a href="#project-structure">Project Structure</a> •
    <a href="#installation--setup">Installation & Setup</a> •
    <a href="#data-preprocessing">Data Preprocessing</a> •
    <a href="#model-building">Model Building</a> •
    <a href="#results">Results</a> •
    <a href="#future-improvements">Future Improvements</a>
</p>

---

<h2 align="center">📝 Project Overview</h2>

<p align="center">
    This project predicts the amount of time (in minutes) users spend listening to podcast episodes, leveraging features like episode length, genre, host popularity, and more.<br>
    Machine learning techniques, especially gradient boosting, drive the predictions.
</p>

---

<h2 align="center">📂 Dataset Description</h2>

<ul>
    <li><code>train.csv</code>: 750,000 rows with features & target variable</li>
    <li><code>test.csv</code>: 250,000 rows with features only</li>
    <li><code>sample_submission.csv</code>: Submission format</li>
</ul>

---

<h2 align="center">🔑 Features</h2>

<table align="center">
    <thead>
        <tr>
            <th>Feature</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr><td>Podcast_Name</td><td>Name of the podcast</td></tr>
        <tr><td>Episode_Title</td><td>Title of the episode</td></tr>
        <tr><td>Episode_Length_minutes</td><td>Duration in minutes</td></tr>
        <tr><td>Genre</td><td>Podcast category (e.g., True Crime, Comedy, Education)</td></tr>
        <tr><td>Host_Popularity_percentage</td><td>Popularity score of host(s)</td></tr>
        <tr><td>Publication_Day</td><td>Day of the week published</td></tr>
        <tr><td>Publication_Time</td><td>Time of day published (Morning, Afternoon, Evening, Night)</td></tr>
        <tr><td>Guest_Popularity_percentage</td><td>Popularity score of guests</td></tr>
        <tr><td>Number_of_Ads</td><td>Number of ads in episode</td></tr>
        <tr><td>Episode_Sentiment</td><td>Overall sentiment (Positive, Negative, Neutral)</td></tr>
        <tr><td>Listening_Time_minutes</td><td><b>Target:</b> Actual listening time</td></tr>
    </tbody>
</table>

---

<h2 align="center">📁 Project Structure</h2>

```text
Predict-Podcast-Listening-Time/
├── train.csv                  # Training dataset
├── test.csv                   # Test dataset
├── sample_submission.csv      # Sample submission format
├── submission.csv             # Final predictions for submission
├── README.md                  # Project documentation
└── notebook.ipynb             # Jupyter notebook with analysis and modeling
```

---

<h2 align="center">⚙️ Installation & Setup</h2>

```bash
# Clone the repository
git clone https://github.com/CodeWithEugene/Predict-Podcast-Listening-Time.git
cd Predict-Podcast-Listening-Time

# Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install required packages
pip install -r requirements.txt
```

<details>
    <summary><b>Required packages</b></summary>

    ```
    pandas
    numpy
    scikit-learn
    xgboost
    lightgbm
    catboost
    matplotlib
    seaborn
    category_encoders
    ```
</details>

---

<h2 align="center">🧹 Data Preprocessing</h2>

<ol>
    <li><b>Handling Missing Values</b>
        <ul>
            <li>Numerical: filled with median</li>
            <li>Categorical: filled with mode</li>
        </ul>
    </li>
    <li><b>Feature Engineering</b>
        <ul>
            <li>Encoded categorical variables using Target Encoder</li>
        </ul>
    </li>
</ol>

---

<h2 align="center">🤖 Model Building</h2>

<ul>
    <li><b>Cross-Validation:</b> KFold (3 splits), seed=42</li>
    <li><b>Model:</b> XGBoost Regressor</li>
    <li><b>Parameters:</b>
        <pre>
xgb_params = {
         'n_estimators': 300,
         'max_depth': 14,
         'learning_rate': 0.04222221,
         'subsample': 0.8,
         'colsample_bytree': 0.8,
         'random_state': 42,
         'tree_method': 'hist',
         'n_jobs': -1
}
        </pre>
    </li>
    <li><b>Metric:</b> Root Mean Squared Error (RMSE)</li>
</ul>

---

<h2 align="center">🏆 Results</h2>

<ul>
    <li><b>Cross-validated RMSE:</b> 12.900 ± 0.009</li>
    <li><b>Maximum RMSE:</b> 12.910</li>
    <li><b>Minimum RMSE:</b> 12.887</li>
</ul>

---

<h2 align="center">🌟 Feature Importance</h2>

<ul>
    <li>Episode length</li>
    <li>Host popularity</li>
    <li>Genre</li>
    <li>Number of ads</li>
</ul>

---

<h2 align="center">📊 Visualizations</h2>

<p align="center">
    <img src="images/image.png" alt="Model Results Visualization" width="900"/>
</p>

<ul>
    <li><b>Feature Importance (top left):</b> Most influential features</li>
    <li><b>Actual vs. Predicted (top right):</b> Scatter plot of true vs. predicted listening times</li>
    <li><b>Residual Distribution (bottom left):</b> Histogram of prediction errors</li>
    <li><b>Test Predictions Distribution (bottom right):</b> Predicted listening times on test set</li>
</ul>

---

<h2 align="center">🚀 Future Improvements</h2>

<ol>
    <li>Try different ML algorithms (Neural Networks, Ensembles)</li>
    <li>More feature engineering & selection</li>
    <li>Extensive hyperparameter tuning</li>
    <li>Add text features from <code>Episode_Title</code> using NLP</li>
    <li>Explore feature interactions (e.g., Genre × Publication_Day)</li>
</ol>

---

<p align="center">
    <sub>Created by <a href="https://eugeniuss.netlify.app/">Eugene Mutembei</a></sub>
</p>

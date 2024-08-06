Amazon Product Review Sentiment Analysis
=========================================

Overview
--------

This project classifies Amazon product reviews into three sentiment categories: positive, negative, or neutral, aiming to provide actionable insights for e-commerce businesses.

Key Findings
------------

- **Model Performance:**
  - **DistilBERT:** Outperforms traditional models (Logistic Regression, Random Forest, XGBoost) in accuracy and recall, particularly for neutral and positive sentiments.
  - **Statistical Models:** Struggle with neutral sentiment classification. Random Forest and XGBoost show low recall for neutral sentiments.

- **Resource Efficiency:**
  - **DistilBERT:** More resource-efficient compared to BERT, making it suitable for the project's constraints.
  - **BERT:** Offers superior performance but requires more computational resources.

Practical Considerations
------------------------

- **Resource Management:** Advanced models like BERT need high computational resources; DistilBERT is a practical alternative.
- **Neutral Sentiments:** Advanced models like BERT handle neutral sentiments better than statistical models.
- **Feature Learning:** Advanced models reduce the need for manual feature engineering, improving performance and reducing preprocessing efforts.

Future Work
-----------

- **Explore Models:** Benchmark T5, GPT, XLNet for improved accuracy.
- **Expand Data Sources:** Include reviews from various e-commerce platforms.
- **Improve Neutral Classification:** Develop techniques for better classification of neutral sentiments.
- **Investigate Features:** Examine additional features for enhanced model performance.

Recommendations
----------------

- **Adopt DistilBERT:** For a balance of accuracy and computational efficiency.
- **Transition to Advanced NLP:** Implement BERT for nuanced sentiment classification.
- **Scale Data:** Increase dataset size for improved performance.

Model Comparison
----------------

### Performance Metrics

+-------------------------+----------+----------------------+-------------------+---------------------+---------------------+------------------+--------------------+----------------------+-------------------+---------------------+---------------------+---------------------+
| Model                   | Accuracy | Precision (Negative) | Recall (Negative) | F1-Score (Negative) | Precision (Neutral) | Recall (Neutral) | F1-Score (Neutral) | Precision (Positive) | Recall (Positive) | F1-Score (Positive) | Training Data Size |
+=========================+==========+======================+===================+=====================+=====================+==================+====================+======================+===================+=====================+=====================+---------------------+
| Logistic Regression     | 0.69     | 0.69                 | 0.82              | 0.75                | 0.45                | 0.17             | 0.25               | 0.74                 | 0.83              | 0.78                | 761K                |
+-------------------------+----------+----------------------+-------------------+---------------------+---------------------+------------------+--------------------+----------------------+-------------------+---------------------+---------------------+---------------------+
| Random Forest           | 0.68     | 0.66                 | 0.84              | 0.74                | 0.49                | 0.08             | 0.13               | 0.72                 | 0.82              | 0.77                | 761K                |
+-------------------------+----------+----------------------+-------------------+---------------------+---------------------+------------------+--------------------+----------------------+-------------------+---------------------+---------------------+---------------------+
| XGBoost                 | 0.70     | 0.70                 | 0.83              | 0.76                | 0.48                | 0.16             | 0.29               | 0.75                 | 0.82              | 0.79                | 200K                |
+-------------------------+----------+----------------------+-------------------+---------------------+---------------------+------------------+--------------------+----------------------+-------------------+---------------------+---------------------+---------------------+
| BERT (Fine-tuned)       | 0.80     | 0.82                 | 0.86              | 0.84                | 0.55                | 0.49             | 0.52               | 0.88                 | 0.89              | 0.89                | 200K                |
+-------------------------+----------+----------------------+-------------------+---------------------+---------------------+------------------+--------------------+----------------------+-------------------+---------------------+---------------------+---------------------+
| DistilBERT (Fine-tuned) | 0.78     | 0.78                 | 0.88              | 0.83                | 0.52                | 0.39             | 0.45               | 0.88                 | 0.87              | 0.87                | 400K                |
+-------------------------+----------+----------------------+-------------------+---------------------+---------------------+------------------+--------------------+----------------------+-------------------+---------------------+---------------------+---------------------+
| DistilBERT (Fine-tuned) | 0.82     | 0.83                 | 0.89              | 0.86                | 0.61                | 0.51             | 0.55               | 0.91                 | 0.91              | 0.91                | 761K                |
+-------------------------+----------+----------------------+-------------------+---------------------+---------------------+------------------+--------------------+----------------------+-------------------+---------------------+---------------------+---------------------+

### Hardware, Time, and Model Size

+------------------------------+--------------------------+------------------+------------+
| Model                        | Hardware                 | Training Time    | Model Size |
+==============================+==========================+==================+============+
| Logistic Regression 761K     | Intel i7 16-Core CPU     | ~4 Minutes       | 237KB      |
+------------------------------+--------------------------+------------------+------------+
| Random Forest 761K           | Intel i7 16-Core CPU     | ~1.0 Hour        | 8.9GB      |
+------------------------------+--------------------------+------------------+------------+
| XGBoost 200K                 | Intel i7 16-Core CPU     | ~2.4 Hours       | 1752KB     |
+------------------------------+--------------------------+------------------+------------+
| BERT (Fine-tuned) 200K       | Nvidia L4 24GB GPU       | ~9.5 Hours       | 418MB      |
+------------------------------+--------------------------+------------------+------------+
| DistilBERT (Fine-tuned) 400K | Nvidia A100 48GB GPU     | ~4.2 Hours       | 256MB      |
+------------------------------+--------------------------+------------------+------------+
| DistilBERT (Fine-tuned) 761K | Nvidia A100 48GB GPU     | ~7.0 Hours       | 256MB      |
+------------------------------+--------------------------+------------------+------------+

Feature Importance
-------------------

Top 20 important features for the XGBoost model:

+------------------+-------------+
| Feature          | Importance  |
+------------------+-------------+
| sentiment_score  | 0.004588    |
+------------------+-------------+
| loves            | 0.004333    |
+------------------+-------------+
| waste            | 0.003470    |
+------------------+-------------+
| returned         | 0.003289    |
+------------------+-------------+
| stopped          | 0.003263    |
+------------------+-------------+
| highly           | 0.003110    |
+------------------+-------------+
| cheaply          | 0.002939    |
+------------------+-------------+
| ok               | 0.002921    |
+------------------+-------------+
| refund           | 0.002784    |
+------------------+-------------+
| junk             | 0.002775    |
+------------------+-------------+
| body             | 0.002758    |
+------------------+-------------+
| broke            | 0.002696    |
+------------------+-------------+
| return           | 0.002677    |
+------------------+-------------+
| okay             | 0.002595    |
+------------------+-------------+
| love             | 0.002569    |
+------------------+-------------+
| perfect          | 0.002529    |
+------------------+-------------+
| trash            | 0.002487    |
+------------------+-------------+
| cheap            | 0.002486    |
+------------------+-------------+
| money            | 0.002478    |
+------------------+-------------+
| complaint        | 0.002397    |
+------------------+-------------+

Tools and Technologies
-----------------------

- **PySpark:** Used for scalable data processing and feature engineering.
- **Google Colab:** Facilitated GPU-supported model training and testing.
- **Hugging Face Transformers:** Enabled the use of pre-trained models like BERT and DistilBERT.

Conclusion
----------

Advanced NLP models like DistilBERT offer significant improvements over traditional methods. Future work includes exploring additional models, expanding data sources, and enhancing sentiment classification techniques.

For detailed analysis and additional information, please refer to the `Final Report` (link-to-final-report).

License
-------

This project is licensed under the MIT License. See the `LICENSE` file for details.

Free software: MIT license Documentation: https://sentiment-amazon-review.readthedocs.io.

Credits
--------

This package was created with Cookiecutter and the audreyr/cookiecutter-pypackage project template.

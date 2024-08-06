========================================
Amazon Product Review Sentiment Analysis
========================================

# Sentiment Analysis for Amazon Product Reviews

## Overview

This project focuses on classifying Amazon product reviews into three sentiment categories: positive, negative, or neutral. By analyzing these reviews, the goal is to provide actionable insights that can help e-commerce businesses improve their products, enhance customer service, and refine marketing strategies.

## Key Findings

- **Model Performance:**
  - **DistilBERT:** Outperforms traditional statistical models (Logistic Regression, Random Forest, XGBoost) in accuracy and recall, especially for neutral and positive sentiments. Offers a good balance between performance and computational efficiency.
  - **Statistical Models:** Struggle significantly with neutral sentiment classification. For example, Random Forest and XGBoost show very low recall for neutral sentiments.

- **Resource Efficiency:**
  - **DistilBERT:** Efficient in terms of computational resources compared to BERT, making it a practical choice for the project's needs.
  - **BERT:** While offering superior performance, it requires more computational resources.

## Practical Considerations

- **Resource Management:** Advanced models like BERT require high computational resources. DistilBERT is a more resource-efficient alternative that fits within the project’s constraints.
- **Neutral Sentiments:** Statistical models face challenges in classifying neutral sentiments effectively. Models with advanced contextual understanding, like BERT, handle these better.
- **Feature Learning:** Advanced models automatically learn features from data, reducing the need for extensive manual feature engineering. This improves model performance and reduces preprocessing efforts.

## Future Work

- **Explore Additional Models:** Test and benchmark other state-of-the-art models such as T5, GPT, and XLNet to explore opportunities for improving classification accuracy.
- **Expand Data Sources:** Collect and analyze reviews from various e-commerce platforms beyond Amazon to enhance the dataset and improve model generalization.
- **Improve Neutral Sentiment Classification:** Develop new techniques and approaches for better classification of neutral sentiments, potentially incorporating advanced NLP methods.
- **Investigate New Features:** Examine additional data features, such as subscription information, which could provide more insights and enhance model performance.

## Recommendations

- **Adopt DistilBERT:** Leverage DistilBERT for a balanced approach to accuracy and computational efficiency. It meets the project's requirements while managing resource constraints effectively.
- **Transition to Advanced NLP Techniques:** Implement BERT to capitalize on its superior contextual understanding and improve sentiment classification, especially for nuanced sentiments.
- **Scale Data for Better Performance:** Increase the dataset size to enhance model performance and better capture the subtleties of sentiment analysis.

## Model Comparison

### Performance Metrics

| Model                    | Accuracy | Precision (Negative) | Recall (Negative) | F1-Score (Negative) | Precision (Neutral) | Recall (Neutral) | F1-Score (Neutral) | Precision (Positive) | Recall (Positive) | F1-Score (Positive) | Training Data Size |
|--------------------------|----------|----------------------|-------------------|---------------------|---------------------|------------------|--------------------|----------------------|-------------------|---------------------|---------------------|
| Logistic Regression      | 0.69     | 0.69                 | 0.82              | 0.75                | 0.45                | 0.17             | 0.25               | 0.74                 | 0.83              | 0.78                | 761K                |
| Random Forest            | 0.68     | 0.66                 | 0.84              | 0.74                | 0.49                | 0.08             | 0.13               | 0.72                 | 0.82              | 0.77                | 761K                |
| XGBoost                  | 0.70     | 0.70                 | 0.83              | 0.76                | 0.48                | 0.16             | 0.29               | 0.75                 | 0.82              | 0.79                | 200K                |
| BERT (Fine-tuned)        | 0.80     | 0.82                 | 0.86              | 0.84                | 0.55                | 0.49             | 0.52               | 0.88                 | 0.89              | 0.89                | 200K                |
| DistilBERT (Fine-tuned)  | 0.78     | 0.78                 | 0.88              | 0.83                | 0.52                | 0.39             | 0.45               | 0.88                 | 0.87              | 0.87                | 400K                |
| DistilBERT (Fine-tuned)  | 0.82     | 0.83                 | 0.89              | 0.86                | 0.61                | 0.51             | 0.55               | 0.91                 | 0.91              | 0.91                | 761K                |

### Hardware, Time, and Model Size

| Model                        | Hardware                 | Training Time    | Model Size |
|------------------------------|--------------------------|------------------|------------|
| Logistic Regression 761K     | Intel i7 16-Core CPU     | ~4 Minutes       | 237KB      |
| Random Forest 761K           | Intel i7 16-Core CPU     | ~1.0 Hour        | 8.9GB      |
| XGBoost 200K                 | Intel i7 16-Core CPU     | ~2.4 Hours       | 1752KB     |
| BERT (Fine-tuned) 200K       | Nvidia L4 24GB GPU       | ~9.5 Hours       | 418MB      |
| DistilBERT (Fine-tuned) 400K | Nvidia A100 48GB GPU     | ~4.2 Hours       | 256MB      |
| DistilBERT (Fine-tuned) 761K | Nvidia A100 48GB GPU     | ~7.0 Hours       | 256MB      |

## Feature Importance

The following table lists the top 20 important features for the XGBoost model:

| Feature         | Importance |
|-----------------|------------|
| sentiment_score | 0.004588   |
| loves           | 0.004333   |
| waste           | 0.003470   |
| returned        | 0.003289   |
| stopped         | 0.003263   |
| highly          | 0.003110   |
| cheaply         | 0.002939   |
| ok              | 0.002921   |
| refund          | 0.002784   |
| junk            | 0.002775   |
| body            | 0.002758   |
| broke           | 0.002696   |
| return          | 0.002677   |
| okay            | 0.002595   |
| love            | 0.002569   |
| perfect         | 0.002529   |
| trash           | 0.002487   |
| cheap           | 0.002486   |
| money           | 0.002478   |
| complaint       | 0.002397   |

## Tools and Technologies

- **PySpark:** Utilized for scalable data processing and feature engineering. PySpark's distributed computing capabilities enabled efficient handling of large datasets and complex transformations.
- **Google Colab:** Used for running experiments and model training. Google Colab provided GPU support for faster model training and testing, especially for deep learning models.
- **Hugging Face Transformers:** Employed for leveraging pre-trained models like BERT and DistilBERT. Hugging Face's library facilitated easy fine-tuning and integration of advanced NLP models.

## Conclusion

The project highlights the benefits of advanced NLP models, particularly DistilBERT, over traditional statistical methods for sentiment analysis. By adopting more sophisticated techniques and expanding the dataset, it’s possible to achieve more accurate and nuanced sentiment classification. These improvements offer valuable insights for businesses to better understand and respond to customer sentiments.

For detailed analysis and additional information, please refer to the [Final Report](link-to-final-report).

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

* Free software: MIT license
* Documentation: https://sentiment-amazon-review.readthedocs.io.


========================================


Credits
-------

This package was created with Cookiecutter_ and the `audreyr/cookiecutter-pypackage`_ project template.

.. _Cookiecutter: https://github.com/audreyr/cookiecutter
.. _`audreyr/cookiecutter-pypackage`: https://github.com/audreyr/cookiecutter-pypackage

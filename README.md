# Text Sentiment Labeling with LabelStudio

https://github.com/user-attachments/assets/6e3f7f5e-fd9e-486a-ba73-87eede8cf7f8

This project presents a complete pipeline for annotating product reviews with sentiment labels (`Positive`, `Neutral`, `Negative`) using **Label Studio**. It includes manual labeling and exploratory data analysis (EDA) on the annotated dataset.

The main objectives of this project are to:
- Demonstrate professional-level manual data annotation skills using an industry-standard tool
- Visualize and analyze the characteristics of labeled sentiment data
- Provide a clean dataset for future sentiment modeling tasks

## Dataset Overview

User reviews of the **Genshin Impact** mobile app were scraped from the **Google Play Store** and then manually labeled for sentiment.

There are two datasets used:

- `reviews_genshin_impact.csv`: raw user reviews with star ratings
- `reviews_genshin_impact_annotation.csv`: reviews with manually assigned sentiment labels

| Column              | Description                              |
|---------------------|------------------------------------------|
| `review_text`       | Text content of the user review          |
| `rating`            | Original app rating (1 to 5 stars)       |
| `sentiment`         | Manual label: `Positive`, `Neutral`, `Negative` |

## 🏷️ Annotation Process

- Annotation tool: **Label Studio** (deployed using Docker)
- Task type: Single-label classification (`sentiment`) for each review
- Labeling method: Manual, by a single annotator
- Label categories:
  - `Positive`: Praise, satisfaction, or positive experience
  - `Neutral`: Informative
  - `Negative`: Complaints, dissatisfaction, or criticism

**Label config used in Label Studio:**

```xml
<View>
  <Header value="Choose text sentiment" />
  <Text name="text" value="$review_text" inline="false" encoding="utf8" />
  <Choices name="sentiment" toName="text" choice="single" required="true" layout="vertical">
    <Choice value="Positive" />
    <Choice value="Neutral" />
    <Choice value="Negative" />
  </Choices>
</View>
```
## Exploratory Data Analysis

Notebook: `about_data.ipynb`

### 🔸 Sentiment Distribution:
![download](https://github.com/user-attachments/assets/0bb6caaa-f678-4dfe-80d9-d2bb49931c7e)

- Negative: 38
- Positive: 32
- Neutral: 30

### 🔸 Review Length Insights:
![download (1)](https://github.com/user-attachments/assets/112a7b7e-2fa5-4881-ba49-c0849571be8a)

- Neutral reviews are generally longer and descriptive
- Negative reviews tend to be short and direct
- Outliers exist in all categories with long reviews

### 🔸 WordCloud Observations:
![download (2)](https://github.com/user-attachments/assets/8e4c5b3d-ee28-4891-8038-ab914d8de6c0)

- `Positive`: Praise, satisfaction, or appreciation
- `Neutral`: Balanced feedback, no strong sentiment
- `Negative`: Complaints, frustration, or negative experience

Visualizations included:
- Sentiment label bar chart
- Word count per sentiment (boxplot)
- WordCloud per sentiment category

## Tools & Libraries Used

| Purpose              | Tools / Libraries                   |
|----------------------|-------------------------------------|
| Annotation           | Label Studio (Docker)               |
| Web Scraping         | google-play-scraper            |
| Data Analysis        | pandas, seaborn, matplotlib         |
| Visualization        | WordCloud, Matplotlib               |

## Key Takeaways

- High-quality manual annotation is essential for building reliable supervised learning datasets.
- Label Studio enables streamlined and customizable annotation processes for text classification tasks.
- Even small manually-labeled datasets can provide valuable insights when explored visually and statistically.
- This annotated dataset can be reused or extended for future NLP modeling tasks, especially in low-resource languages like Bahasa Indonesia.

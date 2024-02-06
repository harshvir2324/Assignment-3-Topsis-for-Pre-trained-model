# Pre trained model comparison for text generation using topsis
```mermaid
graph TD;
  style Start fill:#86c7e0,stroke:#4d7ea8,stroke-width:2px,stroke-dasharray: 5, 5;
  style LoadData fill:#99c2e1,stroke:#4d7ea8,stroke-width:2px,stroke-dasharray: 5, 5;
  style PreprocessData fill:#aad3e4,stroke:#4d7ea8,stroke-width:2px,stroke-dasharray: 5, 5;
  style ChooseMetrics fill:#bbe4f7,stroke:#4d7ea8,stroke-width:2px,stroke-dasharray: 5, 5;
  style ApplyTOPSIS fill:#aad3e4,stroke:#4d7ea8,stroke-width:2px,stroke-dasharray: 5, 5;
  style RankModels fill:#99c2e1,stroke:#4d7ea8,stroke-width:2px,stroke-dasharray: 5, 5;
  style GenerateTable fill:#86c7e0,stroke:#4d7ea8,stroke-width:2px,stroke-dasharray: 5, 5;
  style GenerateChart fill:#99c2e1,stroke:#4d7ea8,stroke-width:2px,stroke-dasharray: 5, 5;
  style End fill:#86c7e0,stroke:#4d7ea8,stroke-width:2px,stroke-dasharray: 5, 5;

  subgraph A[Project Steps]
    Start -->|Start| LoadData;
    LoadData -->|Load the dataset| PreprocessData;
    PreprocessData -->|Clean and format data| ChooseMetrics;
    ChooseMetrics -->|Select evaluation metrics| ApplyTOPSIS;
    ApplyTOPSIS -->|Use TOPSIS method| RankModels;
    RankModels -->|Generate rankings| GenerateTable;
    GenerateTable -->|Create ranked table| GenerateChart;
    GenerateChart -->|Visualize with a bar chart| End;
  end

  subgraph " "
    ChooseMetrics -->|Consider BLEU, model size, inference time, fact-checking score| ApplyTOPSIS;
    GenerateTable -->|Include normalized TOPSIS scores and rankings| GenerateChart;
  end

```

## Overview
Text generation is a process where an AI system produces written content, imitating human language patterns and styles. The process involves generating coherent and meaningful text that resembles natural human communication.This project focuses on comparing the performance of various text generation models to help users choose the most suitable model for their specific needs.

## Key Features:

1. **Metrics Considered:**
   - The comparison is based on essential metrics, including BLEU scores, model size,inference time and fact checking scores.
     
2. **Methodology - TOPSIS:**
   - The Technique for Order of Preference by Similarity to Ideal Solution (TOPSIS) method is employed for the comparison. This method considers both the similarity to the ideal solution and the dissimilarity to the negative ideal solution, providing a comprehensive ranking.

3. **Models Evaluated:**
   - Real-world pretrained models, such as T5-base, GPT-2, BLOOM, Bart Large and Jurassic-1 Jumbo, are included in the comparison. These models are widely used in text generation tasks.
  
## Project Structure:

- **`data.csv`**: CSV file containing evaluation metrics for each model.
- **`result.csv`**: CSV file with ranked results in tabular format.
- **`result.csv`**: CSV file with data used for creating a bar chart.
- **`barchart.png`**: Bar chart visualizing the model comparison.

## Results and Analysis:
1. **Ranked Table:**
- Explore detailed ranked results in summarization_table_result.csv:
  
| Model            | Model_size_GB | Inference_Time_ms | BLEU_Score | Fact_Checking_Score_(0-100) | TOPSIS_Score | Rank |
| ---------------- | ------------- | ----------------- | ---------- | --------------------------- | ------------ | ---- |
| T5-base          | 0.7           | 1.5               | 37.4       | 85                          | 0.920279     | 1    |
| GPT-2            | 1.5           | 0.8               | 35.8       | 75                          | 0.458519     | 2    |
| BLOOM            | 3.9           | 2.1               | 42.1       | 82                          | 0.149159     | 4    |
| Bart Large       | 3             | 2.5               | 40.3       | 83                          | 0.202173     | 3    |
| Jurassic-1 Jumbo | 18.6          | 3.8               | 44.2       | 88                          | 0.006171     | 5    |

2. **Bar Chart:**
The bar chart visually represents the performance metrics of each model, providing an easy-to-understand comparison.
![Alt Text](BarChart.png)




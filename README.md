# 2023 HealthCare AI Competition SNUDH - Oral image synthesis data for artificial intelligence learning project
## <font color="blue">Final Result - 3rd Place (Excellent Award)</font>

## Breaking Problem

### 0. Reproducible Model Performance
To ensure reproducible model performance, random variable handling has been conducted. All random seeds were fixed to 41.

### 1. Imbalanced Train Dataset
The analysis of the training data revealed an imbalance between the labels. Though Borderline SMOTE was intended for use, due to the absence of the imblearn package in the server setup during the previous virtual environment construction period, simple resampling using the `resampling` function of sklearn was employed to address the label imbalance.
#### Balanced Train Dataset
- Decayed (1): 17000
- Not Decayed (0): 17000

### 2. Model Training Speed
Large scale CNNs (such as ResNet, DenseNet, etc.) guarantee performance given sufficient data, but come with the trade-off of decreased training speed. Analyzing and adjusting oversampling, validation size, hyperparameters, and augmentation methods to conduct model selection within the competition period seemed insufficient. Hence, it was decided to utilize EfficientNet, which is efficient in terms of training speed while maintaining performance.
#### Model Performance
| Model           | Params | f1-score       |
|-----------------|--------|----------------|
| EfficientNet B0 | 5.3M   | 0.98882171429196 |
| EfficientNet B3 | 12M    | 0.9973782689708769 |

### 3. Hyperparameters
- **Batch Size**: A batch size of 32 has been found to be optimal both in terms of training speed and model performance for around 30,000 data points.
- **Learning Rate**: Adam optimizer with an initial learning rate of 3e-4 has been set, as it has shown the most decent performance.
- **Learning Rate Decay Method**: ReduceLROnPlateau scheduler has been used.

### 4. Evaluation Dataset (Validation Dataset) Size
Evaluation data size split from the training data is typically done in ratios like 9:1, 8:2, 7:3. Experimentation with 7:3 and 8:2 ratios revealed better model performance with an 8:2 split.

### 5. Data Augmentation
1) Base (Original Dataset)
2) Random Rotation
3) Random Horizontal Flip
4) Random Vertical Flip
5) Random Augmentation
Although all five methods were attempted and combinations were tested, the base Original Dataset yielded the highest performance. Additionally, Cutmix and Non-rigid transform were desired to be implemented but were hindered due to the absence of the albumentations package in the server setup.

### 6. Saving the Best Performing Model
Continuing training without improvement in performance becomes futile. Hence, early stopping with a patience of 5 epochs has been applied, terminating training if the validation loss does not decrease for 5 consecutive epochs.

### Final Configuration
- Fixed Random Seed
- Oversampling
- EfficientNet B3
- Hyperparameters (Batch Size: 32, Learning Rate: 3e-4, ReduceLROnPlateau, Validation Split: 8:2)
- Base Dataset (No Augmentation)
- Early Stopping

![2023 헬스케어 AI 경진대회(포스터)](https://raw.githubusercontent.com/bab-korea/healthcare-ai-contest/main/headlthcare_ai_contest_poster.png)

# 2023 Oral Image Synthesis Data Healthcare AI Competition

The healthcare AI competition in the field of dental oral image synthesis data, held as part of the "2023 NIA Dental Oral Image Synthesis Data Construction Project." Challenge yourself to develop an AI model for classifying dental caries using oral image synthesis data!

This competition will be conducted on the high-performance cloud infrastructure of NAVER CLOUD PLATFORM.

## Competition Topic
Development of an AI model for classifying dental caries using oral image synthesis data

## Evaluation and Assessment Method
- Evaluation will be conducted by a panel of expert judges composed of IT/AI professionals.
   ① Pre-screening: Selection of eligible/ineligible participants
   ② Quantitative Evaluation: Scoring based on evaluation metrics
- Higher scores will be awarded to models with f1-scores closer to 1 (scores will be converted from f1-scores to rankings)

## Submission Format
* Program Output and Performance Metrics<br>
  ① Program Output (Developed Model): Uploaded to the correct answer directory on the GPU server - Source file of the developed model (file containing the language and library versions used)<br>
  ② Performance Metrics: Uploaded to the performance metric directory on the GPU server<br>
* Report (Technical Document) Submission<br>
 - Submission limited to winners after evaluation ※ Winners will be individually notified of the schedule and progress.<br>
 - Submit a summary of results and analysis report in PDF format<br>
 - The report must include the team's name and a brief description of the model<br>
 - The report should be between 1 and 10 pages in length (A4 size).

## Awards and Benefits
- Total Winning Teams: 8 teams / Total Prize Money: 5 million KRW

<table class="tbl_prize">
  <tr>
    <th style="text-align:left;width:50%">Award</th>
    <th style="text-align:center;width:15%">Number of Awards</th>
        <th style="text-align:left;width:35%">Prize Money</th>
  </tr>
  <tr>
    <td>
      <strong>Grand Prize</strong><br>
    </td>
    <td> 1 team </td>
    <td align=center> 2 million KRW </td>
  </tr>
 <tr>
    <td>
      <strong>Excellent Award</strong><br>
    </td>
        <td align=center> 1 team </td>
       <td style="text-align:center"> 1 million KRW</td>
   </tr>
      <tr>
    <td>
      <strong>Honorable Mention</strong><br>
    </td>
        <td align=center> 2 teams </td>
    <td style="text-align:center">50 thousand KRW each</td>
   </tr>
   <tr>
    <td>
      <strong>Runner-up</strong><br>
    </td>
        <td align=center> 4 teams </td>
    <td style="text-align:center">25 thousand KRW each</td>
   </tr>
</table>

## Competition Schedule
- Application: November 30, 2023 (Fri) ~ December 12, 2023 (Tue)
- Competition Participation: December 06, 2023 (Wed) ~ December 12, 2023 (Tue) by 18:00


- Evaluation Period: December 14, 2023 (Thu) ~ December 15, 2023 (Fri)
- Results Announcement: December 16, 2023 (Sat)
- Awards Ceremony: Scheduled for December 21, 2023 (Wed)

## Organized by
- Seoul National University Dental Hospital
- Sponsored

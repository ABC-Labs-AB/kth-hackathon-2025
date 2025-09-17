# 🚀 Submission & Scoring

## Scoring Breakdown

Your hackathon project will be evaluated based on three main criteria, designed to reward both technical excellence and innovative problem-solving approaches:

### 📊 Model Performance (20%)
We'll evaluate your model using **standard classification metrics**:
- **Accuracy** - Overall correctness of predictions
- **Precision** - Quality of positive predictions (avoiding false positives)  
- **Recall (Sensitivity)** - Ability to catch all positive cases
- **F1-Score** - Balanced measure of precision and recall

*Note: Different metrics may be weighted based on business context and the specific problem you're solving. Consider which metrics are most important for your use case.*

### 🧠 Problem-Solving Approach (60%)
This is the **largest component** and focuses on your methodology and reasoning:
- **Problem Understanding** (20%) - How well you grasp the business context and technical challenges
- **Data Analysis & Feature Engineering** (20%) - Quality of data exploration and feature selection
- **Model Selection & Methodology** (20%) - Appropriateness of chosen techniques and experimental design

### 🎤 Presentation (20%)
Your ability to communicate your solution effectively:
- **Clarity & Structure** - Well-organized, easy-to-follow presentation
- **Technical Communication** - Ability to explain complex concepts clearly
- **Business Impact** - Connection between technical solution and business value
- **Team Collaboration** - Evidence of effective teamwork

## 💡 Flexible Approach Philosophy

We understand that hackathons are about **exploration and learning**. Teams are encouraged to:

- **Tackle partial solutions** - Focus on one aspect of the problem that interests you most
- **Build proof-of-concepts** - Demonstrate feasibility rather than production-ready systems  
- **Experiment boldly** - Try innovative approaches even if they're not fully developed
- **Learn and iterate** - Document your learning process and decision-making

**Remember:** A well-reasoned approach to solving part of the problem can score higher than a rushed attempt at the full solution.

## 📤 Submission Requirements

### Required Deliverables
1. **Trained Model** — Submit your final trained model under the filename `final_model`, saved in a format appropriate for your ML framework (e.g. `.pkl` for scikit-learn, `.h5` or SavedModel for TensorFlow, `.pt` for PyTorch).

2. **Predictions File** — Include your model predictions on the **test dataset** in a file named `predictions.pkl`. Your predictions should be formatted as:
   - **sample_file_name**: The filename of each test sample
   - **label**: "POS" or "NEG" 
   - **confidence_score**: Probability/confidence for each prediction (0.0 to 1.0)
   - Format: Python pickle file containing a pandas DataFrame with these three columns

3. **Jupyter Notebooks** — Include all your analysis, modeling, and experimentation notebooks.

4. **Documentation** — You must provide a `README.md` with your submission. The required structure and backbone for this README can be found in the [README Format Guide](README_Format_Guide.md).

### Submission Format
Upload all your final deliverables to your assigned **GCP Storage bucket** by creating a new `final-submission/` folder.

### Expected Folder Structure
After submission, your bucket should contain the following structure (note that `data/` and `notebooks/` folders already exist from your previous work):

- kth-team-XX-data/
  - data/
  - notebooks/
  - final-submission/
    - final_model.[extension]
    - predictions.pkl
    - README.md
    - notebooks/
      - notebook1.ipynb (example: analysis.ipynb)
      - notebook2.ipynb (example: modeling.ipynb)
      - [additional notebooks as needed]

### ⏰ Deadline
**28-09-2025, 23:59** - No late submissions will be accepted. Write permissions to your bucket will be automatically removed at the deadline.

## 🏆 Judging Process

1. **Technical Review** - Judges will evaluate code quality, methodology, and results
2. **Presentation Session** - 10-minute presentation + 5-minute Q&A per team
3. **Scoring & Deliberation** - Judges score independently, then discuss rankings
4. **Awards Ceremony** - Winners announced with feedback for all teams

## 💪 Success Tips

- **Start with data exploration** - Understanding your data is crucial
- **Document your process** - Show your thinking, not just final results  
- **Focus on storytelling** - Connect technical work to business impact
- **Collaborate effectively** - Leverage each team member's strengths
- **Iterate quickly** - Better to have a simple working solution than a complex broken one

---
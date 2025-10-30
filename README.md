# Effects of Lactose and Lactose-Free Milk Coffee on Study Efficiency

## Table of Contents
1. [Abstract](#abstract)
2. [Motivation](#motivation)
3. [Evaluation Parameters](#evaluation-parameters)
4. [Data Source & Collection](#data-source--collection)
5. [Data Analysis Plan](#data-analysis-plan)
6. [Machine Learning Application](#machine-learning-application)
7. [Tools & Libraries](#tools--libraries)
8. [Data Validity and Reliability](#data-validity-and-reliability)
9. [Limitations and Future Work](#limitations-and-future-work)

---

## Abstract
This project investigates whether the type of milk used in coffee (lactose vs. lactose-free) affects study efficiency. Over a 30-day period, I will collect self-observed data while maintaining consistent daily routines, such as sleep duration and meal types. For 15 days, I will drink lactose milk coffee; for the other 15 days, lactose-free milk coffee during studying. Variables such as focus duration, number of breaks, time spent in the library, and overall productivity ratio will be recorded, alongside self-assessed energy levels before and after drinking coffee. The analysis aims to determine whether lactose consumption has a measurable impact on learning performance and energy levels using regression analysis and hypothesis testing.

---

## Motivation
I often consume coffee while studying but have noticed differences in how I feel depending on the milk type. My motivation is to understand how lactose in milk might affect my focus, energy level, and productivity during study sessions. In recent years, the distinction between **lactose and lactose-free milk products** has become increasingly common and popular in daily consumption. I also wanted to explore whether this widespread preference truly creates a noticeable difference in study performance or if it is simply a lifestyle trend. If I discover that lactose negatively influences my efficiency, I will adapt my coffee habits to optimize concentration and study routine. This project will help me make data-driven lifestyle choices to study more effectively.

---

## Evaluation Parameters

To evaluate the impact of lactose and lactose-free milk coffee on study efficiency, the following parameters will be considered:

1. **Focus Duration (minutes)**  
   - Total continuous study time before the first major distraction or break.
2. **Number of Breaks**  
   - Frequency of breaks taken during a study session.
3. **Library Time (minutes)**  
   - Total duration spent studying in the library or study environment.
4. **Productivity Ratio**  
   - Ratio of focus duration to total library time.  
5. **Energy Levels**  
   - Self-assessed energy before and after drinking coffee, rated on a 1–3 Likert scale:  
     - 1 = tired  
     - 2 = normal  
     - 3 = energetic  
6. **Energy Change (EnergyAfter – EnergyBefore)**  
   - The difference between self-reported energy after and before coffee, showing whether energy increased, decreased, or remained stable.  
7. **Coffee Type**  
   - Lactose (coded as `0`) and Lactose-Free (coded as `1`), used to compare performance differences.

Each of these parameters will help determine how the type of milk in coffee influences overall study performance and daily efficiency.

---

## Data Source & Collection
The data will be **self-collected** over a **30-day observation period**:
- **Days 1–15:** Lactose milk coffee  
- **Days 16–30:** Lactose-free milk coffee  
- All other factors (sleep duration, meal type) will be kept constant.

Each day, I will record:
| Date | CoffeeType | FocusDuration(min) | BreakCount | LibraryTime(min) | ProductivityRatio | EnergyBefore(1–3) | EnergyAfter(1–3) | EnergyChange |
|------|-------------|--------------------|-------------|------------------|------------------|------------------|-----------------|---------------|
| 2025-10-29 | Lactose | 90 | 2 | 180 | 0.5 | 1 (tired) | 3 (energetic) | +2 |
| 2025-11-16 | Lactose-Free | 110 | 1 | 200 | 0.55 | 2 (normal) | 3 (energetic) | +1 |

- **Objective variables:** FocusDuration, BreakCount, LibraryTime, ProductivityRatio  
- **Subjective variables:** EnergyBefore, EnergyAfter, and **EnergyChange** (difference between EnergyAfter and EnergyBefore, indicating the variation in perceived energy after coffee)

---

## Data Analysis Plan
1. **Data Cleaning & Preparation**
   - Ensure consistent units and missing value checks  
   - Encode categorical variable (`CoffeeType`: 0 = lactose, 1 = lactose-free)  

2. **Exploratory Data Analysis (EDA)**
   - Compare means of focus duration, productivity, and energy change  
   - Visualize distributions using boxplots and scatter plots

3. **Hypothesis Testing**
   - **H₀₁ (Null):** Lactose in milk has **no meaningful or notable effect** on productivity ratio.  
     **H₁₁ (Alternative):** Lactose in milk **may have some influence** on productivity ratio.  
      `ProductivityRatio ~ CoffeeType`
     
   - **H₀₂ (Null):** There is **no inverse relationship** between EnergyChange and the number of breaks; changes in energy do **not affect** how often breaks are taken.  
     **H₁₂ (Alternative):** Lower EnergyChange values (decreased energy) **may lead to more breaks** during study sessions.  
      `BreakCount ~ EnergyChange`  
      `ProductivityRatio ~ BreakCount`

   - **H₀₃ (Null):** EnergyChange has **no positive relationship** with focus duration.  
     **H₁₃ (Alternative):** Higher EnergyChange (increased energy) **may be associated** with longer focus duration.  
      `FocusDuration ~ EnergyChange`
     
   - **H₀₄ (Null):** The number of breaks taken during study sessions has **no inverse relationship** with productivity ratio.  
     **H₁₄ (Alternative):** A higher number of breaks **may be associated** with lower productivity ratio.  
      `ProductivityRatio ~ BreakCount`
    
4. **Regression Analysis**
   - Perform **linear regression** with:
     ```
     FocusDuration ~ CoffeeType + EnergyChange + BreakCount
     ```
   - Evaluate the influence of milk type and energy variation on study performance while controlling for break count.

5. **Visualization**
   - Use `matplotlib` and `seaborn` for correlation bar plots, and regression line plots.  
   - Create scatter plots showing **EnergyChange vs. ProductivityRatio** to visualize the relationship between energy variation and efficiency.

---

## Machine Learning Application
After regression, a **Random Forest Regressor** can be used to validate variable importance:
- Feature importance will reveal whether `CoffeeType` (lactose vs. lactose-free) or `EnergyChange` has a measurable predictive effect on `FocusDuration` or `ProductivityRatio`.

---

## Tools & Libraries
- **Language:** Python  
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn, scipy 

---

## Data Validity and Reliability
Although the **energy variables** are self-reported, a standardized 1–3 measurement scale will be used daily to reduce subjectivity.  
By keeping sleep duration, meals, and study schedule constant, external bias will be minimized. Averaging data across 15-day intervals further improves reliability and reduces random noise.

---

## Limitations and Future Work
- Self-reported data may include minor bias. 
- External conditions (mood, weather, coursework load) may still affect performance.  
- Future extensions could include other participants or different coffee additives (e.g., oat milk, black coffee).

---

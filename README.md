# 👁️ Screen-Based Vision Acuity Prediction System

An **AI/ML-based screen vision acuity assessment system** that estimates a user's visual acuity and approximate refractive power by presenting randomized characters at different font sizes and analyzing the smallest text size the user can reliably recognize.

The system is designed as a **screen-based preliminary vision assessment tool**, using an adaptive testing approach and a **Random Forest Regression model** to estimate refractive power from visual recognition performance.

> ⚠️ **Disclaimer:** This project is intended for educational and research purposes. It is not a replacement for a professional eye examination or prescription from an optometrist/ophthalmologist.

---

## 📌 Overview

Traditional vision testing generally requires specialized equipment such as Snellen charts, optotypes, or clinical instruments.

This project explores whether a **standard computer/laptop screen** can be used to perform a preliminary vision assessment by dynamically changing:

* Character size
* Character sequences
* Test difficulty
* Font variations
* Recognition thresholds

The system records the smallest character size that the user can consistently identify and uses the collected measurements as input to a machine-learning model.

The objective is to provide an accessible and low-cost approach for **screen-based vision acuity estimation**.

---

## 🎯 Objectives

* Develop a computer-based vision acuity testing system.
* Present randomized character sequences at different font sizes.
* Determine the smallest readable character size for the user.
* Use an adaptive testing strategy to reduce unnecessary test iterations.
* Train a machine-learning model to estimate refractive power.
* Provide an estimated diopter range as the final output.
* Create an easy-to-use desktop interface for conducting the test.
* Explore the feasibility of screen-based preliminary vision assessment.

---

## 🧠 How It Works

The system follows a sequence of visual testing and machine-learning steps.

```text
                 ┌──────────────────────┐
                 │      Start Test      │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Display Characters   │
                 │ at Selected Size     │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ User Enters Answer   │
                 └──────────┬───────────┘
                            │
                     Correct / Incorrect
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Adaptive Difficulty  │
                 │ Adjustment           │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Determine Smallest   │
                 │ Readable Font Size   │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ ML Prediction Model  │
                 │ Random Forest        │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Estimated Refractive │
                 │ Power / Range        │
                 └──────────────────────┘
```

---

## 🔬 Testing Methodology

The testing process presents randomized character sequences to the user.

Each test varies the visual difficulty by changing the displayed character size.

### Example

```text
Large Font
    ↓
Medium Font
    ↓
Smaller Font
    ↓
Smaller Font
    ↓
Recognition Failure
    ↓
Determine Recognition Threshold
```

The system records the user's responses and identifies the approximate threshold at which character recognition becomes unreliable.

Multiple trials can be performed at each level to improve consistency and reduce the influence of individual incorrect responses.

---

## 🤖 Machine Learning Model

### Random Forest Regression

The project uses **Random Forest Regression** to estimate refractive power from the measurements collected during the vision test.

### Input Features

Depending on the implementation, the model can use features such as:

* Minimum readable font size
* Recognition accuracy
* Number of successful trials
* Number of failed trials
* Test distance
* Character recognition threshold
* Other derived testing measurements

### Output

The model produces an estimated refractive power in **diopters (D)** or an approximate refractive-power range.

Example:

```text
Input:
Minimum readable size = 35 px
Recognition accuracy = 80%
Testing distance = 100 cm

        ↓

Random Forest Regression

        ↓

Estimated Power:
Approximately -3.0 D
```

---

## 📊 Experimental Data

Initial experimental observations were collected at a testing distance of approximately **100 cm**.

Example observations:

| Approx. Power | Approx. Recognition Failure Size |
| ------------- | -------------------------------- |
| -0.50 D       | ~11 px                           |
| -0.75 D       | ~8 px                            |
| -2.00 D       | ~22 px                           |
| -2.25 D       | ~26 px                           |
| -3.00 D       | ~35 px                           |
| -3.50 D       | ~40 px                           |
| -3.75 D       | ~42 px                           |
| -6.00 D       | ~80 px                           |

These values are **experimental observations rather than clinical reference values** and may vary significantly between users, displays, viewing distances, fonts, and testing conditions.

The dataset can be expanded with additional participants and controlled measurements to improve model robustness.

---

## 🖥️ User Interface

The project uses a desktop GUI to conduct the vision test.

The interface provides:

* Start Test functionality
* Randomized character display
* Dynamic font-size adjustment
* User response input
* Skip functionality
* Test progression
* Recognition tracking
* Final prediction display

The intended workflow is:

```text
Start Test
    ↓
Read Character Sequence
    ↓
Enter Recognized Characters
    ↓
Submit / Skip
    ↓
Next Test
    ↓
Determine Threshold
    ↓
ML Prediction
    ↓
Display Estimated Result
```

---

## 🛠️ Technologies Used

| Technology        | Purpose              |
| ----------------- | -------------------- |
| **Python**        | Core development     |
| **Tkinter**       | Desktop GUI          |
| **Scikit-learn**  | Machine learning     |
| **Random Forest** | Regression model     |
| **NumPy**         | Numerical processing |
| **Pandas**        | Dataset processing   |
| **Matplotlib**    | Data visualization   |
| **Joblib**        | Model serialization  |

---

## 📁 Project Structure

```text
screen-vision-acuity/
│
├── dataset/
│   ├── vision_data.csv
│   └── processed_data.csv
│
├── model/
│   ├── train_model.py
│   └── vision_model.pkl
│
├── src/
│   ├── main.py
│   ├── vision_test.py
│   ├── adaptive_test.py
│   └── prediction.py
│
├── experiments/
│   └── experimental_results.csv
│
├── requirements.txt
├── README.md
└── LICENSE
```

> The exact structure can be modified according to the current implementation of the repository.

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/screen-vision-acuity.git
```

### 2. Navigate to the project

```bash
cd screen-vision-acuity
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the environment

#### Windows

```bash
venv\Scripts\activate
```

#### Linux / macOS

```bash
source venv/bin/activate
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Project

Run the main application:

```bash
python src/main.py
```

The application will launch the vision testing interface.

Follow the instructions displayed on the screen and complete the visual recognition tests.

---

## 🧪 Model Training

If the model needs to be retrained using the available dataset:

```bash
python model/train_model.py
```

The training pipeline performs the following steps:

```text
Dataset
   ↓
Data Cleaning
   ↓
Feature Preparation
   ↓
Train/Test Split
   ↓
Random Forest Regression
   ↓
Model Evaluation
   ↓
Save Trained Model
```

The trained model can then be loaded by the application for prediction.

---

## 📈 Model Evaluation

The machine-learning model can be evaluated using regression metrics such as:

* Mean Absolute Error (MAE)
* Mean Squared Error (MSE)
* Root Mean Squared Error (RMSE)
* R² Score

Example evaluation:

```text
MAE  : X.XX D
RMSE : X.XX D
R²   : X.XX
```

> Replace these placeholder values with the actual evaluation results obtained from your final dataset.

---

## 🚀 Key Features

### 🔤 Randomized Character Testing

Character sequences are randomized to reduce memorization and predictability during testing.

### 📏 Dynamic Font Scaling

The font size changes during the test to identify the user's recognition threshold.

### 🧠 Adaptive Testing

The testing difficulty can be adjusted based on the user's previous responses rather than using a fixed sequence.

### 🤖 Machine Learning Prediction

A Random Forest Regression model converts the collected measurements into an estimated refractive-power value.

### 🖥️ Desktop Application

The system provides a graphical interface for conducting the complete test.

### 📊 Data-Driven Approach

The system uses experimentally collected observations and machine-learning techniques rather than relying solely on fixed lookup tables.

---

## 🔮 Future Improvements

Several improvements can make the system more reliable and closer to a controlled vision-assessment research prototype:

* Increase dataset size with data from more participants.
* Collect data under controlled lighting conditions.
* Support different screen resolutions and pixel densities.
* Automatically calibrate physical character size.
* Account for screen-to-eye distance.
* Add standardized optotypes such as **Sloan letters**.
* Introduce binocular and monocular testing modes.
* Improve adaptive testing using Bayesian or psychometric methods.
* Compare Random Forest with other regression models.
* Add confidence intervals to predictions.
* Develop a web-based version.
* Add user authentication and test-history tracking.
* Perform controlled validation against professional eye-test measurements.
* Investigate deep-learning approaches for personalized prediction.

---

## ⚠️ Limitations

The results produced by this system can be affected by several factors:

* Monitor size and resolution
* Display scaling settings
* Viewing distance
* Ambient lighting
* Font rendering
* User familiarity with characters
* Individual visual characteristics
* Screen brightness and contrast
* Dataset size
* Training-data quality

Therefore, the predicted refractive power should **not be interpreted as a clinical prescription**.

---

## 🔐 Ethical & Safety Considerations

This project is intended as an **educational and research prototype**.

It should not be used to:

* Diagnose eye diseases
* Replace an eye examination
* Determine a final eyeglass prescription
* Make medical decisions

Users experiencing persistent blurred vision, headaches, eye strain, or other visual problems should consult a qualified eye-care professional.

---

## 🎓 Academic Context

This project explores the application of:

* Machine Learning
* Human-Computer Interaction
* Adaptive Testing
* Computer-Based Vision Assessment
* Regression Analysis
* Experimental Data Collection

It demonstrates how software and machine-learning techniques can be combined to investigate **accessible screen-based visual assessment systems**.

---

## 👨‍💻 Author

**Sudheendra K**

B.Tech – Computer Science Engineering
Mahatma Gandhi Institute of Technology (MGIT)
2023 – 2027

### Areas of Interest

* Machine Learning
* Artificial Intelligence
* Full Stack Development
* Computer Vision
* Generative AI
* Software Development

---

## ⭐ If You Find This Project Interesting

Consider giving the repository a ⭐ and exploring the implementation.

Contributions, suggestions, and research-oriented improvements are welcome.

---

## 📄 License

This project is intended for educational and research purposes.

Add an appropriate open-source license such as **MIT License** if you want to permit reuse and modification of the source code.

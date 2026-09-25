# Baseline Predictive Pipeline -- ETAI - Exploratory Topics of Artificial Intelligence.
### 20221997 - Suelen Karina Faruk 

## Week 1 - Conclusions:
#### Logistic Regression before cleaning the data:
Logistic Regression:
Train accuracy: 0.679
Test accuracy:  0.680
Gap (train - test): -0.001

#### Conclusions:
This model performs well on training but also performs well on testing with these results we can say that the model is less likely to overfit as the gap between train and test is very low.

#### Decision Three after cleaning the data:
Decision Three: 
Train accuracy: 0.829
Test accuracy:  0.626
Gap (train - test): +0.203


#### Conclusions:
This model performs well on the training data, although the gap between the training and test accuracy gives us evidence of possible overfitting. The test accuracy shows that the model is also able to make predictions on unseen data, although its performance is lower than on the training data.

#### Best Model:
Based on test accuracy and the train-test gap, Logistic Regression performs better than the Decision Tree in these experiments. It achieves higher test accuracy and has a much smaller gap between training and test performance, giving us less evidence of overfitting. Besides the smaller gap(train-test), the model has similar scores in train and test which gives us further evidence that the model will be less likely to overfit.


## Week 2 - Conclusions:
#### Logistic Regression after cleaning the data: 
Logistic Regression:
Train accuracy: 0.678
Test accuracy:  0.655
Gap (train - test): +0.023 

#### Conclusions:
The gap increased enough to say Although the model has an overall test accuracy of 65.5%, it's recall for people who actually reoffended is only 51%. Therefore, the overall accuracy does not mean that the model identifies reoffenders particularly well.
The model has similar performance on the training and test data.The small train-test gap is another metric that gives us less evidence of overfitting, as the model's performance does not decrease substantially when applied to unseen data.


#### Decision Three after cleaning the data:
Decision Three: 
Train accuracy: 0.691
Test accuracy:  0.642
Gap (train - test): +0.049

#### Conclusions:
The training accuracy decreased, but the test accuracy increased. This suggests that the model was fitting the training data less closely and was able to generalize better to unseen data, but if we had just the train-test gap result I would say that here this model is less likely to overfit.

#### Best model:
The Logistic Regression that I run before cleaning it has the strongest results among all the models tested.

Compared with Logistic Regression after cleaning, the model has a higher test accuracy (68.0% vs. 65.5%) and a smaller train-test gap (-0.001 vs. +0.023). Compared with the Decision Tree after cleaning, it also has a higher test accuracy (68.0% vs. 64.2%) and a smaller train-test gap (-0.001 vs. +0.049). These results give us less evidence of overfitting and indicate that the model generalizes more consistently to unseen data.



## Brief Summary of the Semester
This is the **starting point** for your semester project: a small but *complete* predictive pipeline -- every piece a real project needs (entry point, config, data loading, preprocessing, model, evaluation), just kept as simple as possible for now.

The task: predict two-year recidivism using ProPublica's COMPAS
dataset -- the data behind a real 2016 investigation into a risk-
assessment algorithm actually used by US courts to help inform bail and sentencing decisions. See `data/README.md` for the full problem description and a complete data dictionary before you start.

It has some **deliberately weak spots**. Part of your work this
semester is finding them and making them better -- see the pipeline progress table below, which tracks what changes and why as the weeks
go on.

## Project structure

```
.
├── main.py                # entry point: run the whole pipeline
├── config.yaml             # all tunable settings live here
├── requirements.txt
├── src/
│   ├── data.py             # loading
│   ├── preprocessing.py    # cleaning + train/test split
│   ├── model.py             # model construction
│   ├── evaluate.py         # accuracy metrics + fairness check
│   └── results.py          # saves each run's report to disk
├── results/                # created automatically -- one file per run (not tracked in git)
└── data/
    ├── compas_two_year_recidivism.csv
    └── README.md            # problem description + full data dictionary
```

## Pipeline progress

This table is updated after each practical class, so you can always see what changed in the pipeline and why -- it's a running log, not a fixed syllabus.

| Week | Practical class focus | Added to the pipeline |
|------|------------------------|------------------------|
| 2 | Introduction & baseline pipeline | Initial version: project structure, a single naive train/test split (no cross-validation), minimal preprocessing (drop rows with missing values, one-hot encode categoricals), logistic regression baseline, a first (deliberately simple) fairness check comparing our model's and COMPAS's own false-positive rate by race, train-vs-test accuracy reporting (to start spotting overfitting), and each run's full report saved automatically to `results/` |

## Environment setup

You only need to do this once per machine.

### macOS / Linux
```bash
python3 -m venv venv                 # creates an isolated Python environment in a folder called "venv"
source venv/bin/activate             # activates it -- packages install here, not system-wide, and stay out of your other projects
pip install -r requirements.txt      # installs the exact packages this project needs, into that environment
```

### Windows -- PowerShell
```powershell
python -m venv venv                  # creates an isolated Python environment in a folder called "venv"
venv\Scripts\activate                # activates it -- packages install here, not system-wide, and stay out of your other projects
pip install -r requirements.txt      # installs the exact packages this project needs, into that environment
```
If PowerShell blocks the activation script, run this once first:
```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

### Windows -- cmd.exe
Same three steps as above, just with cmd's own activation command:
```cmd
python -m venv venv
venv\Scripts\activate.bat
pip install -r requirements.txt
```

Once the environment is active you'll see `(venv)` at the start of your prompt. To leave it later, run `deactivate` (same command on every OS).

### Every time after the first

Creating the environment and installing packages only needs to happen once, ever. Every other time you sit down to work -- a new terminal window, the next practical class, tomorrow -- you don't repeat any of the steps above. From the project's root folder, you just need to:

**macOS / Linux**
```bash
source venv/bin/activate
python main.py
```

**Windows**
```powershell
venv\Scripts\activate
python main.py
```

That's it -- activate, then run. If you don't see `(venv)` at the start of your prompt, the environment isn't active and `python main.py` may use the wrong Python (or fail to find a package) entirely.

## Running the pipeline

With the environment active (see above), from the project's root
folder, on any OS:
```bash
python main.py
```

This loads `config.yaml`, loads and preprocesses the data, trains the model, and prints:
- **train accuracy and test accuracy, side by side.** Comparing the two is how you catch overfitting: if the model looks much better on the data it was trained on than on data it's never seen, it has memorised rather than learned something that generalises. 
- a classification report on the test set
- a false-positive-rate-by-race comparison between our model and
  COMPAS's own score

All of this is also saved to a timestamped file in `results/` (e.g.`results/run_20260916_143012.txt`), so it doesn't just scroll past in your terminal -- open it later, or change something in `config.yaml` (like the model type) and compare the new file to the last one.
`results/` is created automatically the first time you run the
pipeline, and isn't tracked in git (see `.gitignore`) since it's
generated output, not source.

You're free to improve on this structure or restructure it entirely -- what matters is that your project stays runnable end-to-end with a single command, and that each piece (data, preprocessing, model, evaluation) stays easy to find and change independently.

## Dataset

See `data/README.md`.

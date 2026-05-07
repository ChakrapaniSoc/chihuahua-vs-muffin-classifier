# chihuahua-vs-muffin-classifier
Overview
This project is part of the Chihuahua vs Muffin Classifier Hackathon, where the objective is to build a binary image classifier using a data-centric AI workflow powered by 3LC Official Website.
Instead of improving the model architecture, the competition focuses on improving the dataset using:


embeddings


active learning


sample weighting


strategic labeling


The fixed architecture is:


PyTorch ResNet-18


trained from scratch


no pretrained weights allowed



Problem Statement
Classify images into:
LabelClass0Chihuahua1Muffin
The competition evaluates:


hidden test set accuracy


leaderboard ranking on Kaggle Competition Platform



Project Structure
Starter_Kit/│├── data/│   ├── train/│   ├── val/│   └── test/│├── register_tables.py├── train.py├── predict.py├── config.yaml├── requirements.txt├── submission.csv├── README.md└── best_model.pth

Data-Centric AI Concept
Traditional machine learning focuses on:


changing architectures


tuning hyperparameters


Data-centric AI focuses on:


improving labels


improving sample quality


selecting informative samples


correcting dataset issues


This project uses:


embeddings visualization


confidence-based labeling


sample weighting


iterative retraining



Dataset Description
Training Set
TypeCountLabeled Chihuahua50Labeled Muffin50Unlabeled Images3579

Validation Set
TypeCountChihuahua500Muffin500

Test Set
TypeCountHidden Test Images1184

Technology Stack
ToolPurposePythonCore programmingPyTorchDeep learning3LC PlatformData-centric AI workflowVisual Studio CodeDevelopmentKaggleCompetition leaderboardGitVersion control

Environment Setup
Create Virtual Environment
Windows
python -m venv 3lc-env3lc-env\Scripts\activate

Install Dependencies
pip install 3lc joblib pytz umap-learn torch torchvision

Login to 3LC
3lc login <YOUR_API_KEY>
Get API key from:
3LC Account Portal

Start 3LC Service
3lc service
Open dashboard:
3LC Dashboard

Workflow
Step 1 — Register Tables
python register_tables.py
This creates:


train table


validation table


inside the 3LC workspace.

Step 2 — Initial Training
python train.py
This:


trains ResNet-18


logs metrics


generates embeddings


stores runs in 3LC


Output:


best_model.pth



Embeddings Visualization
The 3LC Dashboard provides:


3D embeddings


confidence analysis


clustering visualization


error inspection


Embeddings help identify:


mislabeled images


uncertain samples


high-confidence unlabeled data



Active Learning Workflow
Process


Train on small labeled dataset


Generate predictions on unlabeled data


Visualize embeddings


Select informative samples


Label selected images


Set sample weight = 1


Save new table revision


Retrain model


This iterative loop improves accuracy significantly.

Sample Weighting
WeightMeaning0Ignore sample during training1Include sample during training
Initially:


labeled samples → weight = 1


unlabeled samples → weight = 0



Retraining
After labeling new samples:
python train.py
The script automatically loads:


latest table revision


updated labels


updated sample weights



Prediction & Submission
Generate predictions:
python predict.py
This creates:
submission.csv

Submission Format
image_id,prediction,confidencetest_00001,0,0.92test_00002,1,0.88

Evaluation Metric
Competition metric:


Classification Accuracy


Range:


0.0 → 1.0


Higher is better.

Public vs Private Leaderboard
LeaderboardPortionPublic50%Private50%
Final winners are determined using:


private leaderboard score



Key Features of 3LC
Tables
Version-controlled datasets.
Revisions
Every modification creates a new dataset revision.
Runs
Experiment tracking system.
Embeddings
3D visualization of feature representations.
Sample Weighting
Controls participation in training.

Important Competition Rules
RuleRequirementModelResNet-18 onlyExternal dataNot allowedPretrained weightsNot allowed3LC usageMandatoryTrainingFrom scratch

GitHub Repository Requirements
The final repository should contain:
- Python source files- README- Writeup / presentation- 3LC screenshots- submission details- requirements.txt- zipped 3LC project

Recommended .gitignore
3lc-env/__pycache__/*.pyc.vscode/*.dll*.pyd*.pth*.pt

Common Issues
GitHub Push Rejected
Cause:


large files inside virtual environment


Fix:
git rm -r --cached 3lc-env

Dashboard Connection Error
Fix:


ensure 3lc service is running


use Chrome or Edge



CUDA Not Detected
Verify:
python -c "import torch; print(torch.cuda.is_available())"

Learning Outcomes
This project demonstrates:


data-centric AI


active learning


embeddings analysis


iterative labeling


experiment tracking


dataset engineering



Conclusion
This hackathon showcases how improving dataset quality can significantly improve model performance without changing the architecture.
Using:


embeddings


confidence analysis


active learning


strategic labeling


participants can achieve high classification accuracy through a systematic data-centric workflow.

References


3LC Documentation


PyTorch Documentation


Kaggle Platform


UMAP Documentation


# LoLWatcher

A demo notebook for predicting the winning team of a game of professional League of Legends, specifically LCS games.

___

[![](https://img.shields.io/static/v1?label=Build&message=alpha&color=red "Build")](#)
[![](https://img.shields.io/static/v1?label=Status&message=ok&color=brightgreen "Status")](#)
[![](https://img.shields.io/static/v1?label=Python&message=3.10&color=yellow "Python")](#)
[![](https://img.shields.io/static/v1?label=Platform&message=linux|macOS|Windows&color=lightgrey "Platform")](#)
[![](https://img.shields.io/static/v1?label=License&message=MIT&color=blue "License")](#)
___

### Table of Contents

1. [Install](#install)
1. [Usage](#usage)
1. [Model](#model)

### Install
___

It is recommended to create a new python virtual environment and install the project dependencies with pip.

Create a new env:

`virtualenv env`

Activate the virtual environment:

`.../env/bin/Scripts/activate`

or

`...\env\bin\Scripts\activate`

Install dependencies with pip:

`pip install -r requirements.txt`

Finally, this notebook depends on [Tesseract](https://github.com/tesseract-ocr/tesseract).

Installation instructions can be found [here](https://tesseract-ocr.github.io/tessdoc/Installation.html).

### Usage
___

Run the `LoLWatcher.ipynb` locally while watching LCS!

Or run a demo in Colab with presaved-screenshots from the LCS Summer Playoffs 2022 TL vs FQ upper bracket quarterfinal game 2!

[![](https://img.shields.io/static/v1?label=%7F&message=Open%20in%20Colab&color=blue&logoColor=&logo=googlecolab "Open in Colab")](https://colab.research.google.com/drive/1Gm8JKo5FLo-06LFdQIKSaHX-jZQtoaGH?usp=sharing)

### Model
___

The LoLWatcher V2 model is trained on over 6800 matches of Korean SoloQueue games at the Master, Grandmaster and Challenger level obtained from a list of 120+ LCK, LPL and LCS pros.

Although using the Riot Games match v5 API provides over 100 different metrics per player for over 1000 metrics per game, the LoLWatcher V2 model only uses 63 metrics which can be consistently read by Tesseract OCR during the live LCS broadcast. These include team objectives including total team kills, towers taken, first tower bonus, barons taken, dragons taken and individual stats for each player including minions killed, kills, deaths, and assists.

On the train test split using a test size of 30% and a random state of 5, the model achieved 0.99 precision, 0.98, recall, and 0.98 f1 score with a support of 1077 on the negative class, and 0.98 precision, 0.99 recall, and 0.98 f1 score with a support of 988 on the positive class. This was obtained from the sci-kit learn classification report. The positive class represents a case where the blue side team won the game, and the negative class represents a case where the blue side team lost the game.

The confusion matrix can be found below.

|                 | Predicted Negative | Predicted Positive |
| :---            | :----:             | :---:              |
| Actual Negative | 1056 TN            | 21 FP              |
| Actual Positive | 12 FN              | 976 TP             |

* Precision: 0.9789
* Recall: 0.9879
* F1 Score: 0.9833
* Accuracy: 0.98
* Test Samples: 2065
# LoLWatcher

A demo notebook for predicting the winning team of a game of professional League of Legends, specifically LCS games.

___

[![](https://img.shields.io/static/v1?label=Build&message=alpha&color=red)](#)
[![](https://img.shields.io/static/v1?label=Status&message=ok&color=brightgreen)](#)
[![](https://img.shields.io/static/v1?label=Python&message=3.10&color=yellow)](#)
[![](https://img.shields.io/static/v1?label=Platform&message=linux|macOS|Windows&color=lightgrey)](#)
[![](https://img.shields.io/static/v1?label=License&message=MIT&color=blue)](#)
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

`...\env\bin\Scripts\Activate`

Install dependencies with pip:

`pip install -r requirements.txt`

Finally, this notebook depends on [Tesseract](https://github.com/tesseract-ocr/tesseract).

Installation instructions can be found [here](https://tesseract-ocr.github.io/tessdoc/Installation.html).

### Usage
___

Run the `LoLWatcher.ipynb` locally while watching LCS!

### Model
___

The LoLWatcher V2 model is trained on over 7000 matches of Korean SoloQueue games at the Master, Grandmaster and Challenger level obtained from a list of 120+ LCK, LPL and LCS pros.

Although using the Riot Games match v5 API provides over 100 different metrics per player for over 1000 metrics per game, the LoLWatcher V2 model only uses 63 metrics which can be consistently read by Tesseract OCR during the live LCS broadcast. These include team objectives including total team kills, towers taken, first tower bonus, barons taken, dragons taken and individual stats for each player including minions killed, kills, deaths, and assists.
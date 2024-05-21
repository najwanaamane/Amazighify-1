
# Amazighify: Fine-Tuning SeamlessM4T for Amazigh-Arabic and English Translation

## Overview

Amazighini is an AI-powered project focusing on preserving Amazigh heritage by translating Tachelhit Amazigh dialect speech to Arabic text. The main use cases for this project are educational purposes and facilitating communication between rescue teams and Amazigh speakers in rural areas during disasters. This project fine-tunes the *SeamlessM4T* model using Hugging Face's Transformers library to improve translation accuracy and efficiency.

## Table of Contents

- [Project Structure](#project-structure)
- [Data Pipeline](#data-pipeline)
- [Data Preparation](#data-preparation)
- [Model Fine-Tuning](#model-fine-tuning)
- [Evaluation](#evaluation)
- [Usage](#usage)
- [Future Enhancements](#future-enhancements)
- [Demo](#demo)
- [Links](#links)
- [Contributing](#contributing)
- [License](#license)

## Project Structure


The main files and directories in this project are:

- `fine-tuning_seamless.ipynb`: Jupyter notebook containing the code for fine-tuning the SeamlessM4T model.
- `fine-tuned-seamless-m4t/`: Directory where the fine-tuned models will be saved.
- `dataset_amazigh/`: Directory containing the collected audio recordings and annotations.

## Data Pipeline   

![pipeline](https://github.com/SpixerD/Amazighini/assets/120631086/f641ab54-9eb9-4205-b0d2-6cd0467d96b6)



The data for this project was collected from Amazigh speakers who recorded Arabic phrases translated into Tachelhit Amazigh. The phrases focused on common small talk and frequently used phrases by rescue teams.

### Steps:

1. **Data Collection**: Providing Arabic phrases to Amazigh speakers who recorded their translations in Tachelhit Amazigh.
2. **Organization**: Saving the recorded audio files in a `wav` folder and the corresponding annotations in an `annotations` folder. Each annotation file is a CSV that includes the WAV filenames and their translations in English and Arabic.
3. **Dataset Compilation**: Organizing the entire collection of audio recordings and annotations into a directory named `dataset_amazigh`.

## Data Preparation

The data preparation process involves loading the CSV files into pandas DataFrames, adding full paths to the filenames, and converting the DataFrames to Hugging Face datasets. Additionally, preprocessing is performed to ensure the data is in the correct format for model training.

### Steps:

1. **Loading CSV Files**: Reading the CSV files containing the training and evaluation data.
2. **Adding Full Paths**: Ensuring the filenames have full paths so that the audio files can be correctly accessed.
3. **Converting to Datasets**: Converting the pandas DataFrames to Hugging Face datasets.
4. **Preprocessing**: Performing necessary preprocessing steps such as normalizing the audio data, tokenizing the text, aligning the audio with the corresponding text annotations, and adding padding to ensure uniform length across all files.

## Model Fine-Tuning

The model fine-tuning process involves setting up the SeamlessM4T model and training it with the prepared datasets.

### Steps:

1. **Importing Libraries**: Importing necessary libraries from Hugging Face.
2. **Loading Model and Processor**: Loading the SeamlessM4T model and processor.
3. **Defining Training Arguments**: Setting up training arguments using `Seq2SeqTrainingArguments`.
4. **Training Model**: Using `Seq2SeqTrainer` to train the model.

## Evaluation

Evaluating the model's performance on the test dataset to ensure its accuracy and efficiency.

Steps:
Loading Test Data: Loading the test dataset.  
Evaluating Model: Using the trained model to generate translations and comparing them with the ground truth using WER (Word Error Rate).


## Usage

To use the fine-tuned model for translation tasks, load the model and processor, and input the speech or text you want to translate.

```python
# Load the fine-tuned model
model = SeamlessM4TModel.from_pretrained('./models')
processor = AutoProcessor.from_pretrained('./models')

# Perform translation
input_text = "Input speech or text in Amazigh"
translated_text = model.generate(input_text)
print(translated_text)
```

## Future Enhancements

Future enhancements to this project may include:

- **Using PEFT**: Incorporating Parameter-Efficient Fine-Tuning (PEFT) methods to further optimize the model's performance.
- **Exploring Better Performing Models**: Exploring and integrating more advanced models for improved translation accuracy and efficiency.
- **Expanding the Dataset**: Collecting and annotating more diverse datasets to enhance the model's robustness.

## Demo

![interface](https://github.com/SpixerD/Amazighini/assets/120631086/53361db8-5437-416f-ac89-20d628d414ff)


- [Video Demo] https://drive.google.com/file/d/1ggCiGUbni3VET-tzonltsn7N1fH8X0Ip/view?usp=sharing

## Links

- [Notebook](https://huggingface.co/spaces/ThinkAI-Morocco/Amazighini)
- [Canva](https://www.canva.com/design/DAGFoKNyRTg/F_f4-X_WwRWIBf2O7ywFWw/edit?utm_content=DAGFoKNyRTg&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)


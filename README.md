# Handwritten Notes to Editable Documents

## Project Overview

This project builds an AI-powered pipeline to convert handwritten notes containing digits and English letters into editable digital documents (.docx or .pdf). The system leverages a convolutional neural network trained on the EMNIST dataset, image segmentation techniques, and text postprocessing, including spellchecking and language correction.

### Features

- Handwritten character recognition (digits + uppercase and lowercase letters)
- Image preprocessing and character segmentation
- Text reconstruction preserving line structure
- Spellcheck and optional grammar correction using language models
- Export output as editable .docx or .pdf files
- Optional fallback using Tesseract OCR for printed text
- Simple Streamlit web app for interactive testing
- Workflow orchestration using Apache Airflow for batch processing

## Tech Stack

| Purpose             | Technology                  |
|---------------------|-----------------------------|
| Deep Learning       | PyTorch                     |
| Image Processing    | OpenCV, Pillow              |
| OCR Fallback        | Tesseract                   |
| Spellchecking       | pyspellchecker, SymSpell    |
| Language Correction | Transformers (GPT-2)        |
| Document Generation | python-docx, fpdf           |
| Web UI              | Streamlit                   |
| Workflow Orchestration | Apache Airflow             |

## Getting Started

### Prerequisites

- Python 3.8+
- Install dependencies:

```bash
pip install -r requirements.txt
````

### Running Training

Train the CNN model on the EMNIST dataset:

```bash
python src/train.py
```

### Running Prediction

Predict handwritten characters on a sample image:

```bash
python src/predict.py --input data/test_samples/note1.png
```

### Running the Streamlit App

Start the web app to upload handwritten notes and download editable documents:

```bash
streamlit run app/streamlit_app.py
```

## Project Structure

```
handwritten-doc-converter/
├── data/
│   ├── emnist/
│   └── test_samples/
├── model/
│   └── trained_model.pth
├── src/
│   ├── model.py
│   ├── train.py
│   ├── segment.py
│   ├── predict.py
│   ├── postprocess.py
│   ├── doc_generator.py
│   └── utils.py
├── app/
│   └── streamlit_app.py
├── airflow/
│   └── handwritten_pipeline_dag.py
├── notebook/
│   └── EDA_EMNIST.ipynb
├── requirements.txt
├── README.md
└── .gitignore
```

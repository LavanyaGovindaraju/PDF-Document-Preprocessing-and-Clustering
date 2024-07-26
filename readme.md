# PDF Document Processing Suite

## Overview

This suite contains three main tasks related to PDF document processing:

1. **PDF Page Rotation Angle Detection**: Detects the rotation angle of each page in a PDF document.
2. **PDF Page Classification**: Classifies each page of a PDF document into predefined categories.
3. **PDF Document Partitioning**: Partitions a PDF document into sections based on content.

## Table of Contents

1. [Installation](#installation)
2. [Usage](#usage)
    - [Task 1: PDF Page Rotation Angle Detection](#task-1-pdf-page-rotation-angle-detection)
    - [Task 2: PDF Page Classification](#task-2-pdf-page-classification)
    - [Task 3: PDF Document Partitioning](#task-3-pdf-document-partitioning)
3. [License](#license)

## Installation

To install the necessary dependencies for running the projects, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/pdf-processing-suite.git
    cd pdf-processing-suite
    ```

2. Create a virtual environment with Python 3.8:
    ```bash
    python3.8 -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

4. Install Tesseract OCR:
    - **Windows**:
        - Download the Tesseract installer from [here](https://github.com/UB-Mannheim/tesseract/wiki).
        - Run the installer and follow the instructions.
    - **macOS**:
        ```bash
        brew install tesseract
        ```
    - **Linux**:
        ```bash
        sudo apt-get install tesseract-ocr
        ```

## Usage

### Task 1: PDF Page Rotation Angle Detection

This task involves detecting the rotation angle of each page in a PDF document.

1. **Notebook**: `Task1 - PDF Page Rotation Angle Detection.ipynb`
2. **Description**: The notebook processes each page of the PDF and identifies its rotation angle.
3. **Methods**:
    - **Library Imports**: Required libraries include PyMuPDF for PDF handling, PIL for image processing, NumPy for numerical operations, and scikit-learn for PCA.
    - **Text Analysis**: Analyze text blocks to identify headers, footers, and watermarks.
    - **OCR and PCA**: Use Tesseract OCR and PCA to determine the rotation angle if text analysis is insufficient.
    - **Normalization**: Normalize the rotation angle to be within the range [0, 359] degrees.

### Task 2: PDF Page Classification

This task involves classifying each page of a PDF document into predefined categories.

1. **Notebook**: `Task 2 - Classify PDF Pages.ipynb`
2. **Description**: The notebook analyzes each page of a PDF document and classifies them as:
    - Machine-readable
    - Non-machine readable but OCR-able
    - Non-machine readable and not OCR-able
3. **Methods**:
    - **Library Imports**: Required libraries include PyMuPDF for PDF handling, PyPDF2 for reading PDF files, pytesseract for OCR, and PIL for image handling.
    - **Loading PDF**: Load the PDF document using `fitz.open()` and `PdfReader()`.
    - **Classify Pages**: Each page is processed to determine if it contains machine-readable text, can be OCR-processed, or is not OCR-able:
        - **Machine-readable**: Pages with extractable text.
        - **OCR-able**: Pages without machine-readable text but contain text recognizable by OCR.
        - **Not OCR-able**: Pages where both machine-readable text extraction and OCR fail.
    - **OCR Processing**: Use Tesseract to extract text from page images if machine-readable text is not found.

### Task 3: PDF Document Partitioning

This task involves partitioning a PDF document into sections based on content.

1. **Notebook**: `Cherry on the Cake Task -PDF Document Partitioning.ipynb`
2. **Description**: The notebook partitions the document into different sections.
3. **Methods**:
    - **Library Imports**: Required libraries include PyMuPDF for PDF handling, NumPy for numerical operations, scikit-learn for clustering, TfidfVectorizer for text feature extraction, and PIL for image processing.
    - **Extract Features**: Extract visual features such as color, text, and layout complexity from each page.
    - **Text Feature Extraction**: Use TfidfVectorizer to convert text features (header, footer, watermark text) into numerical vectors.
    - **Clustering for Partitioning**: Use KMeans clustering to partition the document based on content similarity.
    - **Save Features**: Save the features of each page to a CSV file.
    - **Determine Optimal Clusters**: Use the Elbow Method and silhouette scores to determine the optimal number of clusters.


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.




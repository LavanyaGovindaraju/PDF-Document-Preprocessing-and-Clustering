# PDF Document Processing Suite

## Overview

A modular suite for intelligent PDF document processing, including automatic rotation correction, page-level classification, and content-aware partitioning. This toolkit is ideal for digitization workflows, archival analysis, and downstream automation pipelines.

## Table of Contents

1. [Installation](#installation)
2. [Capabilities & Workflow](#-capabilities--workflow)
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

3. Install dependencies:
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

## Capabilities & Workflow

### Rotation Correction

This module identifies and normalizes the orientation of each page in a PDF document. It uses a combination of:

1. **Text block analysis** to detect headers, footers, and layout symmetry

2. **Tesseract OCR** and **PCA** when textual cues are insufficient

**Output**: Rotation angles normalized to [0, 359] degrees per page

### Page-Level Classification

Each PDF page is analyzed and classified into one of three categories:

1. **Machine-readable**: Extractable text is detected directly

2. **OCR-compatible**: No extractable text, but recoverable via OCR

3. **Unprocessable**: Neither extractable nor OCR-detectable content

This classification enables adaptive processing strategies for mixed-content PDFs.

### Content-Based Partitioning

The final module segments the document into coherent sections based on visual and textual patterns:

1. Extracts **features** like layout complexity, font density, headers, and watermarks
   
2. Converts page-level text into **TF-IDF vectors**
   
3. Uses **KMeans clustering** to group similar pages
   
4. Determines optimal cluster count using **elbow method** and **silhouette analysis**
   
**Output**: Cluster assignments and a summary CSV of page features
## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

# Ref-TABMNet: Reference-Aware, Parameter-Efficient TabNet Ensembles for Practical Phishing Detection

Ref-TABMNet is an advanced phishing detection system leveraging reference-aware TabNet ensembles. It provides real-time risk assessment for URLs, integrates with browser extensions, and offers a modular, scalable architecture for research and deployment.

## Features

- **Phishing Detection API** – FastAPI-based backend for real-time URL risk scoring.
- **Browser Extension** – Chrome extension warns users before visiting suspicious links.
- **Feature Engineering** – Extracts lexical, statistical, and reference-aware features from URLs.
- **Reference-Aware Models** – Uses TabNet ensembles with reference feature heuristics.
- **Web-Based Tools** – Includes web checker and popup UI for manual URL inspection.
- **Validation & Testing** – Integrated unit tests and validation scripts for robust development.
- **Modular Architecture** – Clean separation of preprocessing, feature extraction, model training, and serving.

Browser Extension Interface:
<img width="1586" height="897" alt="image" src="https://github.com/user-attachments/assets/15e3e61f-ca9a-4ab3-b26d-a4a5ebdb2451" />

API Endpoint (Prior Extension Creation):
<img width="857" height="961" alt="image" src="https://github.com/user-attachments/assets/b01e79e7-a4b6-44ef-8efa-9cd66c2f958c" />

Model Design:
<img width="1028" height="577" alt="image" src="https://github.com/user-attachments/assets/8435c68b-1f85-4f40-bb70-0b42a7e780d7" />

Model Evaluation:
<img width="778" height="566" alt="image" src="https://github.com/user-attachments/assets/58af0e8f-abbb-47cc-a819-11f9653429d7" />
<img width="797" height="581" alt="image" src="https://github.com/user-attachments/assets/e7d07305-4703-4917-9689-9c4bfeda0045" />

## Project Structure

```
Ref_TabMNet/
│-- preprocessing.py                # Script for feature engineering from raw URL data
│-- requirements.txt                # Python dependencies
│
├── data/
│   ├── raw/
│   │   └── Phishing_URL_Dataset.csv        # Raw dataset
│   └── processed/
│       └── processed_phishing_urls.csv     # Feature-engineered dataset
│
├── extension/
│   ├── background.js               # Chrome extension background logic
│   ├── content.js                  # Annotates suspicious links on pages
│   ├── interstitial.html           # Block page for risky URLs
│   ├── interstitial.js             # Logic for interstitial page
│   ├── manifest.json               # Chrome extension manifest
│   ├── popup.html                  # Extension popup UI
│   ├── popup.js                    # Popup logic
│   └── icons/                      # Extension icons
│
├── src/
│   ├── __init__.py
│   ├── features/
│   │   ├── __init__.py
│   │   ├── preprocess.py           # Feature extraction utilities
│   │   └── reference_features.py   # Reference-aware feature heuristics
│   ├── serve/
│   │   ├── app.py                  # FastAPI server
│   │   ├── inference.py            # Model inference logic
│   │   └── models/
│   │       ├── tabnet_backbone.py    # TabNet model 
│   │       ├── tabm_adapters.py      # TabNet model adapter
│   │       └── train_ref_tabmnet.py  # Model training script
│   └── utils/
│       └── ...                     # Utility scripts
│
├── web/
│   └── checker.html                # Web-based URL checker
│
└── .vscode/
    └── settings.json               # VSCode workspace settings
```

## Installation & Setup

### 1. Clone the repository

```sh
git clone <repository-url>
cd Ref_TabMNet
```

### 2. Set up a virtual environment

On macOS/Linux:
```sh
python -m venv venv
source venv/bin/activate
```
On Windows:
```sh
python -m venv venv
venv\Scripts\activate.bat
```

### 3. Install dependencies

```sh
pip install -r requirements.txt
```

## Usage

### 1. Preprocess the dataset

```sh
python preprocessing.py
```

### 2. Train the TabNet model

```sh
python -m src.serve.models.train_ref_tabmnet
```

### 3. Start the FastAPI server

```sh
python -m src.serve.app
```

### 4. Use the browser extension

- Load `extension` as an unpacked extension in Chrome.
- The extension will warn/block suspicious URLs using your trained model.

### 5. Manual URL checking

- Open `web/checker.html` in your browser for a simple web-based checker.
- Use the extension popup for quick checks.

## Testing

To run unit tests (if available):

```sh
python -m pytest
```

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m "Add new feature"`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a Pull Request.

For major changes, please open an issue first to discuss your proposal.

---

Ref-TABMNet is designed for practical, scalable phishing detection research and deployment. 

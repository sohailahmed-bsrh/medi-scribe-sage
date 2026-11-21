# MediScribe Sage Clinical Documentation Assistant

## Description
Clinical workflow assistant designed to structure unstructured patient-physician dialogue into standardized clinical SOAP notes and consultation summaries.

## Live Demo
Access the live demonstration and portfolio showcase at: [https://sohail.devsil.com/projects.html](https://sohail.devsil.com/projects.html)

## Tech Stack
- Python 3.10+
- FastAPI
- Speech Recognition
- OpenAI / Gemini API
- Streamlit

## Getting Started

### Prerequisites
- Python 3.10 or higher
- Git version control

### Installation and Setup
1. Clone the repository:
```bash
git clone https://github.com/sohailahmed-bsrh/medi-scribe-sage.git
cd medi-scribe-sage
```

2. Configure environment and dependencies:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env
streamlit run app.py
```

## Architecture and Project Structure
The repository is structured according to modular engineering standards:

```text
medi-scribe-sage/
|-- src/
|-- data/
|-- .gitignore
|-- README.md
`-- requirements.txt
```

## Interface and Verification
The system produces verifiable execution logs, data summaries, or interactive interfaces depending on the execution target. Validate operation by running the test suite or local entrypoint.

## Author
Developed by Sohail Ahmed ([Portfolio](https://sohail.devsil.com) | [GitHub](https://github.com/sohailahmed-bsrh)).

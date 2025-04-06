# PDF Processor Application

This application allows users to upload PDF documents, extract text using OCR, and generate summaries using the Grok X AI API.

## Features

- PDF document upload
- Text extraction using OCR (Magic_pdf / MinerU)
- Text summarization using Grok X AI API
- Simple web interface for uploading and viewing results
- Asynchronous processing with a message queue system
- Amazon S3 storage for documents, extracted text, and summaries
- Docker support for easy deployment
- DynamoDB for storing metadata and processing status
- Amazon SQS for message queuing
- AWS Lambda for serverless processing

## Project Structure

```plaintext
PDF-PROCESSOR
├── README.md                # Project documentation
├── Dockerfile             # Dockerfile for containerization
├── requirements.txt          # Python dependencies
├── deploy.sh                 # Deployment script
├── lambda_handler.py          # AWS Lambda function handler
├── template.yml             # AWS SAM template for Lambda deployment
├── update_templates.py       # Script to update HTML templates
├── update_static_to_s3.py    # Script to update static files to S3
├── pdf-processor/
   ├── __init__.py
   ├── app.py                 # Main application file
   ├── config.py              # Configuration settings
   ├── download_models.hf.py # Script to download models from Hugging Face
   ├── static/
   │   ├── css/
   │   │   └── style.css      # CSS styles for the web interface
   │   └── js/
   │       └── main.js        # JavaScript for the web interface
   ├── templates/
   │   ├── index.html         # HTML template for the upload page
   │   └── results.html       # HTML template for displaying results
   ├── services/
   │   ├── __init__.py
   │   ├── ocr_service.py     # OCR service for text extraction
   │   ├── summary_service.py # Summary service for text summarization
   │   ├── storage_service.py # Storage service for file handling
   │   └── message_service.py # Message service for queue handling
   ├── detectron2/           # Detectron2 models and configurations

```

## Installation

1. Make sure you're using Python 3.7+.

Using Conda is recommended:
```
conda create --name detectron2_env python=3.9
conda activate detectron2_env
```

2. Use the requirements.txt to install all needed packages:
```
pip install -r requirements.txt
```

3. Run the application:
```
python app.py
```

4. Open your web browser and go to `http://localhost:000` to access the application.

## Installation (using Docker)

1. Build the Docker image:
```
docker build -t pdf-processor-lambda .
```

2. Run the Docker container:
```
docker run -p 8000:8000 pdf-processor-lambda
```

# Sensory Health with AI

This Flask application detects diseases related to sensory organs (eye, ear, skin, nose) based on uploaded images using pre-trained machine learning models. The app allows users to upload images, and it uses different models for each organ to predict possible conditions or diseases.

## Features

- Image upload for disease detection (Eye, Ear, Skin, and Nose)
- Individual models for each sensory organ (Eye, Ear, Skin, and Nose)
- Results display with condition classification and confidence level
- Dockerized application for easy deployment

## Requirements

Before running this application, ensure you have the following installed:

- Python 3.9 or later
- Docker (for containerized deployment)
- TensorFlow (for ML models)
- OpenCV (for image processing)

## Installation

### Clone the repository

```bash
git clone https://github.com/yourusername/disease-detection-app.git
cd disease-detection-app
```

### Install dependencies

If you are not using Docker, you can install the necessary dependencies via pip:

```bash
pip install -r requirements.txt
```

If you want to use Docker, skip this step, as the dependencies will be installed inside the Docker container.

## Models

Ensure that you have the following pre-trained models saved as .h5 files:

- `EYE.h5` (Eye Disease Detection Model)
- `EAR.h5` (Ear Disease Detection Model)
- `SKIN.h5` (Skin Disease Detection Model)
- `NOSE.h5` (Nose Disease Detection Model)

These models must be placed in the root directory of the project or adjust the code to point to the correct path.

## Running Locally

### Without Docker (Python environment)

1. Ensure your models are in the correct location.
2. Run the Flask application:

```bash
python app.py
```

This will start the Flask app locally on port 5000. You can access the app at http://localhost:5000.

### With Docker

1. Build the Docker image:

```bash
docker build -t flask-disease-detection .
```

2. Run the Docker container:

```bash
docker run -p 5000:5000 flask-disease-detection
```

This will map port 5000 on your host machine to port 5000 inside the container. You can access the app at http://localhost:5000.

### Running with Custom Port

You can also specify a custom port to run the Flask app. For example:

```bash
docker run -e PORT=8080 -p 8080:8080 flask-disease-detection
```

This will run the app on port 8080.

## Application Endpoints

- `/`: Home page
- `/eye`: Eye disease detection page
- `/ear`: Ear disease detection page
- `/skin`: Skin disease detection page
- `/nose`: Nose disease detection page

Each of these pages allows users to upload an image for disease prediction for the corresponding sensory organ.

## Error Handling

If there are any errors during model loading, image preprocessing, or prediction, the app will display an error message on the error page.

## Deployment

To deploy the Flask app to a cloud provider or server:

1. Build and push the Docker image to a container registry (e.g., Docker Hub, AWS ECR, etc.).
2. Deploy the image on a cloud service like AWS ECS, Google Cloud Run, or Azure App Service.
3. Ensure that the cloud service is configured to expose the correct port (e.g., 5000 or a port you specify).
4. For cloud services, ensure that you configure a reverse proxy (e.g., Nginx) if necessary to route traffic to the correct port.

## Folder Structure

```plaintext
disease-detection-app/
│
├── app.py                # Flask application
├── Dockerfile            # Docker configuration
├── requirements.txt      # Python dependencies
├── uploads/              # Directory to store uploaded images
├── templates/            # HTML templates for the frontend
│   ├── eye_detection.html
│   ├── ear_detection.html
│   ├── skin_detection.html
│   ├── nose_detection.html
│   ├── error.html
│   └── home.html
├── EYE.h5                # Eye disease detection model
├── EAR.h5                # Ear disease detection model
├── SKIN.h5               # Skin disease detection model
└── NOSE.h5               # Nose disease detection model
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

# Diabetes Prediction API

This project implements a FastAPI-based web application to predict whether a person is diabetic based on several input parameters. The prediction is performed using a pre-trained machine learning model.

## Features
- **Endpoint**: `/diabetes_prediction`
  - Accepts a JSON payload containing the input parameters.
  - Returns a prediction indicating whether the person is diabetic or not.
- **Cross-Origin Resource Sharing (CORS)**: Configured to allow requests from any origin.

## Prerequisites
To run this application, ensure you have the following installed:
- Python 3.8 or later
- Required Python libraries (see below)

## Installation and Setup
1. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install Dependencies**
   Install the necessary Python libraries using pip:
   ```bash
   pip install fastapi uvicorn pydantic scikit-learn
   ```

3. **Place the Model File**
   Ensure the pre-trained model file (`diabetes_model.sav`) is located in the project directory. This file should be a serialized machine learning model created with libraries like scikit-learn.

## Running the Application
1. Start the FastAPI server:
   ```bash
   uvicorn main:app --reload
   ```
   - `main` refers to the name of the Python file (e.g., `main.py`).
   - `app` refers to the FastAPI instance created in the code.

2. The application will be accessible at: `http://127.0.0.1:8000`

3. Visit the interactive API documentation at `http://127.0.0.1:8000/docs` to test the endpoints.

## API Endpoint Details
### `/diabetes_prediction`
- **Method**: POST
- **Input**:
  - JSON object with the following fields:
    ```json
    {
        "Pregnancies": int,
        "Glucose": int,
        "BloodPressure": int,
        "SkinThickness": int,
        "Insulin": int,
        "BMI": float,
        "DiabetesPedigreeFunction": float,
        "Age": int
    }
    ```
  - Example:
    ```json
    {
        "Pregnancies": 2,
        "Glucose": 120,
        "BloodPressure": 70,
        "SkinThickness": 25,
        "Insulin": 80,
        "BMI": 28.5,
        "DiabetesPedigreeFunction": 0.5,
        "Age": 35
    }
    ```
- **Response**:
  - `The person is not Diabetic` if the prediction is 0.
  - `The person is Diabetic` if the prediction is 1.

## How It Works
1. **Model Loading**:
   The pre-trained diabetes model (`diabetes_model.sav`) is loaded at the start of the application.

2. **Input Handling**:
   The input parameters are validated using Pydantic and converted into the required format for the model.

3. **Prediction**:
   The processed input is passed to the model to obtain the prediction, which is then returned to the user.

## Dependencies
The project requires the following Python libraries:
- `fastapi`: For creating the web API.
- `uvicorn`: For running the FastAPI server.
- `pydantic`: For data validation.
- `scikit-learn`: For loading the serialized model.

## License
This project is open-source and available under the [MIT License](LICENSE).

## Acknowledgments
- **FastAPI**: Framework for building APIs.
- **scikit-learn**: Library for training and serializing the machine learning model.

## Notes
- Ensure the model file (`diabetes_model.sav`) matches the expected input features and order used in this code.
- Modify the CORS settings if stricter access control is required.

For any issues or contributions, please open a pull request or create an issue on the GitHub repository.

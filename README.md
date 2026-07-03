# Mango Grading Project

This project contains machine learning models and scripts for grading and classifying mangos into three categories (Grade-A, Grade-B, Grade-C).

## Project Structure

- `Mango_Classification.ipynb`: A Google Colab notebook for training a YOLO model using a dataset from Roboflow. It also includes evaluation and a Gradio web interface.
- `Mango_classificate_camera.ipynb`: A local Python notebook that uses a trained YOLO model and OpenCV to track mangos via webcam and count them as they cross a specific region, logging the results to `total.csv`.
- `models/`: Directory to store your trained YOLO weights (`best.pt`, `yolo11n.pt`, etc.). Note: `.pt` files are ignored by git due to their size.
- `datasets/`: Directory for your training/testing images and labels.
- `output/`: Directory for output logs, predictions, and `total.csv`.
- `runs/`: Directory where Ultralytics YOLO saves its training/validation runs.

## Setup Instructions

1. **Install Dependencies**:
   ```bash
   pip install ultralytics opencv-python numpy pandas matplotlib gradio roboflow albumentations==1.4
   ```

2. **Models**:
   Place your trained model weights (e.g., `best.pt`, `yolo11n.pt`) inside the `models/` directory before running the camera script.

3. **Running the Camera Script**:
   Open `Mango_classificate_camera.ipynb` in Jupyter Notebook or VS Code, ensure your webcam is connected, and run the cells to start tracking.

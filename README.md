# Mango Grading Project

This project contains machine learning models and scripts for grading and classifying mangos into three categories: **Grade-A, Grade-B, and Grade-C**. It features both a web interface for static image/video uploads and a real-time tracking system via webcam.

## 🛠 Tools & Technologies Used
- **[Ultralytics YOLO (v8/v11)](https://github.com/ultralytics/ultralytics)**: For training the object detection model and real-time tracking.
- **[OpenCV](https://opencv.org/)**: For webcam video stream capture and image processing.
- **[Roboflow](https://roboflow.com/)**: For dataset management and downloading annotated mango images.
- **[Gradio](https://gradio.app/)**: For building a user-friendly web interface to test images and videos.
- **[Pandas](https://pandas.pydata.org/) & [Matplotlib](https://matplotlib.org/)**: For data logging (saving counts to `total.csv`) and visualizing charts.
- **Python & Jupyter Notebooks**: The core programming language and environment.

## 📁 Project Structure
- `Mango_Classification.ipynb`: A Google Colab notebook for training a YOLO model using a dataset from Roboflow. It also includes evaluation and a Gradio web interface.
- `Mango_classificate_camera.ipynb`: A local Python notebook that uses a trained YOLO model and OpenCV to track mangos via webcam and count them as they cross a specific region, logging the results to `total.csv`.
- `models/`: Directory to store your trained YOLO weights (`best.pt`, `yolo11n.pt`, etc.). Note: `.pt` files are ignored by git due to their size.
- `datasets/`: Directory for your training/testing images and labels.
- `output/`: Directory for output logs, predictions, and `total.csv`.
- `runs/`: Directory where Ultralytics YOLO saves its training/validation runs.

## 🚀 How to Use the Project

### Part 1: Real-Time Mango Counting (Webcam)
This part is meant to be run locally on your computer with a connected camera.

1. **Install Dependencies**:
   Open your terminal and install the required Python libraries:
   ```bash
   pip install ultralytics opencv-python numpy pandas matplotlib
   ```
2. **Prepare the Model**:
   Place your trained model weights (e.g., `best.pt` or `yolo11n.pt`) inside the `models/` directory.
3. **Run the Notebook**:
   - Open `Mango_classificate_camera.ipynb` in Jupyter Notebook or VS Code.
   - Run the cells sequentially.
   - A window will pop up showing your webcam feed. When mangos pass through the drawn region, they will be counted by their grade (A, B, C).
   - The final counts will be saved into `output/total.csv` and visualized using a bar chart at the end of the notebook.
   - Press `q` to stop the webcam feed.

### Part 2: Training and Web Interface (Google Colab)
This part is optimized for Google Colab to utilize free GPUs for training.

1. **Open in Colab**: Upload `Mango_Classification.ipynb` to Google Colab.
2. **Mount Google Drive**: Run the first cell to mount your Drive so you can save trained models.
3. **Download Dataset**: Use the provided Roboflow API cell to download the `MangoGrading_Merge-6` dataset.
4. **Train the Model**: Run the YOLO `detect train` commands. The trained weights will be saved to the `runs/` folder and can be copied to your Google Drive.
5. **Start Gradio Web App**: 
   - Run the Gradio cells near the bottom. 
   - A public web link will be generated. You can click the link to open a webpage where you can upload photos or videos of mangos and see the model's grading predictions instantly.

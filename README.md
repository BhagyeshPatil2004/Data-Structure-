# Ultra-Fast YOLOv11 Training & Inference 🚀  

Ultra-fast YOLOv11 setup for **Person, Cars, and Stop Signs** detection with optional **distance estimation**.  
Supports **multi-dataset auto-combination**, **training**, and **Streamlit-based visualization**.  

---

## 📂 Features
- **Dataset Auto-Combiner**  
  - `ultra_fast_yolo11.py` merges multiple YOLO-format datasets.  
  - Automatically unifies classes and generates `combined_dataset/data.yaml`.  

- **Training**  
  - Trains YOLOv11n on combined data.  
  - Outputs saved at:  
    ```
    ultra_fast_yolo11/yolo11n/weights/best.pt
    ```  

- **Inference**  
  - **Streamlit App** → `streamlit_test_image.py`  
    - Runs object detection.  
    - Optional **distance estimation** → set **camera VFOV** + known object heights.  
    - Labels displayed as:  
      ```
      Stop Sign, 2.1m
      ```  
    - Example detections:  
      ![Detection](assets/detection_result.jpg)  

  - **CLI Tester** → `test_image.py`  
    ```bash
    python test_image.py --weights ultra_fast_yolo11/yolo11n/weights/best.pt --img path/to/image.jpg --conf 0.15
    ```  

- **Pretrained Weights**  
  - Base weights included → `yolo11n.pt`  
  - Your trained weights saved under → `ultra_fast_yolo11/yolo11n/weights/`  

---

## 📁 Project Structure
```
├── datasets/                # Place raw datasets here
├── combined_dataset/        # Auto-generated unified dataset
├── ultra_fast_yolo11/
│   ├── yolo11n/weights/     # Training outputs (best.pt, last.pt)
│   ├── ultra_fast_yolo11.py # Dataset combiner + trainer
├── streamlit_test_image.py  # Streamlit app (detection + distance)
├── test_image.py            # Quick inference script
├── yolo11n.pt               # Pretrained YOLOv11 base weights
```

---

## ⚙️ Requirements
- Python 3.9+  
- [Ultralytics](https://github.com/ultralytics/ultralytics)  
- PyTorch  
- Streamlit  

Install dependencies:
```bash
pip install -r requirements.txt
```

---

## ▶️ Usage

### 🔹 Training
```bash
python ultra_fast_yolo11.py
```

### 🔹 Run Streamlit App
```bash
streamlit run streamlit_test_image.py
```

### 🔹 Quick CLI Inference
```bash
python test_image.py --weights ultra_fast_yolo11/yolo11n/weights/best.pt --img path/to/image.jpg --conf 0.15
```

---

## 📸 Example Outputs
- **YOLOv11 Detection**  
  Screenshot 2025-08-25 161242.png

- **Distance Estimation**  
  Screenshot 2025-08-25 161249.png 

---

## 📝 Notes
- Adjust **confidence threshold** inside the app for better results.  
- Set **camera FOV** & **object heights** for distance estimation.  
- Data should be in YOLO format under `datasets/`.  

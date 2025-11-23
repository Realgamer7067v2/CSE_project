# Extraction Of Text from Image/Screen using Machine Vision

Using pre-trained models like paddleocr to process a Image to extract potentially usefull data.This Script Captures the Screen Using Pillow(PIL)'s ImageGrab. Than uses PaddleOCR to Extract all the available text.

## Features
- Full-screen capture via Pillow `ImageGrab`
- Text detection & recognition using PaddleOCR (PP-OCRv5 mobile models)
- Bounding box + label overlay rendered with OpenCV
- Processing time measurement for performance analysis

## Technologies/tools Used
- It uses Paddleocr a highly trained and accurate model with multilangual support for over 109 languages.
- We have furthur used a mobile model to improve the processing time of the image.
- This Script uses PP-OCRv5_mobile_det for text detection and PP-OCRv5_mobile_rec to provide most fastest and accurate results.
- Using the Paddle mobile models we were able to achive image processing of 0.8 sec on a testbench.


## Tech Stack
- Python 3.10+ (recommended)
- Paddle-gpu (3.2.0 recommended)
- PaddleOCR
- Pillow
- NumPy
- OpenCV (cv2)

## Prerequisites
Install Python and ensure `pip` is available on your PATH.
On Windows you may need Visual C++ Build Tools for some packages.

- Your also need to install CUDA toolkit and CuDNN in your enviroment.This is required by the Paddle to do the calculations on the GPU

## Installation
```powershell
# (Optional) create and activate a virtual environment
python -m venv .venv; .\.venv\Scripts\activate

# Upgrade pip
python -m pip install --upgrade pip

# Install dependencies
pip install -r requirements.txt
```

## Usage
```powershell
python main.py
```
The script will:
1. Capture the current screen.
2. Run OCR prediction.
3. Draw bounding boxes + recognized text.
4. Display the annotated image in an OpenCV window.
Press any key in the window to close.

## Configuration
Adjust OCR initialization in `main.py`:
```python
ocr = PaddleOCR(lang='en', use_textline_orientation=False,
                text_detection_model_name="PP-OCRv5_mobile_det",
                text_recognition_model_name="PP-OCRv5_mobile_rec",
                use_doc_orientation_classify=False,
                use_doc_unwarping=False,
                return_word_box=True)
```
Potential changes:
- Set `lang='en'` to other supported languages.
- Enable orientation or document unwarping for scanned docs.
- Switch to server or lightweight models per performance needs.

## Performance Notes
- Full-screen capture + OCR can be GPU intensive.
- Consider adding region capture (e.g., specific coordinates) for faster throughput.
- You can batch successive frames to avoid re-initializing the model.

## Project Structure (Current / Suggested)
```
Real_CSE_Project/
  main.py              # Entry point
  README.md            # Documentation
  requirements.txt     # Dependencies
```


## Acknowledgments
- [PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR) project
- OpenCV community


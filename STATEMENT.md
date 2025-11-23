# Problem Statement

Extract the text from a image/screenshot/document to a machine readable format.

## Scope of the project
- Core Function: Single screenshot capture of full desktop, run PaddleOCR (PP-OCRv5 mobile det + rec, English) to get words, confidence scores, and bounding boxes.
- Processing: Minimal post-processing; directly iterates recognized items; draws green rectangles and puts raw text above each box.
- Performance Feedback: Prints one timing metric (end-to-end `ocr.predict` duration). No profiling of preprocessing or rendering.
- Data Handling: Results only visualized; nothing saved to disk, clipboard, or returned as structured export.
- Configuration Choices: Orientation classification and document unwarping explicitly disabled; using word-level boxes (`return_word_box=True`).
- Interaction Model: One-shot run; no loop, hotkey, region selection, or window targeting; exits after keypress.
- Limitations: English only, no confidence threshold filtering, no error handling for empty results, no GPU/config toggles, no scaling/resizing for speed.
- Immediate Extension Opportunities: Add loop for continuous monitoring, confidence threshold, JSON/CSV export, region/window capture, optional downscale for speed, multi-language support, graceful handling when result list is empty.

## Taget User
- Business Employs who want to extract data for handwritten notes or other documents like PDF to a machine readable format.
- Data Analysist who need to work with many time of different data and need to convert it to 1 type.

## High Level Features
- Full-screen capture via Pillow `ImageGrab`
- Text detection & recognition using PaddleOCR (PP-OCRv5 mobile models)
- Bounding box + label overlay rendered with OpenCV
- Processing time measurement for performance analysis
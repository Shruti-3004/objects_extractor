# 🎥 Product & Brand Detection from Videos using OpenAI Vision

This project automatically detects and identifies **branded products** from **video scenes** using OpenCV for scene change detection and OpenAI’s GPT-4o vision model for product classification. It is tailored for retail analysis, advertising intelligence, and consumer research.

---

## 📦 Features

* 🔍 Scene change detection using histogram correlation
* 🧠 Product recognition using OpenAI's GPT-4o (Vision model)
* 🧹 Deduplication and normalization of product names
* 🧾 Results are saved in a CSV with a log of processed videos
* ♻️ Skips reprocessing already analyzed videos
* ⚠️ Handles errors gracefully with informative feedback

---

## 🧰 Requirements

* Python 3.8+
* An OpenAI API key with access to `gpt-4o` vision model

---

## 📁 Folder Structure

```
.
├── videos/                      # Input folder containing video files
│   └── maybelline_ad.mp4       # Example video
├── detected_objects.csv        # Output CSV (auto-generated)
├── main.py                     # Main pipeline script
├── .env                        # File containing your OpenAI API key
└── README.md                   # This file
```

---

## 🔑 Setup Instructions

### 1. Clone or copy the project

### 2. Place your videos in the `videos/` folder

Make sure your video filenames start with a keyword like `may` (e.g., `maybelline_ad.mp4`) to match the current file glob pattern in the script.

### 3. Add your OpenAI API key

Create a `.env` file in the root directory with the following:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

### 4. Run the code

Run the script with:

```bash
python main.py
```

The output will be saved to `detected_objects.csv`.

---

## 📊 Output

The script creates/updates the `detected_objects.csv` file with the following columns:

| video                 | products                                                       |
| --------------------- | -------------------------------------------------------------- |
| videos/maybelline.mp4 | Maybelline Super Stay Foundation, Maybelline Fit Me Blush, ... |

---

## ⚙️ Customization

### 🔄 Adjust Scene Change Sensitivity

Modify the threshold in `is_scene_change()`:

```python
if is_scene_change(prev_frame, gray, threshold=0.8):
```

Lower threshold → more sensitive to changes
Higher threshold → less sensitive

### 🧠 Modify the Prompt

You can tune the `prompt` inside `identify_objects()` to make it stricter or more lenient depending on the product categories you’re targeting.

---

## 🚨 Error Handling

* Videos already analyzed are **skipped** to avoid redundancy
* If a video fails during processing, the error is printed with a message
* Vision API errors are caught and handled safely

---

## 📌 Limitations

* Requires stable internet connection and OpenAI API usage quota
* GPT-based vision detection can sometimes hallucinate — consider adding additional filters if needed
* OCR is not used; the system relies purely on vision-language inference

---

## 🧠 Potential Enhancements

* Add OCR fallback using PaddleOCR or EasyOCR
* Integrate object detectors (e.g., YOLO) for region proposals before LLM call
* Add GUI or web interface to explore processed data
* Add product image thumbnails in CSV for review

---
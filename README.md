# objects_extractor

Scene-Based Brand Detection using AI

This project detects **scene changes in a video** and uses **OpenAI's Vision model (GPT-4o)** to extract **branded or commercial products** visible in each scene.

---

## 📽️ What It Does

1. **Scene Detection**  
   Splits a video into keyframes by detecting significant scene changes using OpenCV histogram comparison.

2. **Product Detection**  
   Each detected scene is analyzed using OpenAI Vision API to identify visible **commercial products and brands**.

3. **Result Output**  
   Stores results in a structured CSV file with image-frame-to-product mapping.

---

## 📁 Folder Structure


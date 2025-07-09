# 🎬 Educational Video Visualizer – Transcript-to-Image Overlay Pipeline

This notebook takes an educational video and automatically enhances it by:

1. **Transcribing the speech** using OpenAI’s Whisper model.
2. **Identifying the most visually descriptive or conceptually rich moments** in the video using a large language model (LLM) like DeepSeek or Mistral.
3. **Generating images** from those moments using Stable Diffusion.
4. **Overlaying the generated images** at the right timestamps in the video to improve engagement and understanding.

---

## 📦 Features

- ✅ Converts video to audio in-memory using `ffmpeg`
- ✅ Transcribes using Whisper (`base` model)
- ✅ Extracts most visualizable ideas via a prompt to an LLM
- ✅ Parses the LLM response into structured segments
- ✅ Uses Stable Diffusion (`CompVis/stable-diffusion-v1-4`) to generate matching images
- ✅ Overlays generated images on video using MoviePy

---

## 📁 Files

- `Notebook.ipynb` – Main notebook containing all logic
- `E:/course.mp4` – Sample input video (you should replace with your own)

---

## 🚀 How to Run

### 1. 🔧 Install Requirements

Make sure you are using a Python environment with GPU access.

```bash
pip install -r requirements.txt

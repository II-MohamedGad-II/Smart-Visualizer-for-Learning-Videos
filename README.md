# 🎬 Educational Video Visualizer – Transcript-to-Image Overlay Pipeline

This notebook takes an educational video and automatically enhances it by:

1. **Transcribing the speech** using OpenAI’s Whisper model.
2. **Identifying the most visually descriptive or conceptually rich moments** in the video using a large language model (LLM) like DeepSeek or Mistral.
3. **Generating images** from those moments using Stable Diffusion.
4. **Overlaying the generated images** at the right timestamps in the video to improve engagement and understanding.

---
- Input Sample: https://drive.google.com/file/d/1_7vdCyQBA0rj40-PudVQ1M1NxmL5apwI/view?usp=sharing
- Output: https://drive.google.com/file/d/1950SfGDCOJ7fqDrWpbcGWIneqolX4n32/view?usp=sharing
---

## 📦 Features

- ✅ Converts video to audio in-memory using `ffmpeg`
- ✅ Transcribes using Whisper (`base` model)
- ✅ Extracts most visualizable ideas via a prompt to deepseek-V3
- ✅ Parses the deepseek response into structured segments
- ✅ Uses Stable Diffusion (`CompVis/stable-diffusion-v1-4`) to generate matching images
- ✅ Overlays generated images on video using MoviePy

---

## 📁 Files

- `Smart Visualizer.ipynb` – Main notebook containing all logic
- `requirements.txt` – Required libraries to run the code

---

## 🚀 How to Run

### 1. 🔧 Install Requirements

Make sure you are using a Python environment with GPU access.

```bash
pip install -r requirements.txt
```

### 2. 🤖 Log into Hugging Face (if using DeepSeek or gated LLMs)
If you're using DeepSeek or LLaMA models:

```bash
huggingface-cli login
```
Or in code:

```python
from huggingface_hub import login
login(token="hf_...")
```

### 3. 📥 Upload a Video
Replace the line below with your video path:

```python
video_file = "/video/path.mp4"
```
### 4. ▶️ Run the Notebook
The notebook will:
- Transcribe the video
- Ask the language model for key moments to visualize
- Generate images for those moments
- Overlay the images into the video timeline

## 🧠 How the Model Picks Moments
We prompt the LLM with a detailed instruction like:

“Find the most conceptually rich or visually descriptive moments in this transcript... Return a JSON list of moments with start/end timestamps and image suggestions.”

This ensures the image generation is focused on teachable concepts, examples, or illustrative definitions — not just random dialogue.

## 📤 Output
The final output is a video clip with educational illustrations embedded at the right time.

Use .write_videofile("output.mp4") at the end of the notebook if you want to save the result:

python
Copy
Edit
final_clip.write_videofile("enhanced_video.mp4")

## 🔐 Notes
Whisper works on CPU, but GPU is strongly recommended for speed.

Stable Diffusion requires a GPU (VRAM ≥ 8GB recommended).

The LLM component (e.g., DeepSeek or Mistral) must be downloaded from Hugging Face.

You can swap the LLM model (deepseek, mistral, etc.) easily by changing the MODEL_NAME.

## 🙋 FAQ
❓ I don’t have a powerful GPU, can I still use this?
Yes, but image generation and transcription will be much slower. Consider using Google Colab Pro or a RunPod GPU.

❓ Can I use this with Arabic videos?
Yes — Whisper supports multilingual transcription, and you can customize prompts in Arabic to guide the image generation.

## 📫 Contact
Built by [Your Name Here]
For inquiries, reach out via Upwork or GitHub.

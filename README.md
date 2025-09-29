# Eccentric GenAI Intern Assignment

This repository contains my submission for the **GenAI Intern Assignment** at **Eccentric**.  
The task was to generate photorealistic images of three locations, each from three unique camera angles, using **Stable Diffusion XL (SDXL)**.

---

## 📂 Repository Structure

```
eccentric-assignment/
│
├── notebook.ipynb # Jupyter/Colab notebook with full code
├── README.md # Project documentation
├── eccentric_outputs/ # Generated outputs
│ ├── Bandra_Worli_Sea_Link/
│ │ ├── Bandra_Worli_Sea_Link_view_1.png
│ │ ├── Bandra_Worli_Sea_Link_view_2.png
│ │ └── Bandra_Worli_Sea_Link_view_3.png
│ ├── Hawa_Mahal_Jaipur/
│ │ ├── Hawa_Mahal_Jaipur_view_1.png
│ │ ├── Hawa_Mahal_Jaipur_view_2.png
│ │ └── Hawa_Mahal_Jaipur_view_3.png
│ ├── Nagpur_Rainforest/
│ │ ├── Nagpur_Rainforest_view_1.png
│ │ ├── Nagpur_Rainforest_view_2.png
│ │ └── Nagpur_Rainforest_view_3.png
│ └── metadata.json # Seeds, prompts, reproducibility metadata
```

---

## 🛠️ Workflow & Pipeline

### 1. Dataset & Prompt Curation
- Selected **three locations**:
  - Bandra Worli Sea Link (Mumbai)
  - Hawa Mahal (Jaipur)
  - Nagpur Rainforest
- Designed **3 unique prompts per location** to capture multiple angles and lighting.
- Example prompt:  
  *"Wide-angle shot of Hawa Mahal, Jaipur, during sunset with natural lighting, HDR style, photorealistic."*

### 2. Model Selection
- **Base Model**: `stabilityai/stable-diffusion-xl-base-1.0`  
  - Chosen for its higher resolution and detail compared to SD v1.5.
- **Scheduler**: `UniPCMultistepScheduler`  
  - Ensures faster convergence and stable image generation.
- **(Optional extension)**: LoRA fine-tuning (e.g., *Realistic Vision*) can be applied to increase realism further.

### 3. Pipeline Setup
- Implemented using the **Hugging Face Diffusers** library.
- Key parameters:
  - `guidance_scale = 7.5` → balances creativity vs prompt adherence.
  - `num_inference_steps = 50` (sometimes 70 for sharper details).
- Fixed **random seeds** for reproducibility.

### 4. Image Generation
- For each location:
  - 3 curated prompts executed.
  - 3 unique images generated.
- Images saved in structured folders under `eccentric_outputs/`.
- Metadata (prompts + seeds) stored in `metadata.json`.

### 5. Observations
- **SDXL** produces high-quality, sharp outputs, though realism depends heavily on prompt engineering.
- Increasing inference steps (50 → 70) improves detail but not always realism.
- Future improvements:
  - Use **LoRA models** like *Realistic Vision* for more photorealistic results.
  - Experiment with **ControlNet** for consistent camera angles and poses.
  - Integrate an **upscaler** (e.g., Real-ESRGAN) for 4K fidelity.

---

## 📸 Sample Outputs

### Bandra Worli Sea Link
![Sea Link View 1](eccentric_outputs/Bandra_Worli_Sea_Link/Bandra_Worli_Sea_Link_view_1.png)  
![Sea Link View 2](eccentric_outputs/Bandra_Worli_Sea_Link/Bandra_Worli_Sea_Link_view_2.png)  
![Sea Link View 3](eccentric_outputs/Bandra_Worli_Sea_Link/Bandra_Worli_Sea_Link_view_3.png)  

### Hawa Mahal
![Hawa Mahal View 1](eccentric_outputs/Hawa_Mahal_Jaipur/Hawa_Mahal_Jaipur_view_1.png)  
![Hawa Mahal View 2](eccentric_outputs/Hawa_Mahal_Jaipur/Hawa_Mahal_Jaipur_view_2.png)  
![Hawa Mahal View 3](eccentric_outputs/Hawa_Mahal_Jaipur/Hawa_Mahal_Jaipur_view_3.png)  

### Nagpur Rainforest
![Rainforest View 1](eccentric_outputs/Nagpur_Rainforest/Nagpur_Rainforest_view_1.png)  
![Rainforest View 2](eccentric_outputs/Nagpur_Rainforest/Nagpur_Rainforest_view_2.png)  
![Rainforest View 3](eccentric_outputs/Nagpur_Rainforest/Nagpur_Rainforest_view_3.png)  

---

## 🚀 How to Reproduce

1. Open `notebook.ipynb` in Colab or Jupyter.  
2. Install dependencies:
   ```bash
   pip install diffusers transformers accelerate huggingface_hub safetensors

3. Authenticate with Hugging Face:

```
from huggingface_hub import login
login(token="your_token_here")
```
4. Run all cells → outputs saved in eccentric_outputs/.

🔒 Reproducibility

All random seeds fixed.

Prompts and parameters logged in metadata.json.

Re-running with the same seed regenerates identical images.


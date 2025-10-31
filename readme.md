# LatentCanvas

**Interactive latent diffusion playground** where users can generate and visualize images step-by-step from text prompts, powered by a custom UNet‑CLIP‑VAE pipeline and a Streamlit-based UI.

---

## Features

- Step-wise image generation visualization  
- Support for **DDPM** sampler
- Real-time prompt input, seed and step customization  
- Replay & slider-based inspection  
- Save final output as PNG

---

## Architecture Overview

![alt text](https://github.com/yash-jain221/basic_ddpm_clone/blob/master/architecture.png?raw=true)

**Main Files:**

- `pipeline.py`: End-to-end generation pipeline
- `ddpm.py`, `ddim.py`: Sampling algorithms
- `app.py`: Streamlit user interface
- `model_loader.py`: Loads pretrained SD 1.5 weights

---

## Setup Instructions

```bash
git clone https://github.com/yash-jain221/basic_ddpm_clone.git
cd basic_ddpm_clone

# Setup virtual environment
python3 -m venv venv
source venv/bin/activate

# Install requirements
pip install -r requirements.txt

# Launch the Streamlit app
streamlit run app.py
```

## How to Use

1. Enter a text **prompt** (e.g. `a city floating in space, cinematic`).
2. Choose sampler: **DDPM** or **DDIM**.
3. Adjust **inference steps** and **random seed**.
4. Click **Generate** to start step-by-step image generation.
5. Use **Replay** to rewatch the generation sequence.
6. Use **Save Final Image** to export a PNG.

---

## Behind the Scenes

### Latent Diffusion Models
- Images are encoded into a **4-channel latent tensor** using a **VAE encoder**.
- Diffusion operates on latent space created by VAE.

### Samplers
- **DDPM**: Classic stochastic sampling with Gaussian noise at each step.

### Classifier-Free Guidance (CFG)
- Merges conditional and unconditional contexts to steer the generation.
- Controlled via `cfg_scale` (higher = more prompt adherence).

### Prompt Encoding
- Uses a **CLIP** text encoder to turn text into conditioning vectors.

---

## 📸 Example Output

> _A dog with sunglasses, wearing a comfy hat, ultra sharp, 100mm lens_

![example dog](./assets/example_dog.png)

---

## 🧠 References

- [DDPM Paper (Ho et al. 2020)](https://arxiv.org/abs/2006.11239)  
- [Stable Diffusion GitHub](https://github.com/CompVis/stable-diffusion)
- [Diffusion Tutorial Youtube](https://youtu.be/ZBKpAp_6TGI?si=8NdcMyo9AFY99PPF)



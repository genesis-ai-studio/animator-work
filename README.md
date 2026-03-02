# Genesis AI · Animator v2.0

**Professional animation pipeline powered by ComfyUI**

Built for high-quality AI video generation with pose-driven animation, fast inference, and photorealistic image synthesis — all in one ready-to-run environment.

---

## What's Inside

| Component | Description |
|---|---|
| **Wan 2.2 Animate 14B** | State-of-the-art image-to-video animation model (fp8 optimized) |
| **Z-Image Turbo** | Photorealistic text-to-image generation in 8 steps |
| **LightX2V LoRA** | 4-step fast video generation with cfg distillation |
| **Pusa V1 LoRA** | Enhanced motion quality for Wan 2.1 |
| **VitPose + YOLOv10** | Whole-body pose detection and tracking |
| **SAM2** | Segment Anything Model v2 for object isolation |
| **4x UltraSharp** | High-quality video and image upscaling |

---

## Quick Start

### Step 1 — Launch Instance
Click **Rent** on a compatible GPU instance (see requirements below).

### Step 2 — Wait for Setup
The environment will automatically:
- Clone ComfyUI
- Install all custom nodes
- Download all required models (~50–80 GB)

This takes **10–20 minutes** depending on GPU instance bandwidth.

### Step 3 — Access Your Environment

| Service | Button | Direct Port |
|---|---|---|
| Genesis AI Portal | Click **Open** | 1111 |
| ComfyUI | Via Portal | 8188 |
| Jupyter | Via Portal | 8080 |
| Syncthing | Via Portal | 8384 |

---

## Custom Nodes

- `ComfyUI-WanVideoWrapper` — Wan video pipeline
- `ComfyUI_LayerStyle` — Layer masking and styling
- `ComfyUI-Easy-Use` — Simplified workflow nodes
- `ComfyUI-KJNodes` — Utility nodes by Kijai
- `ComfyUI-VideoHelperSuite` — Video handling tools
- `ComfyUI-segment-anything-2` — SAM2 integration
- `ComfyUI_essentials` — Core utility nodes
- `ComfyUI-WanAnimatePreprocess` — Pose preprocessing for Wan Animate
- `rgthree-comfy` — UI and workflow tools
- `ComfyUI_HuggingFace_Downloader` — Download models directly from HuggingFace inside ComfyUI

---

## Model Layout

```
/workspace/ComfyUI/models/
├── clip/                  # UMT5 XXL fp8 text encoder
├── clip_vision/           # CLIP Vision H (Wan 2.1)
├── vae/                   # Wan 2.1 VAE
├── diffusion_models/      # Z-Image Turbo, Z-Image, Wan2.2-Animate-14B
├── detection/             # YOLOv10m, VitPose wholebody
├── loras/                 # LightX2V, Pusa V1, Fun Reward
└── upscale_models/        # 4x UltraSharp
```

---

## Environment Variables

| Variable | Default | Description |
|---|---|---|
| `WORKSPACE` | `/workspace` | Working directory |
| `COMFYUI_ARGS` | `--disable-auto-launch --port 18188 --enable-cors-header` | ComfyUI startup flags |
| `COMFYUI_API_BASE` | `http://localhost:18188` | Internal API address |
| `PROVISIONING_SCRIPT` | GitHub URL | Auto-setup script on first boot |
| `HF_TOKEN` | *(optional)* | HuggingFace token for gated models |

---

## GPU Requirements

| Use Case | Minimum VRAM | Recommended VRAM |
|---|---|---|
| Z-Image Turbo (T2I) | 8 GB | 12 GB |
| Wan 2.2 Animate 14B | 16 GB | 24 GB |
| Full pipeline | 24 GB | 48 GB+ |

**Filters applied:** `cuda_max_good>=12.4` · `compute_cap>=750` (RTX 20xx and newer)

---

## Port Reference

| Service | External Port | Internal Port |
|---|---|---|
| Genesis AI Portal | 1111 | 11111 |
| ComfyUI | 8188 | 18188 |
| API Wrapper | 8288 | 18288 |
| Jupyter | 8080 | 18080 |
| Syncthing | 8384 | 18384 |

---

## Service Management

```bash
# Check all services
supervisorctl status

# Restart ComfyUI
supervisorctl restart comfyui

# View live logs
supervisorctl tail -f comfyui
```

---

*Genesis AI · Professional Animation Pipeline*

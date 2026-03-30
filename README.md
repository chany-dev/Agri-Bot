# Agri-Intelligence: Fine-Tuning Mistral-7B with QLoRA 🌾

This repository contains the implementation of a specialized AI assistant for agricultural advisory. The model is a fine-tuned version of **Mistral-7B-Instruct-v0.3**, optimized to provide precise insights into crop management, soil health, and sustainable farming practices.

---

##  Model Access

The fine-tuned model weights and tokenizer are hosted on the Hugging Face Hub:

**[chanystrange/mistral-agri-merged_143](https://huggingface.co/chanystrange/mistral-agri-merged_143)**

---

## ⚙️ Technical Overview

To achieve high-performance fine-tuning on a single commodity GPU (NVIDIA T4), I utilized **QLoRA (4-bit Quantization)** and **Parameter-Efficient Fine-Tuning (PEFT)**.

### 1. Model Configuration

| Config | Value |
| :--- | :--- |
| **Base Model** | Mistral-7B-Instruct-v0.3 |
| **Dataset** | `Mahesh2841/Agriculture` (Instruction-tuned format) |
| **Quantization** | 4-bit NormalFloat (NF4) with Double Quantization |
| **Fine-Tuning Method** | LoRA (Low-Rank Adaptation) |

### 2. Hyperparameters

| Parameter | Value |
| :--- | :--- |
| LoRA Rank ($r$) | 8 |
| LoRA Alpha ($\alpha$) | 16 |
| LoRA Dropout | 0.1 |
| Learning Rate | 2e-4 |
| Optimizer | paged_adamw_32bit |
| LR Scheduler | Cosine |
| Training Epochs | 3 |
| Batch Size | 1 (with 4 Gradient Accumulation Steps) |

---

##  Key Capabilities

The model has been trained to understand and explain complex agricultural concepts:

- **Crop Rotation:** Detail the sequential planting of different crops to improve soil fertility and disrupt pest life cycles.
- **Soil Health:** Maintaining nutrient balance and preventing depletion.
- **Pest & Disease Management:** Identifying sustainable strategies to reduce chemical dependency.

---

## 📁 Repository Structure

- `Model.ipynb` — Complete Google Colab notebook covering the end-to-end pipeline from environment setup to model merging and deployment.
- `Inference.ipynb` — Interactive notebook to load the fine-tuned model and run it locally. Open this to start asking agricultural questions directly.
- `requirements.txt` — List of necessary Python libraries (Transformers, PEFT, Accelerate, BitsAndBytes).

---

##  Inference

To run the model, open **`Inference.ipynb`** in Google Colab or any Jupyter environment with a GPU.

The notebook handles everything automatically:
- Loads the fine-tuned model directly from Hugging Face Hub in 4-bit quantized mode, so it fits on a single T4 GPU without any manual setup.
- Starts an interactive Q&A loop where you type your agriculture question and the model responds instantly.
- Type `exit`, `quit`, or `stop` to end the session.

> **Note:** A CUDA-compatible GPU is required. Google Colab's free T4 runtime works perfectly.

---

##  Requirements

Install all dependencies with:
```bash
pip install -r requirements.txt
```

---

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

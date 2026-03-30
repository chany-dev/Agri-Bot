# Agri-Intelligence: Fine-Tuning Mistral-7B with QLoRA 🌾

This repository contains the implementation of a specialized AI assistant for agricultural advisory. [cite_start]The model is a fine-tuned version of **Mistral-7B-Instruct-v0.3**, optimized to provide precise insights into crop management, soil health, and sustainable farming practices[cite: 11, 326, 351].

## 🚀 Model Access
The fine-tuned model weights and tokenizer are hosted on the Hugging Face Hub:
[cite_start]**[chanystrange/mistral-agri-merged_143](https://huggingface.co/chanystrange/mistral-agri-merged_143)** [cite: 226, 276]

## 🛠️ Technical Overview
[cite_start]To achieve high-performance fine-tuning on a single commodity GPU (NVIDIA T4), I utilized **QLoRA (4-bit Quantization)** and **Parameter-Efficient Fine-Tuning (PEFT)**[cite: 13, 22, 95].

### 1. Model Configuration
* [cite_start]**Base Model:** Mistral-7B-Instruct-v0.3[cite: 11].
* [cite_start]**Dataset:** `Mahesh2841/Agriculture` (Instruction-tuned format)[cite: 12, 133].
* [cite_start]**Quantization:** 4-bit NormalFloat (NF4) with Double Quantization enabled to minimize memory footprint[cite: 25, 26, 69, 70].
* [cite_start]**Fine-Tuning Method:** LoRA (Low-Rank Adaptation)[cite: 14, 95].

### 2. Hyperparameters
| Parameter | Value |
| :--- | :--- |
| LoRA Rank ($r$) | [cite_start]8 [cite: 16, 98] |
| LoRA Alpha ($\alpha$) | [cite_start]16 [cite: 18, 99] |
| LoRA Dropout | [cite_start]0.1 [cite: 20, 100] |
| Learning Rate | [cite_start]2e-4 [cite: 37, 114] |
| [cite_start]Optimizer | paged_adamw_32bit [cite: 39, 109] |
| LR Scheduler | [cite_start]Cosine [cite: 39, 125] |
| Training Epochs | [cite_start]3 [cite: 29, 107] |
| Batch Size | [cite_start]1 (with 4 Gradient Accumulation Steps) [cite: 33, 34, 108] |

## 📖 Key Capabilities
The model has been trained to understand and explain complex agricultural concepts:
* [cite_start]**Crop Rotation:** Detail the sequential planting of different crops to improve soil fertility and disrupt pest life cycles[cite: 332, 356].
* [cite_start]**Soil Health:** Maintaining nutrient balance and preventing depletion[cite: 357].
* [cite_start]**Pest & Disease Management:** Identifying sustainable strategies to reduce chemical dependency[cite: 334, 358].

## 💻 Repository Structure
* [cite_start]`agro_model.ipynb`: Complete Google Colab notebook covering the end-to-end pipeline from environment setup to model merging and deployment[cite: 1, 55].
* [cite_start]`requirements.txt`: List of necessary Python libraries (Transformers, PEFT, Accelerate, BitsAndBytes)[cite: 3, 136, 203].

## 🧪 Usage
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/chanystrange/your-repo-name.git](https://github.com/chanystrange/your-repo-name.git)

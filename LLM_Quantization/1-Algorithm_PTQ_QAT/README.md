Papers
------------------------

Contributed by Weiming Hu.

Focuses on pure algorithmic optimizations for LLM quantization, covering core methods such as Post-Training Quantization (PTQ), Quantization-Aware Training (QAT), and mathematical error compensation.

### Foundation & Baseline Algorithms
| Conf. | **Title** | **Key Words** |
| ----- | --------- | ------------- |
| MLSys'24 | AWQ: Activation-aware Weight Quantization for LLM Compression and Acceleration | PTQ, Activation-aware, Weight-only |
| ICLR'23 | GPTQ: Accurate Post-Training Quantization for Generative Pre-trained Transformers | PTQ, Second-order information |
| ICML'23 | SmoothQuant: Accurate and Efficient Post-Training Quantization for Large Language Models | PTQ, Activation Outliers, W8A8 |
| NIPS'23 | SpQR: A Sparse-Quantized Representation for Near-Lossless LLM Weight Compression | Outlier isolation, Mixed-precision |
| ICLR'24 | OmniQuant: Omnidirectionally Calibrated Quantization for Large Language Models | PTQ, Learnable parameters |
| arXiv'23 | ZeroQuant / ZeroQuant-V2 (Microsoft) | W/A quant, system |
| arXiv'23 | RPTQ / other robust PTQ lines (optional) | robustness |

### Fine-Tuning, Dynamic Mapping & QAT
| Conf. | **Title** | **Key Words** |
| ----- | --------- | ------------- |
| NIPS'24 | QLoRA: Efficient Finetuning of Quantized LLMs | Propose NormalFloat4 (NF4), Fine-tuning |
| ICML'22 | Be Like Water: Adaptive Floating Point for Machine Learning | Adaptive floating point |
| ISCA'2020 | DRQ: Dynamic Region-based Quantization for Deep Neural Network Acceleration | Dynamic Quantization |
| DAC'2019 | BiScaled-DNN: Quantizing Long-tailed Datastructures with Two Scale Factors for Deep Neural Networks | Two scale factors |
Papers
------------------------

Contributed by Weiming Hu

### Data Type

| Conf.     | **Title**                                                    | **Key Words**                               |
| --------- | ------------------------------------------------------------ | ------------------------------------------- |
| ASPLOS'24 | 8-bit Transformer Inference and Fine-tuning for Edge Accelerators | Posit8 and FP8                              |
| DAC'24    | Algorithm-Hardware Co-Design of Distribution-Aware Logarithmic-Posit Encodings for Efficient DNN Inference | Posit                                       |
| ICLR'24   | Block and Subword-Scaling Floating-Point (BSFP) : An Efficient Non-Uniform Quantization For Low Precision Inference | Propose BSFP                                |
| NIPS'24   | QLoRA: Efficient Finetuning of Quantized LLMs                | Propose NormalFloat4                        |
| ISCA'23   | With Shared Microexponents, A Little Shifting Goes a Long Way | Microsoft MX-FP (two-level shared exponent) |
| arXiv'23  | Microscaling Data Formats for Deep Learning                  | Explore MXFP4, 6, 8                         |
| MICRO'22  | ANT: Exploiting Adaptive Numerical Data Type for Low-bit Deep Neural Network Quantization | Adaptive data type, propose Flint           |
| HPCA'22   | FAST: DNN Training Under Variable Precision Block Floating Point with Stochastic Rounding | Use BFP in training                         |
| ICML'22   | Be Like Water: Adaptive Floating Point for Machine Learning  | Adaptive floating point                     |
| NIPS'20   | Pushing the Limits of Narrow Precision Inferencing at Cloud Scale with Microsoft Floating Point | First propose MSFP                          |

#### Logarithemic Number System

| Conf.   | **Title**                                                    | **Key Words**      |
| ------- | ------------------------------------------------------------ | ------------------ |
| DAC'24  | Algorithm-Hardware Co-Design of Distribution-Aware Logarithmic-Posit Encodings for Efficient DNN Inference | Logarithmic, posit |
| TETC'24 | A Design Framework for H Efficient Logarithmic Floating-Point Multipliers | LFP Multipliers    |
| VLSI'22 | Half-Precision Logarithmic Arithmetic Unit Based on the Fused Logarithmic and Antilogarithmic Converter | Log converter      |
| TC'22   | LNS-Madam: Low-Precision Training in Logarithmic Number System Using Multiplicative Weight Update | LNS training       |

#### MX Format

| Conf.    | **Title**                                                    | **Key Words**                   |
| -------- | ------------------------------------------------------------ | ------------------------------- |
| arXiv'25 | Recipes for Pre-training LLMs with MXFP8                     | MXFP8, NVIDIA                   |
| arXiv'25 | Characterization and Mitigation of Training Instabilities in Microscaling Formats |                                 |
| arXiv'25 | SageAttention3: Microscaling FP4 Attention for Inference and An Exploration of 8-Bit Training | MXFP, Attention                 |
| ICML'25  | BlockDialect: Block-wise Fine-grained Mixed Format Quantization for Energy-Efficient LLM Inference | MXFP, adaptive codebook/dialect |
| arXiv'25 | FGMP: Fine-Grained Mixed-Precision Weight and Activation Quantization for Hardware-Accelerated LLM Inference | MXFP, NVFP                      |
| arXiv'24 | Nanoscaling Floating-Point (NxFP): NanoMantissa, Adaptive Microexponents, and Code Recycling for Direct-Cast Compression of Large Language Models | MXFP                            |
| arXiv'24 | AMXFP4: Taming Activation Outliers with Asymmetric Microscaling Floating-Point for 4-bit LLM Inference | MXFP, Asymmetric quantization   |
| arXiv'24 | MicroScopiQ: Accelerating Foundational Models through Outlier-Aware Microscaling Quantization | MXINT, MXFP, outlier            |
| arXiv'24 | Post Training Quantization of Large Language Models with Microscaling Formats | MXINT                           |
| arXiv'24 | Error Diffusion: Post Training Quantization with Block-Scaled Number Formats for Neural Networks | error compensation              |
| arXiv'23 | A Dataflow Compiler for Efficient LLM Inference using Custom Microscaling Formats | code template                   |
| ICLR'23  | Block and Subword-Scaling Floating-Point (BSFP) : An Efficient Non-Uniform Quantization For Low Precision Inference | BSFP                            |
| ISCA'23  | With Shared Microexponents, A Little Shifting Goes a Long Way | MX-FP, two-level scaling        |
| arXiv'23 | Microscaling Data Formats for Deep Learning                  | Explore MXFP4, 6, 8             |
| HPCA'21  | FAST: DNN Training Under Variable Precision Block Floating Point with Stochastic Rounding | BFP training                    |
| NIPS'20  | Pushing the Limits of Narrow Precision Inferencing at Cloud Scale with Microsoft Floating Point | MSFP (BFP)                      |

#### Quantization Accelerator / Arch.

| Conf.      | **Title**                                                    | **Key Words**       |
| ---------- | ------------------------------------------------------------ | ------------------- |
| ArXiv'2025 | BBAL: A Bidirectional Block Floating Point-Based Quantisation Accelerator for Large Language Models |                     |
| ArXiv'2025 | FGMP: Fine-Grained Mixed-Precision Weight and Activation Quantization for Hardware-Accelerated LLM Inference |                     |
| ISCA'2025  | Oaken: Fast and Efficient LLM Serving with Online-Offline Hybrid KV Cache Quantization |                     |
| ISCA'2025  | LUT Tensor Core: Lookup Table Enables Efficient Low-Bit LLM Inference Acceleration |                     |
| ISCA'2025  | MicroScopiQ: Accelerating Foundational Models through Outlier-Aware Microscaling Quantization |                     |
| HPCA'2025  | LUT-DLA: Lookup Table as Efficient Extreme Low-Bit Deep Learning Accelerator |                     |
| HPCA'2025  | BitMoD: Bit-serial Mixture-of-Datatype LLM Acceleration      |                     |
| HPCA'2025  | Anda: Unlocking Efficient LLM Inference with a Variable-Length Grouped Activation Data Format |                     |
| HPCA'2025  | Panacea: Novel DNN Accelerator using Accuracy-Preserving Asymmetric Quantization and Energy-Saving Bit-Slice Sparsity |                     |
| HPCA'2025  | M-ANT: Efficient Low-bit Group Quantization for LLMs via Mathematically Adaptive Numerical Type |                     |
| DATE'2025  | SBQ: Exploiting Significant Bits for Efficient and Accurate Post-Training DNN Quantization |                     |
| DATE'2025  | FineQ: Software-Hardware Co-Design for Low-Bit Fine-Grained Mixed-Precision Quantization of LLMs |                     |
| ISCA'2024  | Tender: Accelerating Large Language Models via Tensor Decomposition and Runtime Requantization |                     |
| ISCA'2024  | Cambricon-D: Full-Network Differential Acceleration for Diffusion Models |                     |
| HPCA'2024  | SPARK: Scalable and Precision-Aware Acceleration of Neural Networks via Efficient Encoding |                     |
| HPCA'2024  | FIGNA: Integer Unit-Based Accelerator Design for FP-INT GEMM Preserving Numerical Accuracy |                     |
| DAC'2024   | OPAL: Outlier-Preserved Microscaling Quantization A ccelerator for Generative Large Language Models |                     |
| DAC'2024   | Oltron: Algorithm-Hardware Co-design for Outlier-Aware Quantization of LLMs with Inter-/Intra-Layer Adaptation |                     |
| DAC'24     | Algorithm-Hardware Co-Design of Distribution-Aware Logarithmic-Posit Encodings for Efficient DNN Inference | Posit               |
| ICCD'2024  | AirGun: Adaptive Granularity Quantization for Accelerating Large Language Models |                     |
| MICRO'2024 | Cambricon-LLM: A Chiplet-Based Hybrid Architecture for On-Device Inference of 70B LLM |                     |
| ICLR'2024  | LUT-GEMM: Quantized Matrix Multiplication based on LUTs for Efficient Inference in Large-Scale Generative Language Models |                     |
| ArXiv'2024 | MixPE: Quantization and Hardware Co-design for Efficient LLM Inference |                     |
| ISCA'2023  | OliVe: Accelerating Large Language Models via Hardware-friendly Outlier-Victim Pair Quantization |                     |
| ISCA'2022  | Mokey: Enabling Narrow Fixed-Point Inference for Out-of-the-Box Floating-Point Transformer Models |                     |
| HPCA'22    | FAST: DNN Training Under Variable Precision Block Floating Point with Stochastic Rounding | Use BFP in training |
| MICRO'2022 | ANT: Exploiting Adaptive Numerical Data Type for Low-bit Deep Neural Network Quantization |                     |
| ISCA'2021  | Cambricon-Q: A Hybrid Architecture for Efficient Training    |                     |
| MICRO'2020 | GOBO: Quantizing Attention-Based NLP Models for Low Latency and Energy Efficient Inference |                     |
| ISCA'2020  | DRQ: Dynamic Region-based Quantization for Deep Neural Network Acceleration |                     |
| DAC'2019   | BiScaled-DNN: Quantizing Long-tailed Datastructures with Two Scale Factors for Deep Neural Networks |                     |

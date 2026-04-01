Papers
------------------------

Contributed by Weiming Hu.

Tracks the emerging microscaling formats (e.g., NVFP4, MXFP).

### Algorithm for Microscaling

| Conf.       | **Title**                                                    | **Key Words**                             |
| ----------- | ------------------------------------------------------------ | ----------------------------------------- |
| Arxiv'26.3  | FAAR: Format-Aware Adaptive Rounding for NVFP4               | Lixiang                                   |
| Arxiv'26.3  | Unveiling the Potential of Quantization with MXFP4: Strategies for Quantization ErrorReduction | Meta, OAS+MBS                             |
| Arxiv'26.3  | Diagnosing FP4 inference: a layer-wise and block-wise sensitivity analysis of NVFP4 and MXFP4 | NVFP4 vs MXFP4, Sensitivity analysis      |
| Arxiv'26.3  | Practical FP4 Training for Large-Scale MoE Models on Hopper GPUs | MoE, FP4 Training                         |
| Arxiv'26.3  | BATQuant: Outlier-resilient MXFP4 Quantization via Learnable Block-wise Optimization | Learnable optimization, block-wise affine |
| Arxiv'26.3  | WUSH: Near-Optimal Adaptive Transforms for LLM Quantization  | Adaptive Transform                        |
| Arxiv'26.2  | LATMiX: Learnable Affine Transformations for Microscaling Quantization of LLMs | Learnable Affine Transform                |
| Arxiv'26.2  | Dissecting Outlier Dynamics in LLM NVFP4 Pretraining         |                                           |
| ICLR'2026   | ParoQuant: Pairwise Rotation Quantization for Efficient Reasoning LLM Inference |                                           |
| Arxiv'26.1  | Quartet II: Accurate LLM Pre-Training in NVFP4 by Improved Unbiased Gradient Estimation | IST                                       |
| Arxiv'26.1  | ARCQuant: Boosting NVFP4 Quantization with Augmented Residual Channels for LLMs | Residual Channels                         |
| Arxiv’26.1  | Is Finer Better? The Limits of Microscaling Formats in Large Language Models | Granularity                               |
| Arxiv’26.1  | Benchmarking Post-Training Quantization of Large Language Models under Microscaling Floating Point Formats | Accuracy Analysis                         |
| Arxiv'25    | Bridging the Gap Between Promise and Performance for Microscaling FP4 Quantization | MR-GPTQ                                   |
| ArXiv'25    | INT v.s. FP: A Comprehensive Study of Fine-Grained Low-bit Quantization Formats | Format Comparison, Analysis               |
| ArXiv'25.11 | MOSS: Efficient and Accurate FP8 LLM Training with Microscaling and Automatic Scaling | Automatic Scaling                         |
| ARITH'2025  | An Empirical Study of Microscaling Formats for Low-Precision LLM Training | Accuracy Analysis                         |
| arXiv'25.12 | Four Over Six: More Accurate NVFP4 Quantization with Adaptive Block Scaling | Adaptive scale                            |
| arXiv'25    | Recipes for Pre-training LLMs with MXFP8                     | MXFP8, NVIDIA                             |
| arXiv'25    | Characterization and Mitigation of Training Instabilities in Microscaling Formats | Training Instability                      |
| arXiv'25    | SageAttention3: Microscaling FP4 Attention for Inference and An Exploration of 8-Bit Training | MXFP, Attention                           |
| arXiv'25    | FGMP: Fine-Grained Mixed-Precision Weight and Activation Quantization for Hardware-Accelerated LLM Inference | MXFP, NVFP                                |
| arXiv'24    | Nanoscaling Floating-Point (NxFP): NanoMantissa, Adaptive Microexponents, and Code Recycling for Direct-Cast Compression of Large Language Models | MXFP                                      |
| ACL'25      | AMXFP4: Taming Activation Outliers with Asymmetric Microscaling Floating-Point for 4-bit LLM Inference | MXFP, Asymmetric quantization             |
| ISCA'2025   | MicroScopiQ: Accelerating Foundational Models through Outlier-Aware Microscaling Quantization | MXINT, MXFP, outlier                      |
| arXiv'24    | Post Training Quantization of Large Language Models with Microscaling Formats | MXINT                                     |
| arXiv'24    | Error Diffusion: Post Training Quantization with Block-Scaled Number Formats for Neural Networks | error compensation                        |
| arXiv'23    | A Dataflow Compiler for Efficient LLM Inference using Custom Microscaling Formats | code template                             |

### Architecture Co-design

| Conf.       | **Title**                                                    | **Key Words** |
| ----------- | ------------------------------------------------------------ | ------------- |
| arXiv'26.3 | Adaptive Block-Scaled Data Types | 4over6 author |
| arXiv'26.3 | SemanticDialect: Semantic-Aware Mixed-Format Quantization for Video Diffusion Transformers | BlockDialect DiT |
| arXiv'26.2 | HiFloat4 Format for Language Model Inference | Huawei, HiF4 |
| arXiv'26.2 | TriGen: NPU Architecture for End-to-End Acceleration of Large Language Models based on SW-HW Co-Design | NPU Arch, End-to-End Co-design |
| ArXiv'26.1 | RaZeR: Pushing the Limits of NVFP4 Quantization with Redundant Zero Remapping | Zero Remapping |
| ASP-DAC'26 | Precision-Scalable Microscaling Datapaths with Optimized Reduction Tree for Efficient NPU Integration | Reduction Tree |
| ASPLOS'2026 | M2XFP: A Metadata-Augmented Microscaling Data Format for Efficient Low-bit Quantization | Metadata, DSE |
| MICRO'2025  | MX+: Pushing the Limits of Microscaling Formats for Efficient Large Language Model Serving | MXFP4         |
| ISLPED'2025 | Efficient Precision-Scalable Hardware for Microscaling (MX) Processing in Robotics Learning | Precision-scalable units |
| ISCA'2025   | MicroScopiQ: Accelerating Foundational Models through Outlier-Aware Microscaling Quantization | MXINT, MXFP, outlier            |
| ICML'25 | BlockDialect: Block-wise Fine-grained Mixed Format Quantization for Energy-Efficient LLM Inference | MXFP, adaptive codebook/dialect |
| HPCA'2025 | Anda: Unlocking Efficient LLM Inference with a Variable-Length Grouped Activation Data Format | Variable-Length Data Format |
| ICLR'23 | Block and Subword-Scaling Floating-Point (BSFP) : An Efficient Non-Uniform Quantization For Low Precision Inference | BSFP |
| ISCA'23 | With Shared Microexponents, A Little Shifting Goes a Long Way | MX-FP, two-level scaling |
| arXiv'23 | Microscaling Data Formats for Deep Learning | Explore MXFP4, 6, 8 |
| HPCA'21 | FAST: DNN Training Under Variable Precision Block Floating Point with Stochastic Rounding | BFP training |
| NIPS'20 | Pushing the Limits of Narrow Precision Inferencing at Cloud Scale with Microsoft Floating Point | MSFP (BFP) |

Papers
------------------------

Contributed by ziyu huang

### Triton-distributed: Programming Overlapping Kernels on Distributed AI Systems with the Triton Compiler

* **Source:** arxiv
* **Info:**
    * [Triton-distributed: 用Python写出高性能计算通信重叠kernel - 郑思泽的文章 - 知乎](https://zhuanlan.zhihu.com/p/1900910901017679250) ---centauri has solved PP, DP; current hotspot is TP, EP, SP
    * [训练性能显著提升，字节跳动郑思泽详解 Triton-distributed 框架 - HyperAI超神经的文章 - 知乎](https://zhuanlan.zhihu.com/p/1930589381032417142)
    * [Triton-distributed MegaKernel初试 - 郑思泽的文章 - 知乎](https://zhuanlan.zhihu.com/p/1938977221525110949)

### FlashOverlap: A Lightweight Design for Efficiently Overlapping Communication and Computation
* **Source:** arxiv
* **Info:**
    * [无问芯穹计算通信重叠新范式——FlashOverlap技术解析 - 李秀红的文章 - 知乎](https://zhuanlan.zhihu.com/p/1897633068380054002)
    * tile-centric fine grain comm might decrease efficiency, we used several waves as a granularity.

 ### FLUX: Fast Software-based Communication Overlap On GPUs Through Kernel Fusion
* **Source:** arxiv
* **Info:**
   * triton-distributed said: "FLUX fuses the scatter operation into GEMM kernel and performs a global synchronization before local reduction."

### Optimizing Distributed ML Communication with Fused Computation-Collective Operations
* **Source:** SC24
* **Info:**
   * Fusing comm as epilogue following gemm, like FLUX
   * intra GPU: gather multiple tiles' result as "slice" like FlashOverlap
   * inter GPU: AMD's ROC_SHMEM

### TokenWeave: Efficient Compute-Communication Overlap for Distributed LLM Inference
* **Source:** arxiv
* **Info:**
   * [TokenWeave(arxiv25)：粗粒度通信计算重叠 - Arsmart的文章 - 知乎](https://zhuanlan.zhihu.com/p/1953844427287142621)
   * find the fact that FLUX, tilelink performs bad when m is small
   * Previous work focus on MLP. Maybe I can try try attention? E2E? Training?
  
|                       | tile swizzle              | granularity| pingpong within CTA | sync                 |  senario(small m?) |
|-----------------------|---------------------------|-------|----------------------|--------------------------|--------------------------------|
| triton-distributed    | yes (for overlap)         | tile        | no | tile2tile                            | training/decoding, small m using flash decoding|
| flashoverlap          | yes (for continuous comm) | waves       | no |waves2waves(separate signal kernel)   | especially pcie, avoid small m |
| FLUX                  | yes (for avoiding contention) | tile    | no | tile2tile                            | small m performs bad |
| SC                    | no                        | WG          |no  | slice2slice(fused single kernel)     | DLRM, MoE, gemv  |
| TokenWeave            | no                        | waves       |no  | cuda stream sync                     | small m performs well because "less wave quantization; coarse grain comm" |
| Comments                                 | Matching the computation order and communication order(new opti chances introduced by NVSHMEM) | Cutting too small leads to large startup overhead; cutting too large leads to more bubble overlap | Fine-grained kernel fusion, which may improve resource utilization but could also decrease gemm performance | Is the overhead large? Is there global synchronization? Is fine-grained synchronization done well? | mostly focus on MLP.... when m is small: tile-wise comm increases comm latency, small block number reduces overlap|

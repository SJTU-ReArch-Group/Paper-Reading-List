Papers
------------------------

Contributed by ziyu huang

## handwritten work
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


### FlashCommunication V2: Bit Splitting and Spike Reserving for Any Bit Communication
* **Source:** arxiv
* **Info:**
   * Relevant Scenarios: Distributed Training: All-Reduce for Tensor Parallelism (TP); All-to-All for Mixture of Experts (MoE).
      Inference/Deployment: KV cache transfer in systems with pre-fill/decode separation.
   * Hierarchical Communication due to NUMA Architecture:
      A common communication pipeline is: Intra-NUMA Reduce-Scatter (RS) -> Inter-NUMA All-Reduce (AR) -> Intra-NUMA All-Gather (AG). (A key question is how to optimize this pipeline.)
   * hierarchy comm introduced by NUMA: intra numa RS->inter numa AR->intra numa AG(how can I optimize this pipeline?)
   * PCIE cluster is also common, like L20, L40

### How to Copy Memory? Coordinated Asynchronous Copy as a First-Class OS Service
* **Source:** SOSP25
* **Info:**
   * This is an OS level work. We should view "copy" as a OS level service, but not a user function.
   * Can use SIMD and DMA at the same time. (previous function view can not)
   * Operate copy in a global view(absorb redundant copy/boost the priority of some copies)
   * Maybe useful for dynamic situation like... MOE?
     
## compiler work
### Mercury: Unlocking Multi-GPU Operator Optimization for LLMs via Remote Memory Scheduling
* **Source:** SOSP25
* **Info:**
   * Considered memory... Maybe I can introduce comp and comm?
   * basically focus on attn
   * search space: ring attn, tree attn, loong train
 
### TileLink: Generating Efficient Compute-Communication Overlapping Kernels using Tile-Centric Primitives
* **Source:** MLSYS25
* **Info:**
   * search space: tile size; comp/comm order; resource binding
   * primitive: data sending, signal sending
   * basically focus on TP(gemm+comm)
   * search space: FLUX(kind of weak?)
 
## MOE work

|                       | tile swizzle              | granularity| WG spec | SM spec | sync                 |  senario(small m?) |
|-----------------------|---------------------------|------------|---------|---------|--------------------------|--------------------------------|
| triton-distributed    | yes (for overlap)         | tile        | no     |   yes   | tile2tile                            | training/decoding, small m using flash decoding|
| flashoverlap          | yes (for continuous comm) | waves       | no     |   yes   |  waves2waves(separate signal kernel)   | especially pcie, avoid small m |
| FLUX                  | yes (for avoiding contention) | tile    | no     |   no    | tile2tile                            | small m performs bad |
| SC                    | no                        | WG          | no     |   no    | slice2slice(fused single kernel)     | DLRM, MoE, gemv  |
| TokenWeave            | no                        | waves       | no     |   yes   | cuda stream sync                     | small m performs well because "less wave quantization; coarse grain comm" |
| Comments                                 | Matching the computation order and communication order(new opti chances introduced by NVSHMEM) | Cutting too small leads to large startup overhead; cutting too large leads to more bubble overlap | Fine-grained kernel fusion, which may improve resource utilization but could also decrease gemm performance | Is the overhead large? Is there global synchronization? Is fine-grained synchronization done well? | mostly focus on MLP.... when m is small: tile-wise comm increases comm latency, small block number reduces overlap |

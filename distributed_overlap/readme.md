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
* **Source:** arxiv25
* **Info:**
   * Relevant Scenarios: Distributed Training: All-Reduce for Tensor Parallelism (TP); All-to-All for Mixture of Experts (MoE).
      Inference/Deployment: KV cache transfer in systems with pre-fill/decode separation.
   * Hierarchical Communication due to NUMA Architecture:
      A common communication pipeline is: Intra-NUMA Reduce-Scatter (RS) -> Inter-NUMA All-Reduce (AR) -> Intra-NUMA All-Gather (AG). (A key question is how to optimize this pipeline.)
   * hierarchy comm introduced by NUMA: intra numa RS->inter numa AR->intra numa AG(how can I optimize this pipeline?)
   * PCIE cluster is also common, like L20, L40
   * [FlashCommunication V2(arxiv25) - Arsmart的文章 - 知乎](https://zhuanlan.zhihu.com/p/1954583327647446471)    


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
   * basically focus on attn/mlp
   * search space: ring attn, tree attn, loong train, flux
 
### TileLink: Generating Efficient Compute-Communication Overlapping Kernels using Tile-Centric Primitives
* **Source:** MLSYS25
* **Info:**
   * search space: tile size; comp/comm order; resource binding
   * primitive: data sending, signal sending
   * basically focus on TP(gemm+comm)
   * search space: FLUX(kind of weak?)


|                       | tile swizzle              | granularity| WG spec | SM spec | sync                 |  senario(small m?) |
|-----------------------|---------------------------|------------|---------|---------|--------------------------|--------------------------------|
| triton-distributed    | yes (for overlap)         | tile        | no     |   yes   | tile2tile                            | training/decoding, small m using flash decoding|
| flashoverlap          | yes (for continuous comm) | waves       | no     |   yes   |  waves2waves(separate signal kernel)   | especially pcie, avoid small m |
| FLUX                  | yes (for avoiding contention) | tile    | no     |   no    | tile2tile                            | small m performs bad |
| SC                    | no                        | WG          | no     |   no    | slice2slice(fused single kernel)     | DLRM, MoE, gemv  |
| TokenWeave            | no                        | waves       | no     |   yes   | cuda stream sync                     | small m performs well because "less wave quantization; coarse grain comm" |
| Comments                                 | Matching the computation order and communication order(new opti chances introduced by NVSHMEM) | Cutting too small leads to large startup overhead; cutting too large leads to more bubble overlap | Fine-grained kernel fusion, which may improve resource utilization but could also decrease gemm performance | Is the overhead large? Is there global synchronization? Is fine-grained synchronization done well? | mostly focus on MLP.... when m is small: tile-wise comm increases comm latency, small block number reduces overlap |

 
## MOE work
### FlashDMoE: Fast Distributed MoE in a Single Kernel
* **Source:** arxiv25
* **Info:**
   * [FlashDMoE：分布式 MoE 执行范式的变革 - mlsys小登的文章 - 知乎](https://zhuanlan.zhihu.com/p/1930765288657383428)
   * fuse all op in MOE
   * propose one OS block to schedule comp/comm overlap. 
   * Baseline: Comet; FasterMOE; Megatron-TE; Megtron-cutlass (https://github.com/nvidia/megatron-lm/issues/1721)
   
### Lancet: Accelerating mixture-of-experts training via whole graph computation-communication overlapping
* **Source:** MLSYS24
* **Info:**
   * [【论文精读】Lancet: Accelerating Mixture-of-Experts Training via Whole Graph Computation-Communication - 娶个敏感词的文章 - 知乎](https://zhuanlan.zhihu.com/p/10557576327)
   * backward weight update can overlap a2a (no dependency)
   * forward attn can overlap moe-a2a (comm overlap with before/after attn)
   * Baselines: Deepspeed; tutel
<img width="847" height="588" alt="image" src="https://github.com/user-attachments/assets/3010c92a-7f4c-4862-8c37-8bb9347ad17d" />
<img width="858" height="636" alt="image" src="https://github.com/user-attachments/assets/e95ac996-41eb-4959-b044-2442b7738068" />

### Tutel: Adaptive mixture-of-experts at scale
* **Source:** mlsys23
* **Info:**
   * [微软亚洲研究院发布高性能 MoE 库 Tutel 你如何看待？ - 方佳瑞的回答 - 知乎](https://www.zhihu.com/question/502116776/answer/3191238455)
   * [论文阅读笔记：tutel(mlsys23) - Arsmart的文章 - 知乎](https://zhuanlan.zhihu.com/p/1956822528807899482)
   * different token number has an optimal parallel strategy(DP/PP/EP), so we dynamically change strategy and overlap comm with comp(strange idea!)
   * do not theoretically analyze which token number match a strategy, just use experiment to test!
   * Baseline: Deepspeed

### Comet: Fine-grained Computation-communication Overlapping for Mixture-of-Experts
* **Source:** mlsys25
* **Info:**
   * [论文阅读笔记：COMET(MLSYS25) - Arsmart的文章 - 知乎](https://zhuanlan.zhihu.com/p/1893037252499711420)
   * async all2all
   * Async MOE layer0 and layer1: for layer0, first compute local data, and comm remote data asyncly; for layer1, if first Tn column finishes, execute TopK and combine at once. 
   * docs/moe_usage.md
   * Baseline: Megatron-TE, Megatron-cutlass, fastermoe, tutel


### Toward Cost-Efficient Serving of Mixture-of-Experts with Asynchrony
* **Source:** arxiv25
* **Info:**
   * [论文阅读笔记：AEP(arxiv25) - Arsmart的文章 - 知乎](https://zhuanlan.zhihu.com/p/1956451131858325815)
   * a2a is a sync op, but actually after one token finishes topk, it can continue, therefore a2a become async.
   * This work extend comet to multiple layers(attn/moe)
   * Baseline: SGLang

### DeepSpeed-MoE: Advancing Mixture-of-Experts Inference and Training to Power Next-Generation AI Scale
### A Hybrid Tensor-Expert-Data Parallelism Approach to Optimize Mixture-of-Experts Training(deepspeed-ted)
* **Source:** PMLR22 & ICS23
* **Info:**
   * attention(TP)+MOE(EP), exist some redundant comm....(TOO old...)

### Harnessing Inter-GPU Shared Memory for Seamless MoE Communication-Computation Fusion
* **Source:** PPoPP25
* **Info:**
   * [论文阅读笔记：ccfuser(PPoPP25) - Arsmart的文章 - 知乎](https://zhuanlan.zhihu.com/p/1956101225532600662)
   * tile wise overlap local comp & remote comm
   * Baseline: Fastmoe, fastermoe

### ScheMoE: An Extensible Mixture-of-Experts Distributed Training System with Tasks Scheduling
* **Source:** eurosys24
* **Info:**
   * [ScheMoE: An Extensible Mixture-of-Experts Distributed Training System with Tasks Scheduling——论文泛读 - 妙BOOK言的文章 - 知乎](https://zhuanlan.zhihu.com/p/707614012)
   * Three designs: a. portable EP modules. b. optimal comp/comm schedule design.(good direction!) c. inter/intra node A2A(triton-distributed also has this)

### Accelerating Distributed MoE Training and Inference with Lina
* **Source:** atc23
* **Info:**
   * How to schedule AR and A2A? Overlap will prolong both. lina proposes split tensors(fixed as 30MB, not smart) to separate AR and A2A, and overlap A2A with expert-comp.

### PipeMoE: Accelerating Mixture-of-Experts through Adaptive Pipelining
* **Source:** INFOCOM 2023
* **Info:**
   * To overlap comm/comp, how deep should we split the batch? This paper proposes a cost model..(Seems not very valuable?)
 
### Optimizing Mixture-of-Experts Inference Time Combining Model Deployment and Communication Scheduling
* **Source:** arxiv25
* **Info:**
   * consider expert assignment & comm schedule together
   * but the hardware is strange... heterogeneous/homogeneous cluster... in inference?
   * locate two models in one GPU to overlap comm/comp

### FlowMoE: A Scalable Pipeline Scheduling Framework for Distributed Mixture-of-Experts Training
* **Source:** nips25
* **Info:**
   * overlap attn/moe. Full transformer block overlap!

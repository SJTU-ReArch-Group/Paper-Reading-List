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
  
| | tile swizzle                             | granularity         | pingpong within CTA | sync                           |
|---------|---------------------------------|---------------------|----------------------|--------------------------------|
| triton-distributed                       | yes (for overlap)   | tile                 | no                             |
| flashoverlap                              | yes (for continuous comm) | waves           | no                             |
| FLUX                                      | yes (for avoiding contention) | tile          | no                             |
| SC                                        | no                  | WG                   | no                             |
| Comments                                 | Matching the computation order and communication order | Cutting too small leads to large startup overhead; cutting too large leads to more bubble overlap | Fine-grained kernel fusion, which may improve resource utilization but could also decrease gemm performance | Is the overhead large? Is there global synchronization? Is fine-grained synchronization done well? |

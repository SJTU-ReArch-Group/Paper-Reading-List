### PPML Introduction
Privacy-preserving machine learning (PPML) was first proposed around 2014. As the promising performance of deep neural networks (DNNs) has led to their deployment in many real-world tasks, the privacy of both clients and servers has become a potential concern in sensitive applications. In this context, we focus on addressing privacy concerns through cryptographic primitives. The following section lists selected papers that represent significant progress in PPML, along with some useful PPML frameworks. Finally, a more comprehensive list of recommended papers can be found at this [link](https://github.com/Ye-D/PPML-Resource?tab=readme-ov-file).

### PPML Main 
This section focuses on the pure optimization of privacy-preserving machine learning. The commonly used cryptographic primitives includes homomorphic encryption (HE) and multi-party computation (MPC). The cryptographic primitives can handle all operations within deep neural networks, covering everything from multi-layer perceptrons (MLP) to convolutional networks and transformer models. Additionally, efficiency has experienced a thousandfold speedup from earlier solutions, moving towards practical implementations.

| **Title**                                                                                                              | **Key Words**               |
|------------------------------------------------------------------------------------------------------------------------|-----------------------------|
| （CCS 2017）Oblivious Neural Network Predictions via MiniONN Transformations                             | fully homomorphic encryption        |
| （S&P 2017）SecureML: A System for Scalable Privacy-Preserving Machine Learning                             |  |
| （CCS 2018）ABY3 A Mixed Protocol Framework for Machine Learning                            |  |
| （USNIX security 2018）GAZELLE: A Low Latency Framework for Secure Neural Network Inference                                                     |  hybrid protocol (HE+MPC)                           |
| （USENIX security 2020）Delphi: A Cryptographic Inference Service for Neural Networks                  |                 |
| （USENIX security 2022）Cheetah: Lean and Fast Secure Two-Party Deep Neural Network Inferencethe          |                             |
| （S&P 2021）SIRNN: A Math Library for Secure RNN Inference                                                                      |                             |
| （NIPS 2022）Iron: Private Inference on Transformers                       |   Specifically for the Transformers                          |
| （ICLR 2023）MPCFORMER: FAST, PERFORMANT AND PRIVATE Transformer inference with MPC                       |                             |
| （S&P 2023）BOLT: Privacy-Preserving, Accurate and Efficient Inference for Transformers |                             |
| （S&P 2023）HELiKs: HE Linear Algebra Kernels for Secure Inference                                                 |                             |
| （NDSS 2024）BumbleBee: Secure Two-party Inference Framework for Large Transformers                                                           |                             |
| （NDSS 2024）Secure Transformer Inference Made Non-interactive                                                           |                             |



### PPML Framework
This section lists some frameworks designed for PPML, aiming to faciliate the deployment of the secure inference.

| **Title**                                                                                                              | **Key Words**               |
|------------------------------------------------------------------------------------------------------------------------|-----------------------------|
| （NIPS 2021）CRYPTEN Secure Multi-Party Computation                             | Totally built on pytorch |
| SPDZ-2: Multiparty computation with SPDZ, MASCOT, and Overdrive offline phases                             |        |
| （CCS 2020）CrypTFlow2 Practical 2-Party Secure Inference                             | Also known as EzPC        |
| （ATC 2023）SecretFlow-SPU A Performant and User-Friendly Framework for Privacy-Preserving Machine Learning                     |      python frontend & C++ backend                   |



# Efficient DNN Serving
Contributed by *jiale xu*

## Scheduling Strategy
| Conf.    | Title                                                                                                | Keyword                                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| OSDI'22  | Orca: A Distributed Serving System for Transformer-Based Generative Models                           | continuous batching                                                                                              |
| SOSP'23  | Efficient Memory Management for Large Language Model Serving with PagedAttention                     | paged KV Cache, prefill-oriented scheduling                                                                      |
| OSDI'24  | Taming Throughput-Latency Tradeoff in LLM Inference with Sarathi-Serve                               | chunked-prefill, decode-oriented scheduling                                                                      |
| OSDI'24  | DistServe: Disaggregating Prefill and Decoding for Goodput-optimized Large Language Model Serving    | prefill-decode disaggregation,     KV cache transmission                                                         |
| ISCA'24  | Splitwise: Efficient generative LLM inference using phase splitting                                  | prefill-decode disaggregation, cost-efficient analysis, performance characterization                             |
| SOSP'24  | LoongServe: Efficiently Serving Long-Context Large Language Models with Elastic Sequence Parallelism | elastic distributed LLM serving,  prefill-decode disaggregation, LLM serving performance modeling and scheduling |
| OSDI'24  | Fairness in Serving Large Language Models                                                            | fair queueing of client requests, performance modeling                                                           |
| OSDI'24  | Llumnix: Dynamic Scheduling for Large Language Model Serving                                         | instance migration,  layer-wise kv transmission, instance-level scheduling                                       |
| ARXIV'24 | NanoFlow: Towards Optimal Large Language Model Serving Throughput                                    | intra-device parallelism, CPU-GPU overlap, throughput-oriented performance modeling and scheduling               |
| ARXIV'24 | DynamoLLM: Designing LLM Inference Clusters for Performance and Energy Efficiency                    | efficiency in LLM serving, reconfigurable distributed inference                                                  |                                                                       
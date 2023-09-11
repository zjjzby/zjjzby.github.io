---
layout: page
title:  (GraphAGILE) A Domain specific accelerator for GNNs
description: A domain specific accelerator for graph neural network inference.
img: assets/img/graphagile/graphagileoverview.jpg
importance: 1
category: work
---

I propose GraphAGILE, a domain-specific FPGA-based overlay accelerator for graph neural network (GNN) inference. GraphAGILE consists of (1) a novel unified architecture design with an instruction set, and (2) a compiler built upon the instruction set that can quickly generate optimized code. 
Due to the proposed instruction set architecture (ISA) and the compiler,  GraphAGILE does not require any FPGA reconfiguration when performing inference on various GNN models and input graphs.
For the architecture design, we propose a novel hardware module named Adaptive Computation Kernel (ACK), that can execute various computation kernels of GNNs,
including general matrix multiplication (GEMM), sparse-dense matrix multiplication (SpDMM), and sampled dense-dense matrix multiplication (SDDMM).
The compiler takes the specifications of a GNN model and the graph meta data (e.g., the number of vertices and edges) as input,  and generates a sequence of instructions for inference execution.   
We develop the following compiler optimizations to reduce inference latency: (1) computation order optimization that automatically reorders the computation graph to reduce the total computation complexity, (2) layer fusion that merges adjacent layers to reduce data communication volume, (3) data partitioning with a partition-centric execution scheme that partitions the input graph to fit the available on-chip memory of FPGA, (4) kernel mapping that automatically selects execution mode for ACK, and performs task scheduling to overlap computation with data communication and achieves dynamic load balance. 
We implement GraphAGILE on a state-of-the-art FPGA platform, Xilinx Alveo U250. GraphAGILE can execute widely used GNN models, including GCN, GAT, GIN, GraphSAGE, SGC and other GNN models supported by GraphGym. Experimental results show that GraphAGILE achieves up to 47.1x 3.9x reduction in end-to-end latency, including the latency of compilation and hardware execution, compared with the state-of-the-art implementations on CPU (GPU), and achieves up to  2.9x reduction in hardware execution latency compared with the state-of-the-art FPGA accelerators.




<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/graphagile/graphagileoverview.jpg" title="Overview of GraphAGILE" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Overview of GraphAGILE.
</div>


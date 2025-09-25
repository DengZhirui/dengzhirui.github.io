目前强化学习的主流框架有TRL和Verl，TRL的优势在于魔改方便，而Verl包装更好，并且强化学习模型实现的更为完善。
在具体介绍Verl的用法之前，首先了解下面几个概念
### DeepSpeed
[DeepSpeed](https://github.com/deepspeedai/DeepSpeed)是微软开发的深度学习框架，旨在提升大模型训练时对资源的利用效率和训练效率，包括模型并行化、梯度累积、动态精度缩放、本地模式混合精度等技术。
#### 1. ZeRO (Zero Redundancy Optimizer)
包含数据并行、张量切片模型并行和流水线并行。ZeRO可以在当前一代GPU集群上以当前最佳系统吞吐量的三到五倍的速度训练具有1000亿个参数的深度学习模型。ZeRO可以克服**数据并行**和**模型并行**的局限性，同时实现两者的优点。通过在数据并行进程之间划分模型状态参数、梯度和优化器状态来消除数据并行进程中的内存冗余，而不是复制它们。在训练期间使用动态通信调度来在分布式设备之间共享必要的状态，以保持数据并行的计算粒度和通信量。主要有三个优化阶段：
- Optimizer State Partitioning（Pos）：减少4倍内存，通信量与数据并行性相同
- 添加梯度分区（Pos+g）：减少8倍内存，通信量与数据并行性相同
- 添加参数分区（Pos+g+p）：内存减少与数据并行度Nd呈线性关系。例如，在64个GPU之间进行拆分将产生64倍的内存缩减。通信量有50%的适度增长。
<img src="https://raw.githubusercontent.com/DengZhirui/dengzhirui.github.io/main/images/deepspeed1.jpg" width="500"/>

#### 2. ZeRO-2
增加梯度切片，优化内存和碎片内存，在ZeRO-1（只对optimizer切片）的基础上可训练模型的大小扩大了一倍。
#### 3. ZeRO-3 offload
增加模型参数切片，将优化器状态和梯度卸到CPU内存中，单张V100可运行13B模型。
#### 4. Sparse Attention
用6倍速度执行10倍长的序列.
#### 5. 1-bit Adam
梯度压缩为1-bit。

## 混合精度
BF16，FP16
## FSDP and FSDP2

## Ray

## Megatron-LM

## vLLM

## SGLang

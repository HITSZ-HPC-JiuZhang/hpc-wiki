# 哈尔滨工业大学（深圳）超算队

哈尔滨工业大学（深圳）（HITSZ）的超算人才培养与竞赛活动由实验与创新教育中心（ECEI）组织。自 2020 年起，中心持续支持学生参加高性能计算竞赛，并维护专用于教学、训练和科研实践的计算基础设施。

目前，学校面向相关课程与团队训练提供两类主要集群：通用计算用 CPU 集群，以及面向加速计算的 CPU–GPU 异构集群。

## 计算基础设施

### CPU 集群

CPU 集群于 2017 年部署，由 4 套华为 E9000 刀片服务器机箱组成，每套机箱配置 7 个 CH220 V3 刀片节点，并通过 FC-SAN 连接 OceanStor 5600 V3 存储服务器。

| 项目 | 单节点配置 |
| --- | --- |
| 型号 | Huawei CH220 V3 |
| CPU | 2 × Intel Xeon E5-2680 V3 |
| 内存 | 256 GB |
| 本地存储 | 2 × 300 GB、10k RPM、2.5 英寸 SAS，并接入 SAN |
| 网络 | 10 Gbps Ethernet + 8 Gbps FC |

存储系统由一台 3U 存储节点和多台 2U 硬盘扩展柜组成，总容量约 165 TB。集群通过 Huawei FusionCompute 平台管理，主要服务于 ECEI 课程教学，同时为超算队的日常训练和实验提供环境。

### GPU 集群

异构 GPU 集群于 2022 年 1 月投入运行，采用 SLURM 进行作业调度，服务于机器学习课程和计算密集型科研任务。超算队可在寒假等教学低峰期使用该集群进行集中训练。

| 节点类型 | 硬件配置 | 数量 |
| --- | --- | ---: |
| A100 计算节点 | 2 × Intel Xeon Silver 4316；8 × NVIDIA A100 PCIe | 8 |
| A100 NVLink 计算节点 | 2 × AMD EPYC 7513；8 × NVIDIA A100 SXM4 | 2 |
| A30 计算节点 | 2 × Intel Xeon Platinum 8358；8 × NVIDIA A30 PCIe | 2 |
| CPU 计算节点 | 2 × Intel Xeon Platinum 8358 | 4 |

此外，学校还为 ASC 团队保留了专用训练节点：

| 节点类型 | 硬件配置 | 数量 |
| --- | --- | ---: |
| ASC 训练节点 | 2 × Intel Xeon Platinum 8358；4 × NVIDIA A100 PCIe | 2 |

## 课程、训练与技术社群

### 课程体系

学校以“高性能计算实践”课程为核心构建 HPC 教学路径。该课程于 2021 年开设，以矩阵乘法优化为贯穿案例，训练内容依次覆盖：

1. CPU 单核优化，包括 SIMD 向量化与 Cache Blocking；
2. 使用 OpenMP 开展多核并行；
3. 使用 MPI 扩展到多节点；
4. 使用 CUDA 完成 GPU 异构加速。

2023 年增设的“计算机体系结构”课程进一步覆盖 AI 模型部署与先进体系结构等内容。

### 国产计算平台训练

团队也在搭载 Huawei Kunpeng 920 CPU 和 8 × Ascend 910B NPU 的集群上开展专项训练。在 HPCG 源码优化实践中，团队围绕访存模式和并行策略进行调优，将浮点性能从约 40 GFLOPS 提升至 1400 GFLOPS 以上。

在 AI 工作负载方面，团队使用 XLLM 框架在 NPU 平台部署并推理 LLaMA 等大语言模型，以训练跨平台部署与优化能力。

### 技术社群

校内开源技术协会为超算人才培养提供了广泛的技术社区支持。协会维护校园开源镜像站和 Gitea 代码托管平台，并定期开展 Linux 系统管理与性能优化相关分享。

## 科研与应用方向

学校依托现有计算平台开展多类高性能计算相关研究和工程实践：

- **人工智能与计算机视觉**：大规模深度学习模型训练、具身智能、自动驾驶语义分割与目标检测；
- **科学计算**：使用并行计算加速物理与材料科学仿真，并优化有限元分析和分子动力学算法；
- **系统优化**：面向异构计算系统研究性能分析、算子融合和张量加速技术，提高硬件利用效率与能效。

## 竞赛与成果

| 年份 | 赛事 | 成绩 |
| ---: | --- | --- |
| 2022–2023 | ASC Student Supercomputer Challenge | 一等奖、团体竞赛奖 |
| 2024 | ASC Student Supercomputer Challenge | 一支队伍获二等奖；另一支队伍晋级决赛并获一等奖 |
| 2026 | ASC Student Supercomputer Challenge | 一等奖 |
| 2026 | 华为 ICT 大赛 | 三等奖 |

这些竞赛实践覆盖集群部署、HPL/HPCG 性能优化、AI 模型加速和团队协作等能力。

除竞赛外，团队还开展了 Pixel-Adaptive Convolution（PAC）算子优化研究。通过识别内层循环中的向量化机会，并结合 SIMD、分块和 Tiling 优化访存模式，相关实现在多核 CPU 与异构平台上取得了相对于常规实现的显著加速。

## 上游项目与许可

本项目是 [lcpu-club/hpc-wiki](https://github.com/lcpu-club/hpc-wiki) 的 HITSZ 版本。上游 **HPC Wiki** 源于社区，并由北京大学学生 Linux 俱乐部长期运营和维护；本版本保留上游项目及原作者的署名与贡献记录。

本项目继续采用 [知识共享署名—非商业性使用—相同方式共享 4.0 国际许可协议](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh-hans)（CC BY-NC-SA 4.0）。详细条款见仓库根目录的 [`LICENSE`](https://github.com/HITSZ-HPC-JiuZhang/hpc-wiki/blob/main/LICENSE)。

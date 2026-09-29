# HITSZ HPC Wiki

欢迎来到哈尔滨工业大学（深圳）超算队维护的 HPC Wiki。

本知识库面向刚开始接触高性能计算的学习者，也服务于课程实验、超算竞赛训练与科研实践。内容覆盖并行程序设计、计算机体系结构、CPU/GPU 优化、集群调度、性能分析和常用 Benchmark。

## 从这里开始

- [认识哈尔滨工业大学（深圳）超算队](about/hitsz-hpc.md)：了解计算基础设施、课程体系、训练方向和竞赛成果；
- [并行编程导论](parallel-programming/parallel-programming-intro.md)：理解并行计算的主要模型；
- [CUDA 编程入门](gpu/cuda.md)：从正确性出发学习 GPU 程序设计与优化；
- [性能分析工具](performance-analysis/tools.md)：认识常用的 Profiling 工具；
- [贡献指南](contribute/before-contributing.md)：帮助我们改进内容。

## HITSZ 超算实践

学校通过 CPU 集群、CPU–GPU 异构集群和 ASC 专用训练节点，为教学、科研和竞赛提供计算资源。培养路径从 SIMD、Cache Blocking 等 CPU 单核优化出发，逐步扩展到 OpenMP、MPI 和 CUDA，并覆盖国产 CPU/NPU 平台与 AI 模型部署。

团队在 ASC2022–2023、ASC2024 和 ASC2026 中取得一等奖等成绩，并在 2026 年华为 ICT 大赛获得三等奖。

## 共建开放知识

HPC 竞赛与实践涉及大量共通知识。本项目希望在保留来源与署名的前提下复用优质内容、减少重复建设，并持续补充适合 HITSZ 教学和训练环境的实践资料。

本项目基于 [lcpu-club/hpc-wiki](https://github.com/lcpu-club/hpc-wiki) 适配。上游 **HPC Wiki** 源于社区，并由北京大学学生 Linux 俱乐部长期运营和维护；本版本保留上游项目及原作者署名，并继续采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh-hans) 许可协议。

---

*本页撰写：AI 助手 `deepseek/deepseek-flash`（2026 年 9 月）。*
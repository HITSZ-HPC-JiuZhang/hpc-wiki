# 什么是 HPC

**简介**：本页面向刚接触高性能计算的读者，用一页的篇幅讲清四件事：HPC 是什么、为什么需要它、一台超级计算机由哪些部分组成、以及怎样衡量它的性能。其中穿插的专有名词（FLOPS、Rpeak、HPL 等）都会给出官方出处，方便你继续查证。读完本页后，可以接着读 [HPC 历史](hpc-history.md)，了解这个领域是怎样一步一步形成的。

## 几种权威说法

高性能计算（High Performance Computing，HPC）通常指使用当时性能最强的一批计算机，解决单台普通计算机难以完成的问题。下面是几个机构给出的说法：

- **美国国家科学基金会（NSF）**：超级计算机通常指任何时期世界上最快的一批计算机；现代超级计算机由互连的计算机或处理器组成，同时运行同一个程序的不同部分，速度以每秒浮点运算次数（FLOPS）衡量[^1]。
- **美国能源部（DOE）科学办公室**：高性能计算（通常称为超级计算）提供高速完成复杂计算的能力，让研究者能够研究那些因为过于庞大、过于复杂、过于危险、过于微小或者过于短暂而无法做实验的系统[^2]。
- **欧洲高性能计算联合执行体（EuroHPC JU）**：超级计算机是高度先进的计算机，用于完成极快的计算，通常由数千个并行工作的处理器组成，用来解决标准计算机无法处理的过大或者过于复杂的问题[^3]。
- **美国国家标准与技术研究院（NIST）**：HPC 处理的是超出台式计算机能力与容量的问题；当前的 HPC 技术大致分为承担最前沿问题的领导级系统，以及承担日常计算任务的量产系统[^4]。
- **《中国科学院院刊》**：高性能计算又称超级计算，是计算机科学重要的前沿性分支，历来是衡量一个国家科技水平和创新能力的重要标志[^5]。

术语本身也在演变：美国 1991 年《High-Performance Computing Act》把「high-performance computing」写入法律，2017 年的法案又把联邦法定用语改为「high-end computing」，并在定义中写明「包括过去称为高性能计算的计算」[^6]。

## 为什么需要 HPC：计算成为科学的第三支柱

**理论、实验与计算**三条路径并列，是现代科学研究的常见格局。美国国家科学技术委员会的高端计算工作组在 2004 年写道：过去十年里，对物理现象与工程系统的计算机建模和仿真已被广泛认可为科学与技术的「第三支柱」，与理论和实验平起平坐[^7]。2005 年美国总统信息技术咨询委员会（PITAC）的报告进一步给出定义：计算科学是利用先进计算能力来理解和解决复杂问题，并把它称作「21 世纪科学的第三支柱」[^8]。

需要 HPC 的问题有一个共同特征：**它们的规模超出了普通计算机的能力与容量**。下表是一些官方给出的典型案例。

| 应用方向 | 官方案例 | 来源 |
| --- | --- | --- |
| 天气预报与气候 | 美国 NOAA 用两台「双胞胎」超级计算机承担全国业务化天气预报，扩容后每台 14.5 PFLOPS，合计每秒可处理 29 千万亿次计算，20 多个业务化数值天气预报模式运行其上 | NOAA 官方新闻稿[^9] |
| 天体物理 | NASA 戈达德团队在 Columbia 超级计算机上完成双黑洞旋进并合模拟，使用 2,032 个处理器运行 85 小时，同样的计算在单个处理器上大约需要二十年 | NASA NAS 官方报道[^10] |
| 材料与化学 | 阿贡国家实验室的 Aurora 于 2025 年 1 月上线，研究者用它逐原子模拟纳米金刚石在极端高温高压下的结构变化，在计算机上先行设计材料 | ALCF 官方页面[^11] 与 OLCF 官方报道[^12] |
| 生命科学与药物 | NIH 的 Biowulf 是 95,000+ 核心、40+ PB 的 Linux 集群，面向生物科学中大量并发的作业，以及分子动力学一类的大规模分布式内存任务 | NIH HPC 官方页面[^13] |
| 工程仿真 | NASA 把计算流体力学软件 LAVA 开放给美国航空航天界，用于预测火箭、飞机与航天器周围的气流；在 GPU 超级计算机 Cabeus 上，原本需要数天到数周的问题缩短到数小时 | NASA 官方发布[^14] |
| 人工智能训练 | MLPerf Training 基准测量把模型训练到指定质量目标所需的实际时间，覆盖 DeepSeek v3、Llama 3.1 等模型；厂商提交的成绩已扩展到 8,192 块 GPU 的规模 | MLCommons 官方页面[^15] 与 NVIDIA 官方页面[^16] |

## 性能的尺度：从 FLOPS 到 E 级

衡量 HPC 最常用的单位是 **FLOPS**（每秒浮点运算次数）。美国能源部给了几个直观的坐标：一个人用纸笔做加法的速度大约是每秒 1 次浮点运算，现代个人电脑的处理器大约在 150 GFLOPS 量级，而 E 级的 exascale 计算机可以做到每秒 10^18 次[^17]。前缀本身是国际单位制的标准十进制前缀：giga 为 10^9，tera 为 10^12，peta 为 10^15，exa 为 10^18[^18]。

把几个官方数字放在一条时间线上，就能看出这个尺度是怎样被逐级突破的[^17]：

| 系统 | 年代 | 量级 |
| --- | --- | --- |
| Colossus（英国战时电子计算机） | 1940 年代 | 约 500,000 FLOPS |
| CDC 6600 | 1964 | 约 3 MFLOPS（兆级） |
| Cray-2 | 1985 | 首个超过 1 GFLOPS（十亿级） |
| ASCI Red | 1996 | 首个超过 1 TFLOPS（万亿级） |
| Roadrunner | 2008 | 首个达到 1 PFLOPS（千万亿级） |
| Frontier | 2022 | 首个持续性能超过 1 EFLOPS（百亿亿级） |

用人的算力作参照会更直观：按美国能源部的说法，全世界每个人每秒做一道数学题，连续做五年，才相当于一台 E 级计算机一秒的运算量[^17]；橡树岭国家实验室对 Frontier 给出的换算是四年多[^19]；劳伦斯利弗莫尔国家实验室则说，要一百万部手机同时对一道题做计算，才顶得上 El Capitan 一秒，而这些手机叠起来超过五英里高[^20]。

### 榜单与指标

业界最常引用的榜单是 **TOP500**。官方把两个关键指标定义得很清楚[^21]：

- **Rmax**：实测达到的最大 LINPACK 性能；
- **Rpeak**：理论峰值性能，按硬件参数计算得出，是性能的上限。

TOP500 采用允许自行缩放问题规模并优化软件的 LINPACK（即高并行 LINPACK，HPL），成绩以此进入榜单；官方同时声明，这个成绩并不能代表系统的整体性能[^22]。因为 HPL 只反映解稠密线性方程组的能力，社区又发展出两类补充指标：

- **HPCG**：官方定位为 HPL 的补充，用于测量稀疏矩阵向量乘、向量更新、全局点积等更能代表另一大类应用的计算与访存模式[^23]；
- **HPL-MxP**：面向 HPC 与人工智能负载融合的混合精度指标，用低精度 LU 分解加迭代修正把结果还原到 64 位精度[^24]。

**最新一届榜单**（2026 年 6 月，第 67 期）的前五名如下[^25]：

| 名次 | 系统 | 部署机构 | Rmax |
| --- | --- | --- | --- |
| 1 | LineShine | 国家超级计算深圳中心（NSCS），由深圳云计算中心研制 | 2.198 EFLOPS |
| 2 | El Capitan | 美国劳伦斯利弗莫尔国家实验室 | 1.809 EFLOPS |
| 3 | Frontier | 美国橡树岭国家实验室 | 1.353 EFLOPS |
| 4 | Aurora | 美国阿贡国家实验室 | 1.012 EFLOPS |
| 5 | JUPITER Booster | 德国于利希超级计算中心（EuroHPC） | 1.000 EFLOPS |

其中 LineShine 使用自研的「LingKun」平台、304 核的 LX2 处理器、自研 LingQi 互连与麒麟操作系统，共 13,789,440 个核心，功耗约 42.2 兆瓦，能效为 52.07 GFLOPS/W；它是 TOP500 上首个仅用 CPU 就把持续双精度性能推过 2 EFLOPS 的系统，也是 2017 年「神威·太湖之光」之后再次由中国系统登顶[^26]。这一届榜单上共有五台 E 级系统，全榜 500 台机器合计 Rmax 超过 18.73 EFLOPS，入榜门槛提高到 2.66 PFLOPS[^27]。作为对比，1993 年 6 月首期榜单的第一名 CM-5/1024 的 Rmax 是 59.70 GFLOPS[^28]。

能效方面，Green500 榜单追踪单位功耗下的性能，最新一届的第一名 KAIROS 达到 73.28 GFLOPS/W[^26]。关于这些基准的更多细节，见 [Benchmark 章节](../benchmark/intro.md)、[HPL](../benchmark/hpl.md) 与 [HPCG](../benchmark/hpcg.md)。

## 一台超级计算机由什么组成

从使用者角度看，一台超级计算机与一台笔记本的差别，首先体现在**使用方式**上。爱丁堡大学 EPCC 的入门教材这样描述：HPC 系统是面向计算密集负载的独立资源，由大量集成的计算与存储部件组成；输入数据的组织、程序参数的配置、结果的取回方式都与普通笔记本不同，图形界面通常让位给命令行，而所有与计算节点的交互都由一个专门软件——**调度器**（例如 Slurm）来管理，以便成千上万的用户共享同一套系统[^29][^30]。

劳伦斯利弗莫尔国家实验室的入门教程给出了更具体的画面[^31]：

- **计算节点**：本质上是一台独立的计算机，自包含、无盘、多核，没有键盘、鼠标与显示器，全部管理通过网络从管理节点进行；
- **登录节点**：用于编辑文件、提交作业、编译程序等交互工作，教程特别标注「不要在登录节点上运行生产作业」；
- **批处理节点**：承担生产工作，作业通过批调度器（Slurm、Flux 等）提交；
- **互连**：集群标配高速网络（InfiniBand、Omni-Path、Slingshot 等）；
- **存储层级**：个人目录、共享工作区、随时会被清理的临时文件系统、多 PB 级的 Lustre 并行文件系统，以及 PB 级的磁带归档系统 HPSS。

关于集群、调度与模块环境的更多内容，见[超算平台](../platform/platform-intro.md)、[集群](../platform/cluster.md)、[作业调度](../platform/scheduling.md)与[环境管理](../operations/environment.md)；硬件层面的细节见[互连](../hardware/interconnect.md)与[存储](../hardware/storage.md)。

## HPC 难在哪里：三道墙与并行度

把计算拆到成千上万个处理器上并行执行，是 HPC 获得性能的基本手段，但收益有硬性上限。**Amdahl 定律**指出，程序能获得的加速比受可并行代码比例的限制；劳伦斯利弗莫尔国家实验室的教程给出的形式是：加速比上限约为 1/(1−P)，其中 P 是可以并行的部分[^32]。问题规模不变、单纯增加处理器的做法称为强扩展[^32]。

硬件层面还有更深的原因。伯克利加州大学 2006 年的技术报告《The Landscape of Parallel Computing Research: A View from Berkeley》总结了三条「墙」[^33]：

- **内存墙**：旧观念认为乘法慢、读写快；新观念是读写慢、乘法快——访问一次 DRAM 可能要 200 个时钟周期，而一次浮点乘法可能只要 4 个周期；
- **功耗墙**：旧观念认为功耗免费、晶体管昂贵；新观念是功耗昂贵、晶体管「免费」，芯片上能放的晶体管数量超过了供电所能同时开启的数量；
- **ILP 墙**：单处理器依靠指令级并行继续提升性能的路径同样受阻。

三条墙叠加，报告称之为「砖墙」：单处理器性能每 18 个月翻倍的时代在 2006 年前后结束，并行成了继续提升性能的主要方向[^33]。这也是 HPC 与[并行编程](../parallel-programming/parallel-programming-intro.md)密不可分的原因，内存与通信两方面的细节见[内存模型](../memory-model/intro.md)与[通信](../communication/intro.md)。

## 与几个相邻概念的关系

- **高吞吐计算（HTC）**：威斯康星大学麦迪逊分校的高吞吐计算中心指出，对很多科学家来说，真正要衡量的是每月、每年能从计算环境里取得多少浮点运算，每秒能取得多少属于次要问题；这种以吞吐量最大化为目标的模式被称为 HTC，它与 HPC 的区分由该中心团队在 1996 年提出[^34]。
- **云上 HPC**：微软把 HPC（又称 big compute）描述为使用大量基于 CPU 或 GPU 的计算机求解复杂数学任务，云上系统与原位系统的主要差别是资源可以按需动态增减[^35]。EPCC 的教材补充了一个物理约束：HPC 系统是独立资源，必须存在于特定且固定的地点，因为网络线缆长度与电信号、光信号的速度都有上限[^30]。
- **数据中心**：数据中心是承载计算设施的物理场所，能效常用 PUE 衡量，即总输入功率与 IT 负载功率之比，越接近 1 越好[^36]。
- **AI 训练集群**：厂商推出的整机式 AI 数据中心平台（例如 NVIDIA DGX SuperPOD）把计算、存储、网络、软件与管理集成在一起，可扩展到数万块 GPU，用于训练万亿参数规模的生成式模型[^37]。

## 总结与阅读路径

记住三条主线，就抓住了 HPC 的轮廓：**性能存在量级阶梯**（GLOPS、TLOPS、PFLOPS、EFLOPS，每一级对应一个时代）；**系统由节点、互连、存储与调度器组成**，使用方式与个人计算机差别很大；**并行是主要手段，但受并行度、内存与功耗的限制**。

继续阅读：

- [HPC 历史](hpc-history.md)：从 ENIAC 到 E 级系统的完整脉络，以及中国超算的发展路径；
- [现代 HPC](modern-hpc.md)：当前的体系结构与应用格局；
- [超算平台](../platform/platform-intro.md)：集群、云与作业调度的具体使用；
- [并行编程导论](../parallel-programming/parallel-programming-intro.md) 与 [GPU 编程](../gpu/intro.md)：把程序真正跑快的技术路线；
- [Benchmark](../benchmark/intro.md)：HPL、HPCG、MLPerf 等评测基准的细节；
- [HITSZ 超算队](../about/hitsz-hpc.md)：本校的计算基础设施与训练路径。

---

*本页撰写：AI 助手 `deepseek/deepseek-flash`（2026 年 10 月）；事实与来源见页面内引用。*

## 参考资料

[^1]: [Supercharging Science with Supercomputers](https://www.nsf.gov/impacts/supercomputers)（美国国家科学基金会）
[^2]: [Advanced Scientific Computing Research](https://www.energy.gov/science/ascr/advanced-scientific-computing-research)（美国能源部科学办公室）
[^3]: [Supercomputers](https://www.eurohpc-ju.europa.eu/supercomputers_en)（欧洲高性能计算联合执行体）
[^4]: [High Performance Computing](https://www.nist.gov/programs-projects/high-performance-computing)（美国国家标准与技术研究院）
[^5]: [中国超算产业发展现状分析](http://old2022.bulletin.cas.cn/publish_article/2019/6/20190604.htm)（《中国科学院院刊》2019 年第 6 期，作者历军）
[^6]: [15 U.S.C. §5503 Definitions](https://www.govinfo.gov/content/pkg/USCODE-2023-title15/html/USCODE-2023-title15-chap81-sec5503.htm)（美国法典 2023 年版，美国政府出版局）
[^7]: [Federal Plan for High-End Computing](https://www.nitrd.gov/pubs/2004_hecrtf/20040510_hecrtf.pdf)（美国 NITRD 高端计算振兴工作组报告，2004 年 5 月）
[^8]: [Computational Science: Ensuring America's Competitiveness](https://www.nitrd.gov/pubs/pitac/pitac_report_computational-science_2005.pdf)（美国总统信息技术咨询委员会报告，2005 年 6 月）
[^9]: [NOAA completes upgrade to weather and climate supercomputer system](https://www.noaa.gov/news-release/noaa-completes-upgrade-to-weather-and-climate-supercomputer-system)（美国国家海洋和大气管理局，2023-08-10）
[^10]: [Spacetime Simulations and the Discovery of Gravitational Waves](https://www.nas.nasa.gov/pubs/stories/2019/feature_gravitational_waves_Centrella.html)（NASA 先进超算部门，2019-04-18）
[^11]: [Aurora](https://www.alcf.anl.gov/aurora)（美国阿贡国家实验室领导计算设施）
[^12]: [Nanodiamonds and Beyond: Designing Carbon Materials with Artificial Intelligence at Exascale](https://www.olcf.ornl.gov/2026/03/16/nanodiamonds-and-beyond-designing-carbon-materials-with-artificial-intelligence-at-exascale/)（美国橡树岭领导计算设施，2026-03-16）
[^13]: [NIH HPC Systems](https://hpc.nih.gov/systems/)（美国国立卫生研究院高性能计算组）
[^14]: [NASA Releases Powerful LAVA Software to US Aerospace Industry](https://www.nasa.gov/aeronautics/nasa-releases-powerful-lava-software-to-us-aerospace-industry/)（美国国家航空航天局，2026-04-23）
[^15]: [MLPerf Training](https://mlcommons.org/benchmarks/training/)（MLCommons）
[^16]: [MLPerf Benchmarks](https://www.nvidia.com/en-us/data-center/resources/mlperf-benchmarks/)（NVIDIA）
[^17]: [DOE Explains...Exascale Computing](https://www.energy.gov/science/doe-explainsexascale-computing)（美国能源部科学办公室，2021-11-09 发布，2026-03-11 更新）
[^18]: [Metric (SI) Prefixes](https://www.nist.gov/pml/owm/metric-si-prefixes)（美国国家标准与技术研究院）
[^19]: [Frontier: America's Exascale Computing Future](https://www.ornl.gov/file/oak-ridge-leadership-computing-facility-frontier-fact-sheet-0/display)（美国橡树岭国家实验室介绍材料，2023 年 7 月）
[^20]: [El Capitan High Performance Computing](https://www.llnl.gov/news/highlights/el-capitan-high-performance-computing)（美国劳伦斯利弗莫尔国家实验室）
[^21]: [TOP500 Description](https://top500.org/project/top500_description/)（TOP500 官方）
[^22]: [The Linpack Benchmark](https://top500.org/project/linpack/)（TOP500 官方）
[^23]: [HPCG Benchmark](https://www.hpcg-benchmark.org/)（HPCG 官方，田纳西大学与桑迪亚国家实验室）
[^24]: [HPL-MxP Mixed-Precision Benchmark](https://hpl-mxp.org/)（HPL-MxP 官方）
[^25]: [TOP500 List - June 2026](https://www.top500.org/lists/top500/2026/06/)（TOP500 官方，2026-06-23 发布）
[^26]: [LineShine Debuts at No. 1 as the TOP500 Enters a New Global Exascale Era](https://www.top500.org/news/lineshine-debuts-no-1-top500-enters-new-global-exascale-era/)（TOP500 官方新闻稿，2026-06-23）
[^27]: [TOP500 Highlights - June 2026](https://www.top500.org/lists/top500/2026/06/highs/)（TOP500 官方）
[^28]: [TOP500 List - June 1993](https://www.top500.org/lists/top500/1993/06/)（TOP500 官方）
[^29]: [Working on a remote HPC system](https://epcced.github.io/2025-10-14-archer2-intro-hpc/12-cluster.html)（爱丁堡大学 EPCC，ARCHER2 入门教材）
[^30]: [Why do we use HPC?](https://epcced.github.io/2025-10-14-archer2-intro-hpc/11-hpc-intro.html)（爱丁堡大学 EPCC，ARCHER2 入门教材）
[^31]: [Livermore Computing Resources and Environment](https://hpc.llnl.gov/documentation/tutorials/livermore-computing-resources-and-environment)（美国劳伦斯利弗莫尔国家实验室，2026 年 2 月版教程）
[^32]: [Introduction to Parallel Computing Tutorial](https://hpc.llnl.gov/documentation/tutorials/introduction-parallel-computing-tutorial)（美国劳伦斯利弗莫尔国家实验室）
[^33]: [The Landscape of Parallel Computing Research: A View from Berkeley](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2006/EECS-2006-183.pdf)（伯克利加州大学电气工程与计算机科学系技术报告 UCB/EECS-2006-183，2006-12-18）
[^34]: [What is High Throughput Computing?](https://web.archive.org/web/20251224052225/https://chtc.cs.wisc.edu/htc.html)（威斯康星大学麦迪逊分校高吞吐计算中心，经 Internet Archive 存档）
[^35]: [High-Performance Computing (HPC) on Azure](https://learn.microsoft.com/en-us/azure/architecture/guide/compute/high-performance-computing)（微软 Azure 架构中心）
[^36]: [The EU Code of Conduct for Data Centres](https://joint-research-centre.ec.europa.eu/jrc-news-and-updates/eu-code-conduct-data-centres-towards-more-innovative-sustainable-and-secure-data-centre-facilities-2023-09-05_en)（欧盟委员会联合研究中心，2023-09-05）
[^37]: [NVIDIA DGX SuperPOD](https://www.nvidia.com/en-us/data-center/dgx-superpod/)（NVIDIA）

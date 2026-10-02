# HPC 历史

**简介**：本页按时间顺序梳理高性能计算的发展脉络：从计算机诞生之初的科学计算需求，到巨型机、向量机、并行集群，再到今天的 E 级系统；随后单独讲中国超算的路径，并说明这个方向是怎样一步步成为一个有会议、有学会、有榜单、有国家级计划的专门领域的。全部数字与事件都给出了出处，方便你继续查证。

如果用一句话概括这段历史：**科学计算的需求从计算机诞生之初就存在，而 HPC 作为一个专门领域，是在 1970—1990 年代逐步定型的**——1982 年的 Lax 报告、1984 年的美国国家科学基金会超算中心计划、1986 年起的 ISC 会议、1988 年起的 SC 会议、1991 年的《High-Performance Computing Act》与 1993 年诞生的 TOP500 榜单，都是这一时期的标志性事件[^1][^2][^3][^4]。

## 一、科学计算：从计算机诞生之初就存在（1940s–1950s）

**ENIAC** 的诞生就是为了满足弹道计算需求。它于 1943—1945 年建造，是第一台以电子速度运行、不受机械部件拖慢的大型计算机，使用约 18,000 只电子管，平均每一到两天就要更换一只[^5]。1945 年 12 月 10 日，它首次投入实际计算，求解的正是洛斯阿拉莫斯实验室的一个数学问题；1946 年 2 月向公众演示[^6]。洛斯阿拉莫斯国家实验室的回顾给出了直观对比：一项人工需要 20 小时的计算，ENIAC 只需 30 秒[^7]。

同一时期，**存储程序**的思想被写进了文本。1945 年 6 月 30 日署名的《First Draft of a Report on the EDVAC》被公认为最早记录「用同一大内存同时存放指令与数据」这一优势的文稿[^8]。1946 年的另一份报告《Preliminary Discussion of the Logical Design of an Electronic Computing Instrument》把机器划分成算术、存储、控制、输入输出等主要部分，并计划了约 4,000 个 40 位二进制数的存储能力；依据这套设计建造的 IAS 机器于 1952 年投入运行，此后有 17 台同型机器在世界各地建造，成为第一代数字计算机的原型[^9]。

随后登场的商用机器迅速把科学计算当作主要市场。IBM SSEC 于 1948 年揭幕，专门服务科学计算，其首个大项目是计算月球位置[^10]。IBM 701 于 1952 年发布，每秒可完成 16,000 次以上加减运算或 2,000 次以上乘除运算，洛斯阿拉莫斯在 1953 年租用了第一台商用 701[^11]；1954 年发布的 IBM 704 是第一台带全自动浮点运算指令的量产大型机，首次配备磁芯存储[^12]。1957 年，FORTRAN 在 IBM 704 上出现，此后数十年一直是科学与技术计算最常用的语言[^13]。

中国在几乎同一时期起步：1958 年 8 月，103 机可以运行短程序，成为中国第一台通用数字电子计算机；1959 年国庆节宣布试制成功的 104 机浮点运算速度为每秒一万次，是当时国内最快的计算机，承担过中国第一颗原子弹研制中的计算任务[^14]。

## 二、巨型机与向量机时代（1960s–1980s）

博物馆对「超级计算机」的定义带着一份清醒：**「超级」是相对的**，每个时代都有自己的超级计算机，定义随技术进步而变，今天的超级计算机可能成为明天的个人电脑；早期的超级计算机是政府或军方的单台机器，只有他们负担得起[^15]。1961 年，IBM 董事长小托马斯·沃森在公开场合使用了「supercomputers」这一说法[^16]。

**第一代巨型机**在 1960 年前后出现。IBM 7030「Stretch」1960 年发布、1961 年交付洛斯阿拉莫斯，可同时运行 9 个程序，「让计算机同时做许多事」的思路成为此后超级计算机的基本原则；它原计划达到 704 的 100 倍速度，实际只做到 30—40 倍，共建造 9 台[^16]。Remington Rand 的 UNIVAC LARC 于 1960 年交付劳伦斯利弗莫尔实验室，占地近 3,000 平方英尺，两台机器却直接促使 IBM 上马 Stretch[^9]。

**CDC 6600（1964）** 由西摩·克雷设计，刷新了速度纪录，共售出约 100 台，直到 1969 年才被同样出自克雷之手的 CDC 7600 超过；美国能源部的科普材料把 CDC 6600 记为 1964 年第一台达到约 3 MFLOPS 的超级计算机[^17][^18]。CDC 7600 在 1969 年上市，性能约为 6600 的 10 倍[^7]。**ILLIAC IV（1972）** 是第一台大规模并行处理计算机，采用单指令多数据（SIMD）结构，64 个处理单元，运行于 NASA 艾姆斯研究中心[^19]。

**Cray-1（1976）** 与它背后的公司是这一时代的符号。西摩·克雷 1972 年自创 Cray Research，1976 年完成的 Cray-1 从 1976 年到 1982 年保持世界最快，比同代机器快约 10 倍，售价最高可达 1,000 万美元，功耗 115 千瓦；它用向量处理把一条指令同时作用到多个数据上，这套设计主导了从 1970 年代到 1990 年代初的超级计算机[^20]。1985 年的 Cray-2 则成为第一台超过 1 GFLOPS 的超级计算机[^18]。

**日本厂商的进入**改变了竞争格局。富士通 FACOM VP-100/VP-200 于 1982 年 7 月发布，日立 HITAC S-810 于 1982 年 8 月发布，NEC SX-2 于 1983 年 4 月发布，是有记录的首台突破 1 GFLOPS 的超级计算机；富士通第二代 VP2000 系列在 1988 年 12 月把单 CPU 速度推到 5 GFLOPS[^21]。美国国会技术评估办公室 1991 年的报告直言竞争压力主要来自日本企业，并点名日本政府的相关计划[^22]。

美国的政策回应同样密集。1982 年 12 月 26 日，以彼得·拉克斯为主席的小组提交《Report of the Panel on Large Scale Computing in Science and Engineering》（通称 Lax 报告），建议建立国家级计划推进先进计算技术的使用[^23]。美国国家科学基金会（NSF）据此在 1984 年设立超算中心计划，1985 年建立四个中心、1986 年增加第五个：NCSA、康奈尔理论中心、普林斯顿的约翰·冯·诺依曼中心、SDSC 与匹兹堡超算中心（PSC），为研究社区提供「向量超算服务」与培训[^24][^25]。1987 年到 1991 年间，美国又连续出台多份官方报告，1991 年的法案把这种关注上升为国家法律[^22]。

## 三、并行革命与集群（1980s–1990s）

**超立方体与大规模并行**在 1980 年代中后期进入市场。加州理工学院的 Cosmic Cube 于 1983 年夏组装、10 月开始运行，64 个节点，制造成本 8 万美元[^26]。1985 年前后，Intel iPSC（32 至 128 个处理器）、Thinking Machines 的 Connection Machine 与 nCUBE 相继出现；Thinking Machines 的 CM-1 采用最多 65,536 个单比特处理器与 12 维超立方体互连，CM-5 转为 MIMD 结构，其在洛斯阿拉莫斯的最大配置达到 1,056 个处理器，并以近 60 GFlop/s 的成绩成为 1993 年 6 月首期 TOP500 榜单的第一名[^27][^28]。同一时期还有 MasPar 的 SIMD 系统与 Kendall Square Research 的 KSR1（1991 年交付，主打共享内存架构）[^28]。

Cray 也转向大规模并行：1993 年的 T3D 是 Cray 首台大规模并行处理系统，首位客户是匹兹堡超算中心；1995 年的 T3E 被官方称为世界首台在真实应用上持续达到 1 TFLOPS 的超级计算机[^29]。

**ASCI 计划**把并行计算推向了国家级工程。为在核试验停止后继续维持核武库安全评估，美国能源部在 1994 年开始的科学基础库存管理计划中设立了「加速战略计算倡议」（ASCI），目标是在 1995—2005 年的十年间把利弗莫尔的计算能力提升 7,000 倍以上[^30]。该计划的成果之一 ASCI Red 由 Intel 建造、部署于桑迪亚国家实验室，1996 年 12 月首次突破 1 TFLOPS，1997 年 6 月至 2000 年 6 月连续七次位居 TOP500 榜首[^31]。

**集群路线**则来自另一条思路：用商品化部件拼出廉价并行系统。1994 年，NASA 戈达德太空飞行中心的 Thomas Sterling 与 Don Becker 用 16 台 486DX4 处理器通过以太网互联搭出第一台 Beowulf 集群，名字叫 Wiglaf，最初的目标是「5 万美元以内的一 GFLOPS 工作站」[^32]。同一年，伯克利加州大学提出「工作站网络」（NOW）的设想，用商品化工作站与高性能交换机构建廉价、低延迟、可扩展的大规模并行系统，论文中描述的系统是 105 台 Sun Ultra 170 工作站加 Myricom 网络[^33]。集群最终成为 HPC 的主流形态之一，「超算平台」章节介绍的集群与调度就是这一路线的延续。

**软件标准化**是并行编程能够普及的前提。PVM 的最初版本 1989 年夏在橡树岭国家实验室写成，其思路是把异构计算机集合变成统一的并发计算资源[^34]。MPI 的标准化进程始于 1992 年 4 月弗吉尼亚州威廉斯堡的工作坊，1994 年发布 MPI 1.0；阿贡国家实验室在论坛成立时承诺立刻提供实现，这就是 MPICH[^35][^36]。OpenMP 的 Fortran 版 1.0 规范于 1997 年 10 月发布，C/C++ 版于 1998 年 10 月发布[^37]。

**榜单、会议与法案**在这十年里先后出现。TOP500 的前身 1993 年 6 月在德国曼海姆的一场会议上首次发布，同年 11 月又发布一期，此后每半年一期延续至今[^38][^39]。SC 系列会议始于 1988 年的奥兰多[^40]；戈登·贝尔奖 1987 年由戈登·贝尔创立，用于追踪并行计算的进展[^41]。1991 年 12 月 9 日签署的《High-Performance Computing Act》（美国公法 102-194）是美国第一份联邦高性能计算与网络研究的协调计划，直接促成了 1992 年初建立的 HPCC 计划（即后来 NITRD 的前身）[^42]。

## 四、从 TFLOPS 到 PFLOPS（1997–2019）

进入本世纪，榜首位置的更替可以当作 HPC 能力的刻度尺：

| 时间 | 系统 | 榜单成绩 | 备注 |
| --- | --- | --- | --- |
| 1997 | ASCI Red | 1.068 TFLOPS | 首台突破 TFLOPS，连续七期第一[^31] |
| 2002 | Earth Simulator | 35.86 TFLOPS | 连续五期第一[^43] |
| 2004 | Blue Gene/L | 70.72 TFLOPS → 478.2 TFLOPS | 连续七期第一[^44] |
| 2008 | Roadrunner | 1.026 PFLOPS | 首台突破 PFLOPS[^45] |
| 2010 | Tianhe-1A | 2.566 PFLOPS | 中国系统首次登顶[^46] |
| 2011 | K computer | 8.162 → 10.51 PFLOPS | 首台超过 10 PFLOPS[^47] |
| 2012 | Sequoia / Titan | 16.32 / 17.59 PFLOPS | 混合 CPU-GPU 架构起步[^48][^49] |
| 2013–2015 | Tianhe-2 | 33.86 PFLOPS | 连续六期第一[^50] |
| 2016–2017 | Sunway TaihuLight | 93.01 PFLOPS | 全部采用国产处理器[^51] |
| 2018–2019 | Summit | 122.3 PFLOPS | CPU-GPU 混合架构，峰值 200 PFLOPS[^52] |
| 2020–2021 | Fugaku | 415.5 PFLOPS | 首个以 ARM 处理器登顶的系统[^53] |

其中几条线值得单独说明：

- **Earth Simulator** 由 NEC 制造，2002 年 6 月以 35.86 TFLOPS 登顶并保持五期，日本信息处理学会把它列为信息处理技术遗产，JAMSTEC 至今仍在运行其后继系统[^43]。
- **Blue Gene 系列**由 IBM 为劳伦斯利弗莫尔国家实验室打造，经多次扩容后连续七期第一，峰值达到 596 TFLOPS；2007 年推出的 Blue Gene/P 可以配置到 3 PFLOPS 以上，阿贡国家实验室的 Intrepid 与于利希的 JUGENE 都属这一系列[^44][^54]。
- **Roadrunner** 由 IBM 为洛斯阿拉莫斯制造，使用 12,960 颗 PowerXCell 8i 与 6,480 颗 AMD Opteron 组成的混合架构，2008 年 5 月突破 PFLOPS 屏障，6 月榜单正式记录为 1.026 PFLOPS[^45]。
- **加速器进入超算**是这一阶段的另一条主线：NVIDIA 于 2006 年推出 CUDA，使计算负载可以直接使用 GPU 的吞吐能力；天河一号 A（2010）与 Titan（2012）都把 GPU 纳入体系结构，Summit 则把「CPU 加 GPU」的混合架构推到 122.3 PFLOPS 的规模[^55][^46][^49][^52]。

## 五、中国超算之路（1958 至今）

中国的路径从仿制起步，逐步走到全国产系统与体系化布局。

- **银河系列**：1978 年，中共中央和国务院把研制亿次巨型计算机的任务交给国防科技大学，1983 年研制成功，「银河-I」的向量运算速度达到每秒一亿次以上，使中国成为继美国、日本之后第三个能研制巨型机的国家；1983 年 5 月起，国家组织 29 个单位的 95 名专家成立鉴定组，最终确认硬件向量运算速度达标[^56]。总设计师慈云桂立下「五年时间，一天也不能多！亿次速度，一次也不能少！」的誓言[^57]。1992 年完成的「银河-II」是我国第一台十亿次巨型机，采用 4 个中央处理器并行协同工作，总设计师为周兴铭[^58]；1997 年 6 月 19 日，「银河-III」通过国家鉴定，运算速度每秒百亿次，峰值每秒 130 亿次[^59][^60]。
- **曙光系列**：1990 年 3 月，863 计划的研究开发实体——国家智能计算机研究开发中心依托中国科学院计算技术研究所成立，确定以并行处理为基础的高性能计算机系统为主攻方向；1993 年 10 月，「曙光一号」通过成果技术鉴定，是国内第一台全对称共享存储多处理机，研制经费约 200 万元[^61]。此后曙光 1000（1995 年，实际运算速度超过每秒 10 亿次浮点运算）、曙光 2000、曙光 3000 陆续推出；2004 年通过鉴定的曙光 4000A 峰值达到每秒 11.2 万亿次，Linpack 实测每秒 8.06 万亿次，在 2004 年 6 月的 TOP500 榜单上位列第十[^62]。
- **神威系列与技术跨越**：1999 年，国家并行计算机工程技术研究中心研制的神威-I 在国家气象中心投入使用，峰值每秒 3840 亿次[^60]。「神威」系列总设计师金怡濂把我国高性能计算机的峰值运算速度从每秒 10 亿次推进到每秒 3000 亿次以上，获得 2002 年度国家最高科学技术奖[^63]。
- **超算中心体系**：2009 年 5 月，科技部批准成立国家超级计算天津中心，随后批准深圳、济南、长沙、广州、无锡等国家级超算中心，截至 2019 年已建成六家[^64]。以深圳中心为例：2009 年批复成立，2010 年 5 月其主机系统以每秒 1.27 千万亿次的持续运算速度在 TOP500 排名世界第二，2011 年 11 月正式投入运行[^65]。
- **天河系列与神威·太湖之光**：2009 年 10 月，中国首台千万亿次超算「天河一号」诞生，峰值每秒 1206 万亿次；2010 年 11 月，「天河一号 A」以每秒 2566 万亿次的 Linpack 成绩登顶世界第一[^60][^46]。2013 年 6 月，「天河二号」以 33.86 PFLOPS 再次登顶，并连续六期保持第一[^50]。「神威·太湖之光」于 2015 年 12 月 31 日研制完成，2016 年 6 月以 93.01 PFLOPS 登顶，其申威众核处理器与互连网络均为自主研制；三项全机应用在 2016 年入围戈登·贝尔奖并获奖，2017 年「非线性地震模拟」再获该奖[^51][^66]。2018 年，神威 E 级原型机在济南中心启用，「天河三号」E 级原型机也在天津完成部署并通过分项验收[^67][^68]。
- **重返榜首**：2026 年 6 月 23 日，部署于国家超级计算深圳中心的「灵晟」以 2.198 EFLOPS 的持续双精度性能登顶 TOP500，成为 2017 年「神威·太湖之光」之后首个领跑榜单的中国系统。它采用自研 LX2 处理器与灵启互连，是全榜首台仅用 CPU 就把持续性能推过 2 EFLOPS 的系统，功耗约 42.2 兆瓦，能效 52.07 GFLOPS/W[^69]。深圳中心给出的技术细节包括：LX2 集成首颗国产 HBM，内存带宽相比传统 CPU 提升 10 倍；灵启互连可支持 200 万个端口、10 万节点组网；整机 100% 采用全液冷散热；在大规模并行环境下的平均扩展效率为 84.4%[^70]。

## 六、E 级时代（2022 至今）

- **Frontier**（橡树岭国家实验室）在 2022 年 5 月 30 日公布的第 59 期榜单上以 1.102 EFLOPS 成为「第一台真正的 E 级机器」，也是美国首台 E 级系统[^71]。
- **Aurora**（阿贡国家实验室）在 2024 年 5 月的榜单上以 1.012 EFLOPS 正式跨过 E 级门槛，2025 年 1 月上线[^72]。
- **El Capitan**（劳伦斯利弗莫尔国家实验室）在 2024 年 11 月以 1.742 EFLOPS 登顶，是第三台 E 级系统，也是首台服务于国家安全用途的 E 级机器；2025 年 11 月重测为 1.809 EFLOPS[^73]。
- **JUPITER Booster**（德国于利希超级计算中心，EuroHPC）在 2025 年 11 月以恰好 1.000 EFLOPS 成为欧洲首台 E 级系统[^74]。
- **灵晟**（深圳）在 2026 年 6 月登顶后，五台 E 级系统首次同时分布于亚洲、北美与欧洲[^69]。

这一阶段还有三个趋势值得记住。**能效成为与性能并列的指标**：Green500 于 2007 年 11 月首次发布榜单，第一期榜首为 357 MFLOPS/W，2016 年起与 TOP500 统一提交规则；2026 年 6 月的最新一届榜首 KAIROS 达到 73.28 GFLOPS/W[^75]。**人工智能与科学计算融合**：美国能源部科学办公室把 AI 与机器学习视为从超大规模数据中得出新见解的途径，并把百亿亿次计算计划（ECP）视为支撑未来 AI 的软硬件基础[^76]。**云与容器进入主流**：微软 Azure 上的 Eagle 系统在 2024 年 11 月位列 TOP500 第四，是当时排名最高的云端系统；Apptainer 等项目让容器在无特权用户的 HPC 环境中可用；橡树岭国家实验室则在 2026 年把 20 量子比特的量子计算机接入经典 HPC 环境，探索二者集成[^73][^77][^78]。

## 七、这个领域是怎样形成的

把以上事件串起来可以看到，HPC 作为专门领域经历了一个逐步确立的过程：**学术共同体、政府计划、评价体系与人才培养**在 1980—2000 年代相继建立起来。

- **会议与学会**：ISC 的前身是 1986 年曼海姆大学的「Supercomputer Seminar」，SC 系列始于 1988 年；ACM 的高性能计算特别兴趣小组（SIGHPC）2011 年 11 月在 SC11 上首次亮相，是主要专业学会中第一个专为 HPC 群体设立的国际性组织；IEEE 计算机学会的 HPC 技术组织（TCHPC）2017 年成立；SIAM 的计算科学与工程（CSE）会议首届于 2000 年 9 月在华盛顿举行[^4][^40][^79][^80][^81]。
- **期刊**：《Journal of Parallel and Distributed Computing》第 1 卷第 1 期出版于 1984 年 8 月；《International Journal of High Performance Computing Applications》由 SAGE 出版，创刊主编为斯坦福大学的 Joanne Martin，现任主编之一是 Jack Dongarra[^82]。
- **国家级计划与设施**：NSF 的超算中心计划（1984）后来演进为 PACI、TeraGrid（2001）、XSEDE（2011）与 ACCESS（2022）；美国能源部的 INCITE 计划由副部长 Raymond Orbach 于 2003 年启动，2004 年在橡树岭、2006 年在阿贡分别建立领导级计算设施；欧洲方面，PRACE 于 2010 年 4 月成立，EuroHPC 联合执行体于 2018 年成立[^24][^83][^84][^85]。
- **关键报告**：1982 年 Lax 报告[^23]、1992 年发布的《Grand Challenges 1993》蓝皮书[^86]、2004 年高端计算振兴工作组的《Federal Plan for High-End Computing》（提出建模与仿真已成为科学技术的「第三支柱」）[^87]、2005 年 PITAC 报告《Computational Science: Ensuring America's Competitiveness》[^88]、2006 年伯克利视图报告与 2010 年的 E 级计算咨询报告[^89][^90]。
- **术语的演变**：1991 年的法案把「high-performance computing」写入法律，2017 年的《American Innovation and Competitiveness Act》把联邦法定用语改为「high-end computing」，并在定义中写明「包括过去称为高性能计算的计算」；美国 NITRD 体系在 2013 年的文件中明确把「high end computing」「high performance computing」与「supercomputing」当作同义词[^91]。
- **教育与人才**：爱丁堡大学 EPCC 的 HPC 硕士项目自 2001 年开办，持续为这个领域输送人才；面向研究者的 HPC Carpentry 教学体系在 2024 年进入 Carpentries 课程孵化阶段；学生竞赛方面，SC 的学生集群竞赛 2007 年创办，ASC 学生超算竞赛首届于 2012 年举行[^92][^93][^94]。

## 八、里程碑一览

| 年份 | 事件 |
| --- | --- |
| 1945 | ENIAC 首次投入计算；EDVAC 报告提出存储程序的构想 |
| 1948 | IBM SSEC 揭幕，明确以科学计算为主要用途 |
| 1957 | FORTRAN 在 IBM 704 上发布 |
| 1959 | 中国 104 机试制成功，承担原子弹研制的计算任务 |
| 1960–1961 | IBM 7030「Stretch」交付，第一代巨型机登场 |
| 1964 | CDC 6600 刷新速度纪录 |
| 1972 | Cray Research 成立；ILLIAC IV 运行 |
| 1976 | Cray-1 发布，向量机时代开始 |
| 1982 | 日本厂商发布向量机；Lax 报告提交 |
| 1983 | 中国「银河-I」研制成功；加州理工 Cosmic Cube 运行 |
| 1984–1986 | NSF 超算中心计划启动；ISC 会议（1986）与 SC 会议（1988）先后开办 |
| 1991 | 美国《High-Performance Computing Act》通过 |
| 1993 | TOP500 首期发布；「曙光一号」通过鉴定；Cray T3D 交付 |
| 1994 | Beowulf 集群与伯克利 NOW 项目启动；MPI 1.0 发布 |
| 1996–1997 | ASCI Red 突破 1 TFLOPS 并登顶；OpenMP 发布；「银河-III」通过鉴定 |
| 1999 | 神威-I 投入使用 |
| 2002 | Earth Simulator 登顶，日本向量机达到 35.86 TFLOPS |
| 2004 | Blue Gene/L 登顶；曙光 4000A 进入 TOP500 第十 |
| 2008 | Roadrunner 成为首台 PFLOPS 系统 |
| 2010 | 「天河一号 A」登顶，中国系统首次位列世界第一 |
| 2011 | K computer 突破 10 PFLOPS |
| 2013 | 「天河二号」登顶并连续六期第一 |
| 2016 | 「神威·太湖之光」以全国产处理器登顶 |
| 2018 | Summit 登顶；中国 E 级原型机（神威、天河三号）完成部署 |
| 2020 | Fugaku 成为首台以 ARM 处理器登顶的系统 |
| 2022 | Frontier 成为首台 E 级系统 |
| 2024 | Aurora 与 El Capitan 先后跨过 E 级门槛 |
| 2025 | JUPITER Booster 成为欧洲首台 E 级系统 |
| 2026 | 「灵晟」以 2.198 EFLOPS 登顶，五台 E 级系统跨越三大洲 |

## 九、总结与延伸阅读

这段历史有两条互相交织的线索：**性能阶梯**从每秒几千次运算一路走到每秒 2×10^18 次，每一级都对应着体系结构的更替——巨型机、向量机、大规模并行、集群、异构加速、E 级系统；**领域建设**则从 1970 年代的政策报告走到 1980—1990 年代的会议、学会、榜单与国家级计划，最终形成一个有稳定评价体系与人才路径的专门方向。中国超算从 1983 年的亿次机起步，走过引进与自主并行的阶段，在 2010 年代两度登顶，又在 2026 年以全国产系统重返榜首。

继续阅读：

- [什么是 HPC](what-is-hpc.md)：概念、组成与性能指标的基础；
- [现代 HPC](modern-hpc.md)：当前的体系结构与应用格局；
- [Benchmark](../benchmark/intro.md) 与 [HPL](../benchmark/hpl.md)：榜单背后的评测方法；
- [超算平台](../platform/platform-intro.md)：集群、调度与使用的具体内容；
- [HITSZ 超算队](../about/hitsz-hpc.md)：本校的计算设施与训练路径。

---

*本页撰写：AI 助手 `deepseek/deepseek-flash`（2026 年 10 月）；事实与来源见页面内引用。*

## 参考资料

[^1]: [Report of the Panel on Large Scale Computing in Science and Engineering](https://www.osti.gov/biblio/5934266)（美国能源部 OSTI 书目记录，Lax 报告，1982-12-26）
[^2]: [Report of the Task Force on the Future of the NSF Supercomputer Centers Program](https://nsf-gov-resources.nsf.gov/pubs/1996/nsf9646/nsf9646.pdf)（美国国家科学基金会，1995-09-15）
[^3]: [TOP500 25 Year Anniversary](https://www.top500.org/25years/)（TOP500 官方）
[^4]: [SC Conference History](https://supercomputing.org/conference-history/)（SC 会议系列官方）；[ISC High Performance — History](https://isc-hpc.com/history/)（ISC 官方）
[^5]: [ENIAC](https://www.computerhistory.org/revolution/birth-of-the-computer/4/78)（计算机历史博物馆）
[^6]: [Physics History December 1945: The ENIAC Computer Runs Its First, Top-Secret Program](https://www.aps.org/apsnews/2022/11/eniac-first-top-secret-program)（美国物理学会，2022-11-10）
[^7]: [Computing on the mesa](https://web.archive.org/web/20250403210617/https://www.lanl.gov/media/publications/national-security-science/1220-computing-on-the-mesa)（洛斯阿拉莫斯国家实验室，2020-12-01；经 Internet Archive 存档）
[^8]: [First Draft of a Report on the EDVAC](https://archive.org/stream/vnedvac/vnedvac_djvu.txt)（1945-06-30 原文，Internet Archive 全文）；[June 30: "First Draft of Report on EDVAC" Published](https://www.computerhistory.org/tdih/june/30/)（计算机历史博物馆）
[^9]: [Establishing a Pattern: Von Neumann at the IAS](https://www.computerhistory.org/revolution/supercomputers/10/28)（计算机历史博物馆，含 IAS 机器与 UNIVAC LARC 条目）
[^10]: [The Selective Sequence Electronic Calculator](https://www.ibm.com/history/selective-sequence-calculator)（IBM 官方历史页）
[^11]: [The IBM 700 Series](https://www.ibm.com/history/700)（IBM 官方历史页）
[^12]: [IBM Archives: 704 Data Processing System](https://web.archive.org/web/20200102204408/https://www.ibm.com/ibm/history/exhibits/mainframe/mainframe_PP704.html)（IBM Archives，经 Internet Archive 存档）
[^13]: [Fortran](https://www.ibm.com/history/fortran)（IBM 官方历史页）
[^14]: [1959](https://www.cas.cn/zj/ys1/bn/200909/t20090928_2529131.shtml)（中国科学院院史编年史）；[历史沿革](https://www.ict.ac.cn/jssgk/lsyg/)（中国科学院计算技术研究所）
[^15]: [Supercomputers](https://www.computerhistory.org/revolution/supercomputers/10/intro)（计算机历史博物馆展厅导言）
[^16]: [The IBM 7030, aka Stretch](https://www.ibm.com/history/stretch)（IBM 官方历史页）
[^17]: [CDC 6600's Five Year Reign](https://www.computerhistory.org/revolution/supercomputers/10/33)（计算机历史博物馆）
[^18]: [DOE Explains...Exascale Computing](https://www.energy.gov/science/doe-explainsexascale-computing)（美国能源部科学办公室）
[^19]: [September 7: The ILLIAC IV Supercomputer Is Shut Down](https://www.computerhistory.org/tdih/september/7/)（计算机历史博物馆）；[History Timeline](https://siebelschool.illinois.edu/about/history-timeline)（伊利诺伊大学厄巴纳-香槟分校）
[^20]: [The Cray-1 Supercomputer](https://www.computerhistory.org/revolution/supercomputers/10/7) 与 [Cray Research, Inc.](https://www.computerhistory.org/revolution/supercomputers/10/35)（计算机历史博物馆）
[^21]: [Brief History — IPSJ Computer Museum](https://museum.ipsj.or.jp/en/computer/super/history.html)、[SX-1, SX-2](https://museum.ipsj.or.jp/en/computer/super/0008.html)、[FACOM VP-100 Series](https://museum.ipsj.or.jp/en/computer/super/0005.html)、[HITAC S-810](https://museum.ipsj.or.jp/en/computer/super/0007.html)、[FUJITSU VP2000 Series](https://museum.ipsj.or.jp/en/computer/super/0010.html)（日本信息处理学会计算机博物馆）
[^22]: [Seeking Solutions: High-Performance Computing for Science](https://ota.fas.org/reports/9138.pdf)（美国国会技术评估办公室，1991-04）；[Reports Leading to the National High Performance Computing Program](https://science.osti.gov/-/media/ascr/pdf/program-documents/archive/Reports_leading_to_national_high_performance_computing_program.pdf)（美国能源部科学办公室）
[^23]: 同[^1]；另见美国国家医学图书馆档案著录（DOD 与 NSF 资助，Peter D. Lax 任主席）
[^24]: 同[^2]（NSF 超算中心计划的时间线与五个中心的官方名称）
[^25]: [A Legacy of Innovation](https://www.ncsa.illinois.edu/about/history/)（NCSA）；[SDSC opens its doors](https://timeline.sdsc.edu/1985/11/14/sdsc-opens-its-doors-as-one-of-the-nations-first-supercomputer-centers/)（SDSC）；[First PSC Supercomputer Powered on 35 Years Ago](https://www.psc.edu/psc-35-year-anniversary/)（匹兹堡超算中心）
[^26]: [Parallel Computing Works! — Birth of the Hypercube](https://www.netlib.org/utk/lsi/pcwLSI/text/node13.html)（加州理工学院 C3P 项目组，netlib 存档）
[^27]: [The Personal SuperComputer](https://www.computerhistory.org/revolution/supercomputers/10/74) 与 [The Connection Machine](https://www.computerhistory.org/revolution/supercomputers/10/73)（计算机历史博物馆）
[^28]: [The marketplace of high-performance computing](https://www.netlib.org/utk/people/JackDongarra/PAPERS/108_1999_the-marketplace-for-high-performance-computers.pdf)（Strohmaier、Dongarra、Meuer、Simon，Parallel Computing 25 (1999)）
[^29]: [Cray history](https://web.archive.org/web/20260909000305/https://www.hpe.com/us/en/products/compute/hpc/cray.html)（HPE 官方，经 Internet Archive 存档）；[PSC Machine Timeline](https://www.psc.edu/psc-machine-timeline/)（匹兹堡超算中心）
[^30]: [Delivering Insight: The History of the Accelerated Strategic Computing Initiative](https://asc.llnl.gov/sites/asc/files/2020-09/DeliveringInsightASCI_0.pdf)（劳伦斯利弗莫尔国家实验室，2009）
[^31]: [Sandia's ASCI Red, world's first teraflop supercomputer, is decommissioned](https://newsreleases.sandia.gov/sandias-asci-red-worlds-first-teraflop-supercomputer-is-decommissioned/)（桑迪亚国家实验室，2006-06-29）；[ASCI Red: Sandia National Laboratory](https://top500.org/resources/top-systems/asci-red-sandia-national-laboratory/)（TOP500 官方）
[^32]: [The Roots of Beowulf](https://ntrs.nasa.gov/api/citations/20150001285/downloads/20150001285.pdf)（NASA 戈达德太空飞行中心技术报告）；[Beowulf History](https://www.beowulf.org/overview/history.html)（beowulf.org）
[^33]: [Parallel Computing on the Berkeley NOW](http://www.theether.org/papers/jpps.pdf)（伯克利加州大学，D. E. Culler 等）；论文出处见[D. E. Culler 论文列表](https://www2.eecs.berkeley.edu/Pubs/Faculty/culler.html)
[^34]: [PVM List of Frequently Asked Questions](https://www.netlib.org/pvm3/faq_html/node4.html)（netlib，PVM 开发团队）
[^35]: [Background of MPI-1.0](https://www.mpi-forum.org/docs/mpi-3.1/mpi31-report/node8.htm)（MPI 论坛官方标准文档）
[^36]: [DOE-Supported Computing Technologies That Made a Difference: MPI and MPICH](https://science.osti.gov/-/media/ascr/pdf/ascac/pdf/meetings/201709/Rusty_Lusk_ASCAC-201709.pdf)（阿贡国家实验室 Rusty Lusk，ASCAC 报告，2017-09-26）
[^37]: [Specifications](https://www.openmp.org/specifications/)（OpenMP 架构评审委员会官方）
[^38]: 同[^3]
[^39]: [TOP500 List — June 1993](https://top500.org/lists/top500/1993/06/)（TOP500 官方）
[^40]: 同[^4]
[^41]: [ACM Gordon Bell Prize Recognizes Top Accomplishments](https://sc16.supercomputing.org/2016/08/25/acm-gordon-bell-prize-recognizes-top-accomplishments-running-science-apps-hpc/index.html)（SC16 官方新闻稿）；[A look back on 30 years of the Gordon Bell Prize](https://www.davidhbailey.com/dhbpapers/Bell-prize.pdf)（Bailey 等，IJHPCA 31(6)，2017）
[^42]: [HIGH-PERFORMANCE COMPUTING ACT OF 1991](https://www.govinfo.gov/content/pkg/COMPS-1848/pdf/COMPS-1848.pdf)（美国政府出版局）；[HPCC/NITRD Authorizing Legislation](https://www.nitrd.gov/legislation/)（美国 NITRD 国家协调办公室）
[^43]: [The Earth Simulator](https://top500.org/resources/top-systems/the-earth-simulator-earth-simulator-center/)（TOP500 官方）；[TOP500 List — June 2002](https://top500.org/lists/top500/2002/06/)；[Earth Simulator](https://museum.ipsj.or.jp/en/heritage/Earth_Simulator.html)（日本信息处理学会信息处理技术遗产）；[JAMSTEC Earth Simulator](https://www.jamstec.go.jp/es/en/)（日本海洋研究开发机构）
[^44]: [BlueGene/L: Lawrence Livermore National Laboratory](https://top500.org/resources/top-systems/bluegenel-lawrence-livermore-national-laboratory/)（TOP500 官方）；[LLNL, IBM win SC20 Test of Time for Blue Gene/L](https://www.llnl.gov/article/46966/llnl-ibm-win-sc20-test-time-blue-genel)（劳伦斯利弗莫尔国家实验室）
[^45]: [Roadrunner: Los Alamos National Laboratory](https://top500.org/resources/top-systems/roadrunner-los-alamos-national-laboratory/)（TOP500 官方）；[Breaking the petaflop barrier](https://www.ibm.com/history/petaflop-barrier)（IBM 官方历史页）；[Roadrunner Supercomputer Breaks the Petaflop Barrier](https://www.osti.gov/biblio/987139/)（美国能源部 OSTI）
[^46]: [TOP500 Highlights — November 2010](https://top500.org/lists/top500/2010/11/highlights) 与 [Tianhe-1A 系统页](https://www.top500.org/system/176929/)（TOP500 官方）
[^47]: [K computer takes first place in world](https://www.riken.jp/en/news_pubs/news/2011/20110620/index.html)（理化学研究所，2011-06-20）与 [K computer Takes Consecutive No. 1](https://www.riken.jp/en/news_pubs/news/2011/20111114/index.html)（2011-11-14）
[^48]: [Sequoia is ranked the world's fastest supercomputer](https://www.llnl.gov/article/38116/sequoia-ranked-worlds-fastest-supercomputer)（劳伦斯利弗莫尔国家实验室，2012-06-18）
[^49]: [ORNL Supercomputer Named World's Most Powerful](https://www.olcf.ornl.gov/2012/11/12/ornl-supercomputer-named-worlds-most-powerful/)（橡树岭领导计算设施，2012-11-12）
[^50]: [China's Tianhe-2 Supercomputer Takes No. 1 Ranking on 41st TOP500 List](https://www.top500.org/news/chinas-tianhe-2-supercomputer-takes-no-1-ranking-on-41st-top500-list/)（TOP500 官方新闻稿，2013-06-17）；[Tianhe-2 系统页](https://top500.org/resources/top-systems/tianhe-2-milkyway-2-national-university-of-defense/)（TOP500 官方）
[^51]: [China Tops Supercomputer Rankings with New 93-Petaflop Machine](https://www.top500.org/news/china-tops-supercomputer-rankings-with-new-93-petaflop-machine/)（TOP500 官方新闻稿，2016-06-20）；[Sunway TaihuLight 系统页](https://top500.org/system/178764/)（TOP500 官方）
[^52]: [ORNL's Summit Supercomputer Named World's Fastest](https://www.ornl.gov/news/ornls-summit-supercomputer-named-worlds-fastest)（橡树岭国家实验室，2018-06-25）；[Summit Supercomputer Ranked Fastest Computer in the World](https://www.energy.gov/articles/summit-supercomputer-ranked-fastest-computer-world)（美国能源部）
[^53]: [Japan Captures TOP500 Crown with Arm-Powered Supercomputer](https://www.top500.org/news/japan-captures-top500-crown-arm-powered-supercomputer/)（TOP500 官方新闻稿，2020-06-22）；[Fujitsu and RIKEN Take First Place Worldwide](https://www.fujitsu.com/global/about/resources/news/press-releases/2020/0622-01.html)（富士通官方新闻稿）
[^54]: [IBM Triples Performance of World's Fastest, Most Energy-Efficient Supercomputer](https://www.alcf.anl.gov/news/ibm-triples-performance-world)（IBM 新闻稿，阿贡领导计算设施转载，2007-06-26）
[^55]: [CUDA Programming Guide — Introduction](https://docs.nvidia.com/cuda/cuda-programming-guide/01-introduction/introduction.html)（NVIDIA 官方文档）
[^56]: [「银河-1」亿次计算机](https://www.ccf.org.cn/Computing_history/Full_List/2017/First_class/2018-09-12/652326.shtml)（中国计算机学会「计算机历史记忆」认定，2018-09-12）
[^57]: [历史上的今天，「银河－I」计算机横空出世！](https://web.archive.org/web/20260811113811/https://www.nudt.edu.cn/zjkd/kdgs/f510ef9ef03c49ebac9350a302c80290.htm)（国防科技大学，2019-12-06；经 Internet Archive 存档）；[纪念慈云桂诞辰](https://web.archive.org/web/20250523102015/https://www.nudt.edu.cn/rwfc/e111546b4c3444a2bed76ce9cb7b2625.htm)（国防科技大学，2025-04-05）
[^58]: [一生就是做了那么几台机器——访计算机专家、中国科学院院士周兴铭](https://www.ccf.org.cn/Computing_history/Updates/2020-12-15/720614.shtml)（中国计算机学会，2020-12-15）
[^59]: [百年瞬间丨「银河-Ⅲ」巨型计算机研制成功](https://www.12371.cn/2021/06/19/VIDE1624068600421689.shtml)（共产党员网，2021-06-19）
[^60]: [中国超级计算发展态势](https://epaper.gmw.cn/gmrb/html/2012-06/06/nw.D110000gmrb_20120606_1-04.htm)（《光明日报》，2012-06-06）
[^61]: [中国超算事业的第一缕「曙光」](https://web.archive.org/web/20250908045822/https://www.cas.cn/zt/kjzt/kjzlzqzl/kjzlzq/202409/t20240909_5031034.shtml)（中国科学院，原载《中国科学报》2024-09-09；经 Internet Archive 存档）；[「863」，中国高技术奋起发展的标志](https://epaper.gmw.cn/gmrb/html/2021-03/29/nw.D110000gmrb_20210329_1-05.htm)（《光明日报》，2021-03-29）
[^62]: [高性能计算机研究中心](https://ict.cas.cn/jssgk/zzjg/kyxt/gxnjsyjzx/)与[历史沿革](https://www.ict.ac.cn/jssgk/lsyg/)（中国科学院计算技术研究所）；[发展历程](https://www.ssc.net.cn/about-history.html)（上海超级计算中心）
[^63]: [2002年度国家最高科学技术奖获奖人——金怡濂](https://web.archive.org/web/20250413082234/https://www.nosta.gov.cn/pc/zh/gjkjjl/hjr5/59.shtml)（国家科学技术奖励工作办公室；经 Internet Archive 存档）
[^64]: [我国先后建成六家国家级超算中心](https://www.qstheory.cn/science/2019-07/08/c_1124722159.htm)（求是网，原载《中国科学报》，2019-07-08）
[^65]: [发展历程](https://www.nsccsz.cn/nsccsz2024/fzlc2024/fzlc2024.shtml)（国家超级计算深圳中心）
[^66]: [About](https://www.nsccwx.cn/About.html)（国家超级计算无锡中心，含戈登·贝尔奖记录）
[^67]: [瞄准超算皇冠：神威 E 级超算原型机正式启用](https://web.archive.org/web/20200808170930/http://www.xinhuanet.com/politics/2018-08/05/c_129926915.htm)（新华社，2018-08-05；经 Internet Archive 存档）
[^68]: [国产百亿亿次超算技术实现新突破 「天河三号」E 级原型机完成研制部署](https://web.archive.org/web/20200807035058/http://www.xinhuanet.com/politics/2018-07/26/c_1123181952.htm)（新华社，2018-07-26；经 Internet Archive 存档）
[^69]: [TOP500 List — June 2026](https://www.top500.org/lists/top500/2026/06/) 与 [LineShine Debuts at No. 1 as the TOP500 Enters a New Global Exascale Era](https://www.top500.org/news/lineshine-debuts-no-1-top500-enters-new-global-exascale-era/)（TOP500 官方，2026-06-23）
[^70]: [重磅登顶！「灵晟」问鼎全球超算 TOP500](https://www.nsccsz.cn/nsccsz2024/zxdt2024/202606/19c3a18b-f9f5-4ba7-a557-9eb890f73615.shtml)（国家超级计算深圳中心，2026-06-23）
[^71]: [ORNL's Frontier First to Break the Exaflop Ceiling](https://www.top500.org/news/ornls-frontier-first-to-break-the-exaflop-ceiling/)（TOP500 官方新闻稿，2022-05-30）；[Frontier](https://www.olcf.ornl.gov/olcf-resources/compute-systems/frontier/)（橡树岭领导计算设施）
[^72]: [Aurora](https://www.alcf.anl.gov/aurora)（阿贡领导计算设施）；[Frontier keeps top spot, but Aurora officially becomes the second exascale machine](https://top500.org/news/frontier-keeps-top-spot-aurora-officially-becomes-second-exascale-machine/)（TOP500 官方新闻稿，2024-05-13）
[^73]: [El Capitan achieves top spot, Frontier and Aurora follow behind](https://top500.org/news/el-capitan-achieves-top-spot-frontier-and-aurora-follow-behind/)（TOP500 官方新闻稿，2024-11-18）；[LLNL's El Capitan verified as world's fastest supercomputer](https://www.llnl.gov/article/52061/lawrence-livermore-national-laboratorys-el-capitan-verified-worlds-fastest-supercomputer)（劳伦斯利弗莫尔国家实验室）
[^74]: [El Capitan Retains #1 as JUPITER Becomes Europe's First Exascale System in the 66th TOP500 List](https://top500.org/news/el-capitan-retains-1-as-jupiter-becomes-europes-first-exascale-system-in-the-66th-top500-list/)（TOP500 官方新闻稿，2025-11-17）
[^75]: [Green500 — June 2026](https://top500.org/lists/green500/green500-june-2026/)（TOP500/Green500 官方）；[Energy-Efficient Supercomputing Comes of Age with TOP500-Green500 Merge](https://top500.org/news/energy-efficient-supercomputing-comes-of-age-with-top500-green500-merge/)（TOP500 官方，2016-06-09）
[^76]: [Artificial Intelligence for Science](https://science.osti.gov/Initiatives/AI)（美国能源部科学办公室）
[^77]: [Apptainer](https://apptainer.org/)（Apptainer 项目官方站点）
[^78]: [ORNL Deploys New IQM Quantum Computer](https://www.olcf.ornl.gov/2026/07/08/ornl-deploys-new-iqm-quantum-computer/)（橡树岭领导计算设施，2026-07-08）
[^79]: [New ACM Special Interest Group on High Performance Computing Debuts at SC11](https://web.archive.org/web/20220629191249/https://www.acm.org/articles/membernet/2011/membernet-11222011)（ACM MemberNet，2011-11-22；经 Internet Archive 存档）
[^80]: [IEEE-CS TCHPC Newsletter 创刊号](http://tc.computer.org/tchpc/wp-content/uploads/sites/3/2017/10/TCHPC-Newsletter_October2017_final.pdf)（IEEE 计算机学会 HPC 技术组织，2017-10）
[^81]: [First SIAM Conference on Computational Science and Engineering](https://web.archive.org/web/20000815064530if_/http://www.siam.org/meetings/cse00/)（SIAM，2000；经 Internet Archive 存档）
[^82]: [Journal of Parallel and Distributed Computing 卷次页](https://www.sciencedirect.com/journal/journal-of-parallel-and-distributed-computing/vol/1/issue/2)（Elsevier）；[International Journal of High Performance Computing Applications](https://web.archive.org/web/20200421190724/https://us.sagepub.com/en-us/nam/journal/international-journal-high-performance-computing-applications)（SAGE，经 Internet Archive 存档）
[^83]: [NSF Creates TeraGrid](https://www.ncsa.illinois.edu/2001/08/09/nsf-creates-teragrid/)（NCSA，2001-08-09）；[XSEDE 过渡说明](https://www.xsede.org)（XSEDE 官方）；[Advancing to ACCESS](https://access-ci.org/advancing-to-access/)（ACCESS 官方，2022-09-01）；[PACI 项目页](https://web.archive.org/web/20250302161149/https://www.nsf.gov/funding/opportunities/paci-advanced-computational-infrastructure/5215/5427)（NSF，经 Internet Archive 存档）
[^84]: [About INCITE](https://science.osti.gov/ascr/Facilities/Accessing-ASCR-Facilities/INCITE/About-incite)（美国能源部科学办公室）
[^85]: [PRACE FAQs](https://prace-ri.eu/prace-archive/about/faqs/)（PRACE 官方）；[Discover EuroHPC JU](https://www.eurohpc-ju.europa.eu/about/discover-eurohpc-ju_en)（EuroHPC 联合执行体官方）
[^86]: [FY 1993 Blue Book: Grand Challenges 1993](https://catalog.data.gov/dataset/fy-1993-blue-book-grand-challenges-1993-high-performance-computing-and-communications)（美国 NITRD，报告 PDF 见 data.gov 条目）
[^87]: [Federal Plan for High-End Computing](https://www.nitrd.gov/pubs/2004_hecrtf/20040510_hecrtf.pdf)（美国 NITRD 高端计算振兴工作组，2004 年 5 月）
[^88]: [Computational Science: Ensuring America's Competitiveness](https://www.nitrd.gov/pubs/pitac/pitac_report_computational-science_2005.pdf)（美国总统信息技术咨询委员会，2005 年 6 月）
[^89]: [The Landscape of Parallel Computing Research: A View from Berkeley](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2006/EECS-2006-183.pdf)（伯克利加州大学技术报告 UCB/EECS-2006-183，2006-12-18）
[^90]: [The Opportunities and Challenges of Exascale Computing](https://science.osti.gov/-/media/ascr/pdf/reports/Exascale_subcommittee_report.pdf)（美国能源部先进科学计算咨询委员会分委员会总结报告，2010 年秋）
[^91]: [15 U.S.C. §5503 Definitions](https://www.govinfo.gov/content/pkg/USCODE-2023-title15/html/USCODE-2023-title15-chap81-sec5503.htm)（美国法典 2023 年版）；[HEC Education Initiative Position](https://www.nitrd.gov/nitrdgroups/images/4/4f/HEC_Education_Initiative_Position_%28March_2013%29.pdf)（美国 NITRD HEC-IWG，2013-03）
[^92]: [Masters programmes in High Performance Computing](https://www.epcc.ed.ac.uk/education-training/masters-programmes-high-performance-computing-hpc-and-hpc-data-science)（爱丁堡大学 EPCC）
[^93]: [HPC Carpentry](https://www.hpc-carpentry.org/)（HPC Carpentry 官方站点）
[^94]: [Student Cluster Competition History](https://sc26.supercomputing.org/students/cluster-competition-history/)（SC 会议系列官方）；[ASC 2012 官方历史页](https://www.asc-events.net/StudentChallenge/History/2012/index.html)（ASC 官方）

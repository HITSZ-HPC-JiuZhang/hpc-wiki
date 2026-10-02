# Linux 发行版选择

集群服务器上的科学计算软件基本都以 Linux 为第一支持平台：MPI 实现、作业调度器、GPU/NPU 驱动、并行文件系统客户端、容器方案与集群管理工具都是如此，因此本页只讨论 Linux 发行版。发行版一经部署，驱动、调度器、工具链与软件环境都会围绕它展开，更换成本很高，值得在动手前想清楚。

## 选择判据

1. **稳定与可复现**：发行版需要提供固定版本的软件仓库、足够长的支持周期，以及把系统状态冻结下来的手段（软件包快照、版本锁定、整机快照）。滚动发行的仓库只保留当前版本，默认状态下无法把系统还原到过去某一天，不适合承担需要复现结果的集群节点。
2. **兼容与生态**：至少需要 systemd 与成熟的 .rpm/.deb 生态；更关键的是厂商支持矩阵，GPU/NPU 驱动、编译器与商业软件通常只认证少数发行版（见下文清单）。还要注意 ABI 的方向性：在旧系统上构建的二进制可以在新系统上运行，反之不行，因此构建基线宜选择支持周期长、基础库保守的发行版。
3. **性能与调优**：同硬件、同内核、同工具链下，发行版之间的裸机性能差异很小；实际差异来自默认启用的服务、默认调优参数（CPU 频率调节策略、透明大页、I/O 调度器等）、内核版本与驱动完备性。HPC 工具链通常自行安装，进一步缩小了差异。RHEL 系自带 tuned 调优框架，提供包括 hpc-compute 在内的多个档位，计算节点默认使用 throughput-performance[^1]；其他发行版也可以单独安装 tuned。与功耗相关的设置见[功耗管理](power-management/intro.md)。
4. **支持周期与合规**：集群通常按年维护，发行版的安全更新承诺年限直接决定维护成本；国产化项目还要按信创要求选择厂商认证的系统。

## 候选发行版

| 系列 | 代表发行版 | 支持周期（官方口径） |
| --- | --- | --- |
| Red Hat 系 | RHEL、Rocky Linux、AlmaLinux、CentOS Stream | 每个主版本 10 年；RHEL 10 支持至 2035 年 5 月[^2] |
| Debian 系 | Debian stable、Ubuntu LTS | Debian 为 3 年完整支持加 2 年 LTS[^3]；Ubuntu LTS 标准 5 年，可延长至 15 年[^4] |
| SUSE 系 | SLES、openSUSE Leap | SLES 15 常规支持至 2031 年 7 月，长期服务至 2037 年[^5] |
| 国产发行版 | openEuler、Anolis OS、银河麒麟、统信 UOS | 按厂商与信创要求选用，定位见下文[^6] |

### Red Hat 系

RHEL 8、9、10 每个主版本提供十年生命周期，分别支持到 2029、2032、2035 年的 5 月[^2]。Rocky Linux 与 AlmaLinux 是社区重建版本：前者宣称与 RHEL 100% 兼容，后者自 2023 年 7 月起把目标定为与 RHEL 保持 ABI 兼容，两者的支持时间都与 RHEL 对齐[^7]。CentOS Stream 位于 RHEL 上游，生命周期约五年，适合跟踪开发；CentOS Linux 7 与 8 已分别于 2024 年 6 月 30 日与 2021 年 12 月 31 日停止维护，不要再作为新集群的起点[^8]。

### Debian 系

Debian stable 是官方定位的生产发布版，生命周期五年（三年完整支持加两年 LTS）；当前版本 Debian 13 的常规支持至 2028 年 8 月，LTS 至 2030 年 6 月[^3]。Ubuntu LTS 每两年发布一次，标准安全维护五年，配合 Ubuntu Pro 可延长至十年，加购 Legacy add-on 总计十五年，当前 LTS 为 26.04 与 24.04[^4]。需要较新硬件支持时可以启用 HWE 内核，官方标注为开发模式的 edge 变体不要用于生产[^9]。另外，Ubuntu 默认开启自动安全更新，集群部署时通常需要评估并调整这一行为[^10]。

### SUSE 系

SLES 常见于欧洲的高性能计算环境，SLES 15 的常规支持至 2031 年 7 月、长期服务（LTSS）至 2037 年 7 月，SLES 16 的常规支持至 2035 年 11 月[^5]。openSUSE Leap 与 SLES 共享二进制核心，从 Leap 16 起每个小版本提供 24 个月维护，生命周期与 SLE 对齐[^11]。

### 国产发行版

openEuler、Anolis OS、银河麒麟与统信 UOS 主要面向国产平台与信创场景。openEuler 由开放原子开源基金会运营，24.03 LTS 计划支持到 2027 年 3 月[^6]；Anolis OS 宣称 100% 兼容 CentOS 生态，Anolis OS 8 的支持到 2031 年[^12]；银河麒麟与统信 UOS 的服务器版本都提供多架构支持，覆盖 x86_64、AArch64 与 LoongArch 等[^13][^14]。

在鲲鹏、昇腾平台上，按厂商支持清单选择可以减少驱动与工具链的摩擦：昇腾 CANN 的安装指南按产品型号列出支持的系统，并把发行版归为 Ubuntu 系、openEuler 系与 SLES 系三类安装参照[^15]；openEuler 24.03 LTS 与 RHEL 10 一起出现在 OpenHPC 4.x 的构建目标中[^16]。需要注意：这些系统的生态成熟度与软件包丰富度同 RHEL 系、Debian 系仍有差距，建议作为特殊场景下的必要选择，不作为通用集群的默认方案。

## 不建议用于集群的选择

- **滚动发行版**（Arch Linux、openSUSE Tumbleweed 等）：默认无法复现历史状态，更适合个人开发机。
- **生命周期过短的发行版**：Fedora 每 6 个月发布一次、每个版本维护约 13 个月，官方也建议需要长周期支持的用户改用 CentOS Stream 或 RHEL[^17]。
- **以桌面为主的发行版**：默认附带大量与计算无关的组件与自动更新行为。
- **非 systemd 的轻量发行版**（Alpine、Void 等）：体积小，但商业 HPC 软件与驱动对它们的兼容成本很高。
- **已经停止维护的发行版**：CentOS Linux 7 与 8 已属于这一类[^8]。

## 厂商与工具链支持矩阵

| 组件 | 官方支持范围（节选） |
| --- | --- |
| NVIDIA CUDA 与驱动 | 覆盖主流 RHEL 系、Debian 系与 SUSE 系发行版；驱动程序的支持列表中，国产发行版只列入银河麒麟；两个指南都声明支持延续到各发行版自身的生命周期结束[^18] |
| AMD ROCm | Ubuntu、RHEL、SLES、Debian、Rocky Linux 与 Oracle Linux，不含国产发行版[^19] |
| 华为昇腾 CANN | 按产品型号列出，覆盖 openEuler、CentOS、麒麟、统信 UOS 与 Ubuntu 等[^15] |
| Intel oneAPI | CPU 侧覆盖 RHEL 8/9/10、Ubuntu 22.04 与 24.04、SLES 15 SP4–SP7、Debian 11/12、Rocky Linux 9 等；GPU 侧范围更窄[^20] |
| OpenHPC | 2.x 对应 RHEL 8；3.x 对应 RHEL 9、openSUSE Leap 15.5 与 openEuler 22.03 LTS；4.x 对应 RHEL 10 与 openEuler 24.03 LTS[^16] |
| Slurm | Debian 11–13、RHEL 8/9/10 及其衍生版、SLES 12/15、Ubuntu 20.04–24.04；官方明确不推荐发行版仓库里的非官方包，生产部署推荐自行构建 RPM 或 DEB[^21] |

## 场景对照

| 场景 | 建议 |
| --- | --- |
| 生产集群（CPU/GPU 节点） | RHEL 系或 SLES，选择仍在受支持期内的主版本 |
| 需要较新硬件支持 | Ubuntu LTS（启用 HWE 内核）或 Debian stable |
| 鲲鹏/昇腾平台、信创项目 | 按厂商支持清单选用国产发行版，必要时才用 |
| 竞赛现场 | 选队伍最熟悉的发行版，赛前固化整机快照与自动化部署脚本 |
| 个人开发机 | 不受本页约束，用容器或 Spack 隔离软件环境即可 |

## 把可复现落到操作上

- **软件包快照**：Debian 提供 snapshot.debian.org，可按日期与版本号取回历史软件包，并可作为普通 apt 源使用[^22]；Ubuntu 提供 snapshot.ubuntu.com，24.04 及以后版本的 apt 支持用 `--snapshot` 参数按指定时刻安装软件包[^23]。
- **版本锁定**：RHEL 系用 `dnf versionlock` 把软件包锁定在指定版本[^24]；Debian/Ubuntu 用 `apt-mark hold` 阻止软件包被自动安装、升级或移除[^25]。
- **环境隔离**：Spack 用“清单加锁文件”的方式固定软件的具体规格，从锁文件重建的环境在兼容机器上初始规格一致[^26]；HPC 场景常用 Apptainer 容器打包软件，单文件格式便于携带与归档[^27]。更多内容见[环境管理](environment.md)。
- **整机快照与自动化部署**：预置打包好的根文件系统与部署脚本，比现场逐台配置可靠。
- **变更记录**：系统级改动统一记录便于回溯，做法见[操作历史记录](operation-log.md)；内核与文件系统等配置项见[系统配置](system-config.md)。

---

*本页撰写：AI 助手 `deepseek/deepseek-flash`（2026 年 10 月）；事实与图片出处见页面内引用。*

## 参考资料

[^1]: [Getting started with TuneD](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/monitoring_and_managing_system_status_and_performance/getting-started-with-tuned_monitoring-and-managing-system-status-and-performance)（Red Hat Enterprise Linux 9 官方文档）
[^2]: [Red Hat Enterprise Linux Life Cycle](https://access.redhat.com/support/policy/updates/errata)（Red Hat 官方生命周期政策页）
[^3]: [Debian Releases](https://www.debian.org/releases/) 与 [Debian LTS](https://wiki.debian.org/LTS)（Debian 官方网站与官方 Wiki）
[^4]: [Ubuntu release cycle](https://ubuntu.com/about/release-cycle) 与 [Ubuntu Expanded Security Maintenance](https://ubuntu.com/security/esm)（Ubuntu 官方页面）
[^5]: [SUSE Product Support Lifecycle](https://www.suse.com/lifecycle/)（SUSE 官方生命周期页）
[^6]: [openEuler 下载中心](https://www.openeuler.org/en/download/)（openEuler 官方网站）
[^7]: [Rocky Linux](https://rockylinux.org/)、[Rocky Linux 发布与支持说明](https://docs.rockylinux.org/releases/)、[AlmaLinux FAQ](https://wiki.almalinux.org/FAQ.html) 与 [AlmaLinux Release Notes](https://wiki.almalinux.org/release-notes/)（各发行版官方页面）
[^8]: [CentOS Stream](https://www.centos.org/centos-stream/)、[CentOS Linux EOL](https://www.centos.org/centos-linux-eol/) 与 [End dates are coming for CentOS Stream 8 and CentOS Linux 7](https://blog.centos.org/2023/04/end-dates-are-coming-for-centos-stream-8-and-centos-linux-7/)（CentOS 官方页面与官方博客）
[^9]: [Ubuntu kernel lifecycle](https://ubuntu.com/kernel/lifecycle) 与 [HWE kernels](https://documentation.ubuntu.com/kteam-docs/public/reference/hwe-kernels.html)（Ubuntu 官方文档）
[^10]: [How to manage automatic updates](https://documentation.ubuntu.com/server/how-to/software/automatic-updates/)（Ubuntu Server 官方文档）
[^11]: [openSUSE Lifetime](https://en.opensuse.org/Lifetime) 与 [openSUSE Leap 16.0](https://get.opensuse.org/leap/16.0/)（openSUSE 官方 Wiki 与官方站点）
[^12]: [Anolis OS](https://openanolis.cn/anolisos)（龙蜥社区官方站点）
[^13]: [银河麒麟高级服务器操作系统 V11](https://www.kylinos.cn/productPc/server/serverMainV11/)（麒麟软件官方产品页）
[^14]: [统信服务器操作系统](https://www.uniontech.com/m/os-serverCloud.html)（统信软件官方产品页）
[^15]: [CANN 软件安装指南](https://www.hiascend.com/doc_center/source/zh/CANNCommunityEdition/700alpha003/softwareinstall/instg/CANN%207.0.0alpha003%20%E8%BD%AF%E4%BB%B6%E5%AE%89%E8%A3%85%E6%8C%87%E5%8D%97%2001.pdf)（华为昇腾官方文档）
[^16]: [OpenHPC Downloads](https://openhpc.community/downloads/)（OpenHPC 官方页面）
[^17]: [Fedora Linux Release Life Cycle](https://docs.fedoraproject.org/en-US/releases/lifecycle/)（Fedora 官方文档）
[^18]: [CUDA Installation Guide for Linux](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html) 与 [NVIDIA Driver Installation Guide](https://docs.nvidia.com/datacenter/tesla/driver-installation-guide/introduction.html)（NVIDIA 官方文档）
[^19]: [ROCm System Requirements](https://rocm.docs.amd.com/projects/install-on-linux/en/latest/reference/system-requirements.html)（AMD 官方文档）
[^20]: [oneAPI System Requirements](https://www.intel.com/content/www/us/en/developer/articles/system-requirements/oneapi-base-toolkit/2025.html)（Intel 官方文档）
[^21]: [Slurm Platforms](https://slurm.schedmd.com/platforms.html) 与 [Slurm Quick Start Administrator Guide](https://slurm.schedmd.com/quickstart_admin.html)（SchedMD 官方文档）
[^22]: [snapshot.debian.org](https://snapshot.debian.org/)（Debian 官方服务）
[^23]: [Ubuntu snapshot service](https://snapshot.ubuntu.com/)（Ubuntu 官方服务）
[^24]: [How to lock package versions with versionlock](https://access.redhat.com/solutions/98873)（Red Hat 官方知识库）
[^25]: [apt-mark(8)](https://manpages.debian.org/trixie/apt/apt-mark.8.en.html)（Debian 官方手册页）
[^26]: [Spack Environments](https://spack.readthedocs.io/en/latest/environments.html)（Spack 官方文档）
[^27]: [Apptainer 用户文档](https://apptainer.org/docs/user/latest/introduction.html)（Apptainer 官方文档）

# HITSZ HPC Wiki

本仓库是面向哈尔滨工业大学（深圳）（HITSZ）超算队教学与训练场景维护的 HPC 知识库。内容覆盖高性能计算基础、并行编程、GPU 编程、性能分析、Benchmark、科学计算与机器学习系统等主题。

HITSZ 的超算人才培养与竞赛活动由实验与创新教育中心（ECEI）组织。学校维护 CPU 集群和 CPU–GPU 异构集群，并通过课程、专项训练和技术社群支持学生参与 HPC 实践。团队在 ASC2026 获一等奖，并在 2026 年华为 ICT 大赛获三等奖。更多信息见[哈尔滨工业大学（深圳）超算队介绍](docs/zh/docs/about/hitsz-hpc.md)。

## 上游项目与署名

本项目基于 [lcpu-club/hpc-wiki](https://github.com/lcpu-club/hpc-wiki) 进行适配。上游 **HPC Wiki** 源于社区，并由北京大学学生 Linux 俱乐部长期运营和维护。本仓库保留上游项目、原作者和贡献者的署名及贡献历史；各文档中已有的来源说明保持不变。

## 本地构建

项目使用 [MkDocs](https://www.mkdocs.org/) 与 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 构建。

```shell
git clone https://github.com/HITSZ-HPC-JiuZhang/hpc-wiki.git
cd hpc-wiki

# 构建静态站点到 site/
uvx --with-requirements requirements.txt mkdocs build \
  -f docs/zh/mkdocs.yml -d "$(pwd)/site"

# 在本地启动预览
uvx --with-requirements requirements.txt mkdocs serve \
  -f docs/zh/mkdocs.yml
```

在阅读 Wiki 之前，建议：

- 学习[提问的智慧](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way)；
- 善用搜索工具；
- 至少掌握一门编程语言，例如 Python；
- 通过实际实验巩固概念；
- 保持对技术的好奇与长期投入。

## 特别鸣谢

本项目受 [CTF Wiki](https://ctf-wiki.org/) 和 [OI Wiki](https://oi-wiki.org/) 的启发，同时在编写过程中参考了很多资料，特别鸣谢以下项目：

- 上海科技大学 GeekPie 社区的 [GeekPie_HPC Wiki](https://hpc.geekpie.club/wiki/index.html)
- 东南大学超算团队的 [asc-wiki](https://asc-wiki.com)
- 北京大学学生 Linux 俱乐部的 [HPC from Scratch 项目](https://wiki.lcpu.dev/zh/hpc/from-scratch/arrange)

## Copyleft

<a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />本作品采用<a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/">知识共享署名—非商业性使用—相同方式共享 4.0 国际许可协议</a>进行许可。完整条款见仓库根目录的 [`LICENSE`](LICENSE)。
**简体中文** · [English](README.en.md)

# 菠萝狗 5 · 前行步态训练资料

这里整理的是 **站立与向前小跑** 的配套训练方法。官网示例仍名为“菠萝狗 第四代 12自由度”，仓库采用“菠萝狗 5”作为展示名称。

## 下载资料

| 文件 | 用途 |
| :---: | :---: |
| [py-apple-dog-forward.simready](forward-trot/py-apple-dog-forward.simready) | 从 SimReady 官网下载的完整示例，包含机器人模型、关节映射、奖励与训练设置 |
| [mjlab-training-project.zip](forward-trot/mjlab-training-project.zip) | 与 Sim2Real 前行策略来源配套的原始 MJLab 训练工程 |
| [training-settings.json](forward-trot/training-settings.json) | 官网工程中的训练设置，便于查阅与对照 |
| [effective-training.json](forward-trot/effective-training.json) | 前行策略来源工程保存的实际训练参数 |
| [source.json](forward-trot/source.json) | 下载入口、来源版本、文件校验和及对应关系 |

## 按这个顺序开始

1. 打开 [StackForce SimReady](https://sim.stackforce.cc/)，点击 **打开项目 / 文件**，载入上面的 `.simready`；也可以从官网示例列表加载“菠萝狗 第四代 12自由度”。
2. 在 **策略映射** 中查看 12 个关节、初始姿态、观测和动作配置。首次训练先保留这些设置。原模型坐标中，前行指令为 **X = -0.1 m/s**，不要直接改成正值。
3. 进入 **训练**，安装并启动网页提供的本地运行器，连接后先做小规模验证。CPU 或显存有限时，先减少并行环境与训练轮数，确认流程可运行。
4. 训练任务混合零速站立与前行。观察软件内置曲线，并定期回放保存的检查点，分别检查站立、前行和启停效果。
5. 保存工程、参数与模型。原配方从随机初始化开始训练，不把本仓库的已训练 ONNX 当作从零训练的初始权重。对比检查点后，再进行仿真和实机适配。

## 原配方中的关键设置

| 项目 | 设置 |
| :---: | :---: |
| 训练框架 | MJLab / PPO |
| 环境比例 | 50% 零速站立，50% 前行；Y 与转向指令为 0 |
| 前行指令 | 模型坐标 X = -0.1 m/s |
| 仿真与控制 | 仿真步长 0.001 s，20 步更新一次控制（50 Hz） |
| PPO 学习率 | 固定 0.00015 |
| 原始训练规模 | 4096 个并行环境，841 轮，每 20 轮保存，seed = 7 |
| Actor / Critic | 隐藏层 [128, 64] / [256, 128] |

原始规模用于记录配方；实际可按算力缩小。小规模试跑用于确认流程，训练效果要结合回放判断。

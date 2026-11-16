**简体中文** · [English](COMPATIBILITY.en.md)

# 机械与策略对应关系

菠萝狗 5 的配套网站示例沿用“菠萝狗 第四代 12自由度”或 `pydog-gen4-*` 标识。选择工程时，请按网站中的示例名称查找，并使用与工程匹配的模型、策略和关节配置。

| 项目 | 使用说明 |
| :---: | :---: |
| 机械结构 | 12 自由度结构与带轮小腿；按[打印清单](print-list.csv)和[打印说明](PRINTING.md)装配 |
| SimReady | 在 [SimReady](https://sim.stackforce.cc/) 中打开[前行训练工程](../training/README.md)，配置训练并回放结果 |
| Sim2Sim | 在 [Sim2Sim](https://sim2sim.stackforce.cc/) 中选择对应的菠萝狗示例，检查模型、策略与动作 |
| Sim2Real | 在 [Sim2Real](https://sim2real.stackforce.cc/) 中配置设备、关节映射与零位，再部署匹配的策略 |
| 固件和板卡 | ESP32-S3 Zero + Connector HAT RevB；[点击进入硬件开源查看](../hardware/README.md)，按[接线说明](WIRING.md)配置 |
| 站立与向前小跑 | `pydog-gen4-stand-forward`；[策略与部署工程](../policies/forward-trot/) |
| 全向小跑 | `pydog-gen4-trot-v132-100`；[策略与部署工程](../policies/omnidirectional-trot/) |
| 带轮结构 | 轮子的锁止或被动转动状态应与所用仿真模型一致 |

部署前应对应好关节顺序、转动方向、零位、限位、舵机规格、质量与重心，以及策略的观测维度、历史帧数、控制周期和动作缩放。`pydog12` 与 Gen4 示例使用不同的模型与配置，不能直接互换。

五种策略及各自的适配信息见 [policies/](../policies/README.md)，各目录的 `source.json` 保留原始示例的验证状态。配套[训练方法](../training/README.md)针对站立与向前小跑；其他动作应使用各自匹配的训练配置。部署到自己的机器人时，从单关节、单腿和站立开始验证，再逐步运行运动策略。

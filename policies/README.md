**简体中文** · [English](README.en.md)

# 菠萝狗 5 · 开源策略与训练好的策略文件

这里收录 [StackForce Sim2Real](https://sim2real.stackforce.cc/) 当前开放的 5 个菠萝狗示例，下载于 **2026-11-15**。“开源策略”和“训练好的策略文件”均指向本目录。

| 步态或动作 | ONNX 文件 | 完整工程 | 输入 / 输出维度 |
| :---: | :---: | :---: | :---: |
| 向前小跑 | [policy.onnx](forward-trot/policy.onnx) | [project.sim](forward-trot/project.sim) | 585 / 120 |
| 全向小跑 | [policy.onnx](omnidirectional-trot/policy.onnx) | [project.sim](omnidirectional-trot/project.sim) | 585 / 120 |
| 慢行 | [policy.onnx](slow-walk/policy.onnx) | [project.sim](slow-walk/project.sim) | 625 / 124 |
| 跳跃（Bound） | [policy.onnx](bound/policy.onnx) | [project.sim](bound/project.sim) | 860 / 159 |
| 翻倒自起立 | [policy.onnx](self-righting/policy.onnx) | [project.sim](self-righting/project.sim) | 605 / 127 |

## 怎么使用

1. 下载对应的 `project.sim`，在 Sim2Sim 或 Sim2Real 中选择 **打开工程 / 选择 .sim**。完整工程包含模型、策略、观测与动作配置，比单独导入 ONNX 更适合作为起点。
2. 先在仿真中检查动作，再在实物部署中完成自己的设备映射、方向与零位标定。下载包不包含你的实机标定结果。
3. 单独使用 ONNX 时，配合相同目录的 `sim2sim.profile.json`；其中保存了控制周期、观测、关节与控制器状态的约定。

机器人只有 **12 个主动关节**。ONNX 的额外输出用于控制器状态反馈，不能当作额外关节，不能把所有输出直接发送给舵机。自起立的主策略在原始工程中名为 `terminal-hold.onnx`，这里另存为 `policy.onnx` 便于统一下载；完整 `.sim` 保持原始结构。

[返回首页](../README.md)

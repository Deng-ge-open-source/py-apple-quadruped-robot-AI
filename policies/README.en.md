[简体中文](README.md) · **English**

# Py-Apple Dog 5 · Open and pretrained policies

These five Py-Apple Dog examples were downloaded from [StackForce Sim2Real](https://sim2real.stackforce.cc/) on **2026-11-15**. Both “open policies” and “pretrained policy files” on the homepage point to this directory.

| Gait or action | ONNX file | Complete project | Input / output dimensions |
| :---: | :---: | :---: | :---: |
| Forward trot | [policy.onnx](forward-trot/policy.onnx) | [project.sim](forward-trot/project.sim) | 585 / 120 |
| Omnidirectional trot | [policy.onnx](omnidirectional-trot/policy.onnx) | [project.sim](omnidirectional-trot/project.sim) | 585 / 120 |
| Slow walk | [policy.onnx](slow-walk/policy.onnx) | [project.sim](slow-walk/project.sim) | 625 / 124 |
| Bound | [policy.onnx](bound/policy.onnx) | [project.sim](bound/project.sim) | 860 / 159 |
| Self-righting | [policy.onnx](self-righting/policy.onnx) | [project.sim](self-righting/project.sim) | 605 / 127 |

## Usage

1. Download a `project.sim` and open it in Sim2Sim or Sim2Real. Each complete project includes the model, policy, and observation/action configuration.
2. Inspect it in simulation first. Map and calibrate your own hardware before physical deployment; your device calibration is not included in these files.
3. When using ONNX separately, retain the accompanying `sim2sim.profile.json`, which defines timing, observations, joint mappings, and controller state.

There are **12 actuated joints**. Additional ONNX outputs carry controller feedback state; they are not extra joints and must not all be sent to servos. The self-righting entry originally uses `terminal-hold.onnx`; its standalone copy is named `policy.onnx` here. The complete `.sim` preserves the original layout.

[Back to homepage](../README.en.md)

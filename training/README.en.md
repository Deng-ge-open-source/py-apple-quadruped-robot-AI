[简体中文](README.md) · **English**

# Py-Apple Dog 5 · Forward-gait training

This package covers **standing and forward trotting**. The website still lists the example as “菠萝狗 第四代 12自由度” (Py-Apple Dog Gen4, 12 DOF); the repository uses the name Py-Apple Dog 5.

## Files

| File | Purpose |
| :---: | :---: |
| [py-apple-dog-forward.simready](forward-trot/py-apple-dog-forward.simready) | Official SimReady example with the robot model, joint mapping, rewards, and training settings |
| [mjlab-training-project.zip](forward-trot/mjlab-training-project.zip) | Original MJLab training project accompanying the source of the Sim2Real forward policy |
| [training-settings.json](forward-trot/training-settings.json) | Training settings extracted from the official example |
| [effective-training.json](forward-trot/effective-training.json) | Effective training configuration saved with the original forward-policy project |
| [source.json](forward-trot/source.json) | Download endpoint, source version, hashes, and correspondence checks |

## Getting started

1. Open [StackForce SimReady](https://sim.stackforce.cc/), choose **Open project / file**, and load the `.simready` file. Alternatively, load “菠萝狗 第四代 12自由度” from the example list.
2. Review the 12 joints, default pose, observations, and actions in **Policy mapping**. Keep these defaults for the first run. Forward motion in this model uses **X = -0.1 m/s**; do not change the sign without checking the coordinate system.
3. In **Training**, install and start the local runner provided by the website, connect it, and begin with small-scale validation. Reduce environment count and iterations when using a CPU or limited GPU memory.
4. The task mixes standing and forward commands. Monitor the built-in curves and replay saved checkpoints to assess standing, forward motion, and starting/stopping separately.
5. Save the project, settings, and checkpoints. The original recipe trains from random initialization; the pretrained ONNX files are not initialization weights for a from-scratch run. Compare checkpoints before simulation and hardware adaptation.

## Original recipe

| Setting | Value |
| :---: | :---: |
| Framework / algorithm | MJLab / PPO |
| Command mix | 50% standing, 50% forward; zero lateral and yaw commands |
| Forward command | X = -0.1 m/s in model coordinates |
| Timing | 0.001 s simulation timestep; control every 20 steps (50 Hz) |
| PPO learning rate | Fixed at 0.00015 |
| Original scale | 4096 environments, 841 iterations, checkpoint every 20 iterations, seed 7 |
| Actor / critic hidden layers | [128, 64] / [256, 128] |

These values document the original recipe. Use a smaller run to verify the workflow on limited hardware, and judge motion quality through playback.

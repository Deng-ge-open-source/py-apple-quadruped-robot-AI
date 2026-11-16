[简体中文](COMPATIBILITY.md) · **English**

# Matching the robot, model, and policy

Py-Apple Dog 5 examples on the companion websites retain Gen4 names or `pydog-gen4-*` identifiers. Select the matching example and keep its model, policy, and joint configuration together.

<div align="center">

| Component | How to use it |
| :---: | :---: |
| Mechanical structure | 12-DOF structure with wheeled lower legs; follow the [print list](print-list.en.csv) and [printing guide](PRINTING.en.md) |
| SimReady | Open the [forward-gait training project](../training/README.en.md) in [SimReady](https://sim.stackforce.cc/) to configure training and replay results |
| Sim2Sim | Select the matching Py-Apple Dog example in [Sim2Sim](https://sim2sim.stackforce.cc/) to check the model, policy, and motion |
| Sim2Real | Configure the device, joint mapping, and zero positions in [Sim2Real](https://sim2real.stackforce.cc/), then deploy the matching policy |
| Controller and HAT | ESP32-S3 Zero + Connector HAT RevB; see the [hardware files](../hardware/README.en.md) and [wiring guide](WIRING.en.md) |
| Standing and forward trot | `pydog-gen4-stand-forward`; [policy and deployment project](../policies/forward-trot/) |
| Omnidirectional trot | `pydog-gen4-trot-v132-100`; [policy and deployment project](../policies/omnidirectional-trot/) |
| Wheeled lower legs | Wheel locking or passive rotation must match the selected simulation model |

</div>

Before deployment, match joint order, direction, zero positions, limits, servo specifications, mass, and center of gravity. Also match the policy's observation dimensions, history length, control period, and action scaling. The `pydog12` and Gen4 examples use different models and configurations and are not interchangeable.

The five policies and their compatibility information are in [policies/](../policies/README.en.md). Each `source.json` retains the original example's validation status. The [training instructions](../training/README.en.md) cover standing and forward trotting; other motions require their own matching training configurations. On your robot, start with one joint, one leg, and standing before trying locomotion.

[Back to homepage](../README.en.md)

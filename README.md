# UAV Platform

## Description
Building environments for navigation, drone tracking, etc. in a pybullet simulation.

## Installation
```bash
git clone https://github.com/utiasDSL/gym-pybullet-drones.git
cd gym-pybullet-drones/

conda create -n drones python=3.10
conda activate drones

pip3 install --upgrade pip
pip3 install -e
```

## Framework
```plaintext
2025_UAV_Platform
├── gym_pybullet_drones/       # 核心 Python 包
│   ├── __init__.py            # 包初始化
│   ├── assets/                # URDF、EEPROM 等模型与固件文件
│   │   ├── crazyflie.cf2x.urdf
│   │   ├── eeprom.bin
│   │   └── ...
│   ├── envs/                  # 各种飞控与RL环境（继承 BaseAviary / BaseRLAviary）
│   │   ├── BaseAviary.py
│   │   ├── BaseRLAviary.py
│   │   ├── NavRLAviary.py
│   │   └── ...  
│   ├── control/               # 控制器模块，将速度／姿态指令映射为电机推力
│   │   ├── BaseControl.py
│   │   ├── DSLPIDControl.py
│   │   └── ...
│   ├── utils/                 # 枚举类型、日志、WandB 回调等工具
│   │   ├── enums.py
│   │   ├── Logger.py
│   │   ├── wandb_callback.py
│   │   └── ...
│   └── examples/              # 示例脚本
│       ├── pid.py
│       ├── pid_velocity.py
│       ├── learn_navrl.py
│       ├── test_navrl_gui.py
│       └── ...
├── pyproject.toml             # 包管理与依赖配置
├── README.md                  # 项目说明
├── pypi_description.md        # PyPI 发布说明
└── LICENSE
```

## Virtual Display
```bash
ps aux | grep Xvfb
kill <PID>

Xvfb :4 -screen 0 1280x720x24 & 
x11vnc -display :4 -rfbport 44445 -nopw &
export DISPLAY=:4
```

## References
* https://github.com/utiasDSL/gym-pybullet-drones
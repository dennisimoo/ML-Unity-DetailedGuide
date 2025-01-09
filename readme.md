# ML-Unity-DetailedGuide

A collection of different projects in Unity about ML-Agents such as **DungeonEscape**, **Sorter**, and **WallJump** for reinforcement learning using Unity environments. I felt that the original did not have enough detailed steps on running the model, so being the newcomer to Unity myself, I'm working on this project. My aim with this project is to guide people step by step, who may be having similar challenges when starting off.

## Features
- **Builtin ML-Agents environments**- several come out of the box, e.g. DungeonEscape, Sorter, and WallJump
- **Training Configuration** - easily change hyper parameters, rewards etc via YAML files
- **Parallel environment training**- Train many instances of environment in parallel for speed
- **Export of Trained Models** - export models that have been trained to.ONNX format and then do inference in Unity

## Installation & Usage

### 1. Prerequisites
Ensure you have the following installed:

* **Unity Hub** (Latest version) – [Download Link](https://unity.com/download)
* **Unity Editor** (Version 2023.2 to avoid compatibility issues)
* **Python 3.10** – Install using the following command:
```bash
# macOS
brew install python@3.10
# Windows
choco install python --version=3.10
```
* **Pip** – for managing Python packages (it is installed with Python)
  
Verify that pip is installed using the following command:
```bash
python3.10 -m pip --version
```
* **Unity ML-Agents Toolkit** – After activating your virtual environment, install using the following command:
```bash
source venv/bin/activate
pip install torch -f https://download.pytorch.org/whl/torch_stable.html
pip install mlagents
```

### 2. Running the Unity Project
1. **Clone this repository** and then navigate into the directory where the repository was downloaded to:
```bash
cd /Users/yourname/Downloads/ML-Unity-DetailedGuide
```

2. **Open Unity Hub**, click **Add**, and select the entire project folder:
```
/Users/yourname/Downloads/ML-Unity-DetailedGuide/Project
```

3. Make sure you have Unity version **2023.2** installed.

4. Once the project is opened, navigate to:
```
Assets > ML-Agents > Examples
```
Select any of the various environments you see inside of the `Scenes` folder (**Soccer**, **DungeonEscape**, etc.).

### 3. Training a New Model
Before training, activate your virtual environment:
```bash
source venv/bin/activate
```

Then use any of these commands:

- **Soccer Training**:
```bash
mlagents-learn config/poca/SoccerTwosHigherLayers.yaml --run-id=soccer_ml_run
```

- **Sorter Training**:
```bash
mlagents-learn config/ppo/Sorter_curriculum.yaml --run-id=sorter_ml_run --time-scale=10 --num-envs=1
```

- **Worm Training**:
```bash
mlagents-learn config/ppo/Worm.yaml --run-id=worm_ml_run --time-scale=10 --num-envs=1
```

- **WallJump Training**:
```bash
mlagents-learn config/ppo/WallJump.yaml --run-id=walljump_ml_run --time-scale=10 --num-envs=1
```

### 4. Parameters
- `--run-id`: Unique name for the training session
- `--time-scale`: Speed multiplier for the Unity environment
- `--num-envs`: Number of parallel environment instances

### Important Notes
- Every time you want to train you have to:
  1. Go in project directory in terminal
  2. Run `source venv/bin/activate`
  3. Run training command
- Add `--resume` at the end of your command to continue training from previous session

### Tips
- If your performances are low, decrease `--time-scale` or `--num-envs`

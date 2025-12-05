This repo is based on (LeRobot)[https://github.com/huggingface/lerobot] and (RoboCandyWrapper)[https://github.com/villekuosmanen/RoboCandyWrapper].

To use RoboCandyWrapper:
```bash
conda create -n candy python=3.10 -y
conda activate candy
#If it shows Windows paths or you're inside /mnt/c/..., simply move to Linux home first:
cd ~

pip install robocandywrapper
#OR
git clone https://github.com/villekuosmanen/RoboCandyWrapper.git
cd RoboCandyWrapper
pip install -e .

python
```
Inside python:
```bash
from robocandywrapper import make_dataset_without_config

repo_ids = [
    "lerobot/svla_so100_pickplace",
    "lerobot/svla_so100_stacking",
]

dataset = make_dataset_without_config(repo_ids)
print(len(dataset))
```
If that prints a number (episode count), RoboCandyWrapper works.
```bash
exit()
```
```bash
python -m examples.add_episode_annotations     --dataset amtellezfernandez/robot-learning-tutorial-data     --episode 0     --success     --annotate operator "am"     --annotate notes "alba teleoperated this" --show-timestamps
```
```bash
# Add multiple annotations to one episode
python -m examples.add_episode_annotations --dataset amtellezfernandez/robot-learning-tutorial-data \
    --episode 0 \
    --success \
    --annotate human_visible "no" \
    --annotate quality "good" \
    --annotate task_id "candy_wrapper_pick_v1" \
    --annotate object "box" \
    --annotate obstacles_present "no" \
    --annotate collisions "none"
```
```bash

# Add dataset-level annotations
python -m examples.add_episode_annotations --dataset amtellezfernandez/robot-learning-tutorial-data \
    --dataset-annotate robot_model "kassow" \
    --dataset-annotate end_effector "standard_gripper" \
    --dataset-annotate workspace_id "manufacturing_cell_A3" \
    --dataset-annotate environment_type "factory_h"
```
```bash

# Batch operation - modify 5 episodes at once
python -m examples.add_episode_annotations --dataset amtellezfernandez/robot-learning-tutorial-data \
    --episodes "0,1,2,3,4" \
    --annotate quality "good" \
    --annotate human_visible "yes"
```
```bash

# Modify all episodes
python examples/add_episode_annotations.py --dataset amtellezfernandez/robot-learning-tutorial-data \
    --all-episodes \
    --annotate batch_id "2024-01-15"
```

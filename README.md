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

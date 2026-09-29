# GPU Usage Guide

A **step-by-step guide for accessing and using the GPU servers at IIIT Guwahati (IIITG)**

---



# Account Acquisition

Students / Scholars of **IIIT Guwahati** must obtain **GPU server credentials** from the **ICT**.

### Steps
1. Contact the ICT support team.
2. Request **GPU server access**.
3. Once approved, you will receive:
   - **Username**
   - **Password**
   - **Server address**

---

# Required Software

Install the following tools on your **local machine**.

| Tool | Purpose |
|-----|-----|
| WinSCP | Transfer files between your system and server |
| PuTTY | SSH access to the server |

---

# Server Login Setup

###  Install WinSCP

Download and install **WinSCP**.

###  Connect to the Server

1. Open **WinSCP**
2. Enter:
   - Hostname
   - Username
   - Password
3. Click **Login**

---

###  Install PuTTY

Download and install **PuTTY** if it is not already installed.

---

###  Open PuTTY from WinSCP

Inside **WinSCP**, open **PuTTY terminal**.

---

###  Login Using Credentials

Enter the **server credentials** provided by the ICT section.

---

# Environment Setup

### Activate Anaconda

```bash
source ~/anaconda3/bin/activate
```

---

### Create a New Conda Environment

```bash
conda create --name myenv
```

---

### Activate Environment

```bash
conda activate myenv
```

---

### Deactivate Environment

```bash
conda deactivate
```

---

# Installing PyTorch with CUDA

Run the following command:

```bash
conda install pytorch==2.5.0 torchvision==0.20.0 torchaudio==2.5.0 pytorch-cuda=12.4 -c pytorch -c nvidia
```

This installs:

- PyTorch
- Torchvision
- Torchaudio
- CUDA support

---

# Useful Commands

### Check Available GPUs

```bash
nvidia-smi
```

Displays:
- GPU cards
- Memory usage
- Running processes

---

### Run Program on Specific GPU

```bash
CUDA_VISIBLE_DEVICES=2 python check_GPU.py
```

Where:

- `2` → GPU ID  
- `check_GPU.py` → Python program


  ```bash
  Visible CUDA devices: 7

```bash
Logical cuda:0
  Name      : NVIDIA A100-PCIE-40GB
  PCI Bus ID: Not available in this PyTorch version
```

```bash
Logical cuda:1
  Name      : NVIDIA A100-PCIE-40GB
  PCI Bus ID: Not available in this PyTorch version
```
```bash
Logical cuda:2
  Name      : NVIDIA A100-PCIE-40GB
  PCI Bus ID: Not available in this PyTorch version
```
```bash
Logical cuda:3
  Name      : NVIDIA A100-PCIE-40GB
  PCI Bus ID: Not available in this PyTorch version
```
```bash
Logical cuda:4
  Name      : Tesla V100-PCIE-32GB
  PCI Bus ID: Not available in this PyTorch version
```
```bash
Logical cuda:5
  Name      : Tesla V100-PCIE-32GB
  PCI Bus ID: Not available in this PyTorch version
```
```bash
Logical cuda:6
  Name      : Tesla V100-PCIE-32GB
  PCI Bus ID: Not available in this PyTorch version
  ```
  

---

### Monitor Running Processes

```bash
top
```

Shows:
- Running processes
- Active users
- CPU usage

---

### Check GPU Status

```bash
gpustat
```

Displays GPU utilization in a simplified format.

---

#  Running Programs in Background

To run a program **without keeping your local machine connected**, use:

```bash
CUDA_VISIBLE_DEVICES=2 nohup python check_GPU.py &
```

Explanation:

| Command | Description |
|------|------|
| `nohup` | Keeps program running after logout |
| `&` | Runs the process in background |

After running:

- A **Process ID (PID)** will be returned
- Output will be saved in **nohup.out**

---

### Check Program Output

```bash
cat nohup.out
```

---


## Server Overview

The GPU server is a shared, multi-user Linux machine with seven NVIDIA GPUs.

| GPU ID | Model | Memory | Architecture |
|--------|-------|--------|--------------|
| 0 | NVIDIA A100-PCIE-40GB | 40 GB | Ampere |
| 1 | NVIDIA A100-PCIE-40GB | 40 GB | Ampere |
| 2 | NVIDIA A100-PCIE-40GB | 40 GB | Ampere |
| 3 | NVIDIA A100-PCIE-40GB | 40 GB | Ampere |
| 4 | Tesla V100-PCIE-32GB | 32 GB | Volta |
| 5 | Tesla V100-PCIE-32GB | 32 GB | Volta |
| 6 | Tesla V100-PCIE-32GB | 32 GB | Volta |

> **Note:** The V100 does not support `bfloat16`. Use an A100 (GPU 0–3) for BF16 workloads.

---

## 2. Account Acquisition

Students and scholars of IIIT Guwahati must obtain GPU server credentials from the **ICT section**.

1. Contact the ICT support team.
2. Request GPU server access.
3. Once approved, you will receive:
   - **Username**
   - **Password**
   - **Server address**

After your first login, change the initial password:

```bash
passwd
```

---

## Required Software

Install the following on your local machine.

| Tool | Platform | Purpose |
|------|----------|---------|
| [WinSCP](https://winscp.net) | Windows | Transfer files between your system and the server |
| [PuTTY](https://www.putty.org) | Windows | SSH terminal access to the server |
| OpenSSH (`ssh`, `scp`) | Linux / macOS / Windows 10+ | Built-in command-line alternative |
| [VS Code](https://code.visualstudio.com) + Remote-SSH | All | Edit and run code on the server (optional) |
| [Git](https://git-scm.com) | All | Version control for your code (optional) |

---


## Basic Linux Commands

### Navigation

| Command | Description | Example |
|---------|-------------|---------|
| `pwd` | Show current directory | `pwd` |
| `ls` | List files | `ls` |
| `ls -lh` | List with sizes, owner, date | `ls -lh ~/data` |
| `ls -la` | Include hidden files | `ls -la ~` |
| `ls -lt` | Sort by modification time (newest first) | `ls -lt logs/` |
| `cd <dir>` | Change directory | `cd ~/project` |
| `cd ..` | Go up one level | `cd ..` |
| `cd ~` / `cd` | Go to home directory | `cd` |
| `cd -` | Return to previous directory | `cd -` |
| `tree -L 2` | Show directory structure (2 levels) | `tree -L 2 ~/project` |

### File and directory operations

| Command | Description | Example |
|---------|-------------|---------|
| `mkdir <dir>` | Create a directory | `mkdir results` |
| `mkdir -p <path>` | Create nested directories | `mkdir -p runs/exp1/logs` |
| `touch <file>` | Create an empty file | `touch notes.txt` |
| `cp <src> <dst>` | Copy a file | `cp train.py train_v2.py` |
| `cp -r <src> <dst>` | Copy a directory | `cp -r code code_backup` |
| `mv <src> <dst>` | Move or rename | `mv old.py new.py` |
| `rm <file>` | Delete a file | `rm nohup.out` |
| `rm -r <dir>` | Delete a directory | `rm -r runs/exp1` |
| `rm -i <file>` | Delete with confirmation | `rm -i *.pt` |
| `ln -s <target> <link>` | Create a shortcut (symbolic link) | `ln -s ~/data/mitbih data` |

> **Warning:** `rm` deletes permanently. There is no recycle bin.

### Viewing files

| Command | Description | Example |
|---------|-------------|---------|
| `cat <file>` | Print the whole file | `cat config.yaml` |
| `less <file>` | Scroll through a file (`q` quit, `/word` search) | `less train.log` |
| `head -n N <file>` | First N lines | `head -n 20 data.csv` |
| `tail -n N <file>` | Last N lines | `tail -n 50 train.log` |
| `tail -f <file>` | Follow a file as it grows | `tail -f train.log` |
| `wc -l <file>` | Count lines | `wc -l data.csv` |

### Searching

| Command | Description | Example |
|---------|-------------|---------|
| `grep "<text>" <file>` | Find lines containing text | `grep "accuracy" train.log` |
| `grep -i` | Case-insensitive search | `grep -i "error" train.log` |
| `grep -r "<text>" <dir>` | Search recursively in a directory | `grep -r "lr=" ~/project` |
| `grep -n` | Show line numbers | `grep -n "import" train.py` |
| `find <dir> -name "<pattern>"` | Find files by name | `find ~ -name "*.pt"` |
| `find <dir> -size +1G` | Find files larger than 1 GB | `find ~ -size +1G` |
| `which <cmd>` | Show which executable runs | `which python` |

### Permissions

| Command | Description | Example |
|---------|-------------|---------|
| `chmod +x <file>` | Make a script executable | `chmod +x run.sh` |
| `chmod 700 <dir>` | Restrict a directory to yourself | `chmod 700 ~/private` |
| `ls -l` | View permissions | `ls -l run.sh` |

### Editing files

```bash
nano train.py       # Ctrl+O to save, Ctrl+X to exit
vim train.py        # i to insert, Esc then :wq to save and exit, :q! to quit without saving
```

### Shell shortcuts and history

| Command / Key | Description |
|---------------|-------------|
| `Tab` | Auto-complete file or command names |
| `↑` / `↓` | Previous / next command |
| `Ctrl + C` | Stop the running foreground program |
| `Ctrl + R` | Search command history |
| `Ctrl + L` / `clear` | Clear the screen |
| `history` | List previous commands |
| `!<n>` | Re-run command number `n` from history |
| `man <cmd>` | Show the manual for a command |
| `<cmd> --help` | Show a short usage summary |

> In PuTTY, selecting text copies it and right-click pastes.

---

## Transferring Files

### WinSCP

Drag and drop files between the local (left) and server (right) panes. For large datasets, upload a single `.zip` or `.tar.gz` and extract it on the server.

### scp (run on the local machine)

| Task | Command |
|------|---------|
| Upload a file | `scp train.py <username>@<server-address>:~/project/` |
| Upload a directory | `scp -r dataset/ <username>@<server-address>:~/data/` |
| Download a file | `scp <username>@<server-address>:~/project/results.csv .` |
| Download a directory | `scp -r <username>@<server-address>:~/project/results ./` |

### rsync (large or repeated transfers, Linux/macOS)

Copies only changed files and can resume interrupted transfers.

```bash
rsync -avzP dataset/ <username>@<server-address>:~/data/dataset/
rsync -avzP <username>@<server-address>:~/project/checkpoints/ ./checkpoints/
```

| Flag | Meaning |
|------|---------|
| `-a` | Preserve permissions and timestamps |
| `-v` | Verbose output |
| `-z` | Compress during transfer |
| `-P` | Show progress and allow resume |

### Archives

| Task | Command |
|------|---------|
| Extract `.zip` | `unzip dataset.zip -d ~/data/` |
| Extract `.tar.gz` | `tar -xzf dataset.tar.gz -C ~/data/` |
| Create `.zip` | `zip -r results.zip results/` |
| Create `.tar.gz` | `tar -czf results.tar.gz results/` |
| List `.tar.gz` contents | `tar -tzf dataset.tar.gz` |

### Downloading directly to the server

```bash
wget <url>                                    # download a file
wget -c <url>                                 # resume an interrupted download
curl -L -o file.zip <url>                     # download with curl
git clone https://github.com/<user>/<repo>.git  # clone a repository
```

---

## Environment Setup

### Activate Anaconda

```bash
source ~/anaconda3/bin/activate
```

### Create a new environment

```bash
conda create --name myenv python=3.10
```

### Activate the environment

```bash
conda activate myenv
```

### Deactivate the environment

```bash
conda deactivate
```

### Environment management

| Command | Description |
|---------|-------------|
| `conda env list` | List all environments |
| `conda create --name newenv --clone myenv` | Copy an environment |
| `conda remove --name myenv --all` | Delete an environment |
| `conda env export > environment.yml` | Export environment to a file |
| `conda env create -f environment.yml` | Recreate environment from a file |
| `conda info` | Show conda configuration and active environment |

### Package management

| Command | Description |
|---------|-------------|
| `conda list` | List installed packages |
| `conda list <name>` | Check if a package is installed |
| `conda install <pkg>` | Install a package with conda |
| `conda install <pkg>=<version>` | Install a specific version |
| `conda update <pkg>` | Update a package |
| `conda remove <pkg>` | Uninstall a package |
| `pip install <pkg>` | Install a package with pip |
| `pip install -r requirements.txt` | Install from a requirements file |
| `pip freeze > requirements.txt` | Save installed pip packages |
| `pip show <pkg>` | Show package version and location |
| `pip uninstall <pkg>` | Uninstall a pip package |
| `conda clean --all` | Remove cached conda packages |
| `pip cache purge` | Remove cached pip packages |

### Auto-activate Anaconda at login (optional)

```bash
~/anaconda3/bin/conda init bash
source ~/.bashrc
```

---

## Installing PyTorch with CUDA

Check the driver's supported CUDA version (top-right of the output). It must be **12.4 or higher**.

```bash
nvidia-smi
```

Install PyTorch inside the activated environment:

```bash
conda install pytorch==2.5.0 torchvision==0.20.0 torchaudio==2.5.0 pytorch-cuda=12.4 -c pytorch -c nvidia
```

This installs PyTorch, Torchvision, Torchaudio, and the CUDA 12.4 runtime.

**pip alternative:**

```bash
pip install torch==2.5.0 torchvision==0.20.0 torchaudio==2.5.0 --index-url https://download.pytorch.org/whl/cu124
```

### Verify the installation

| Check | Command |
|-------|---------|
| PyTorch version | `python -c "import torch; print(torch.__version__)"` |
| CUDA available | `python -c "import torch; print(torch.cuda.is_available())"` |
| Number of GPUs | `python -c "import torch; print(torch.cuda.device_count())"` |
| CUDA build version | `python -c "import torch; print(torch.version.cuda)"` |
| cuDNN version | `python -c "import torch; print(torch.backends.cudnn.version())"` |
| GPU name | `python -c "import torch; print(torch.cuda.get_device_name(0))"` |

Expected: the PyTorch version, `True`, and the number of visible GPUs.

### Common additional packages

```bash
pip install numpy pandas matplotlib scikit-learn tqdm tensorboard
```

---

## Using the GPUs

### Check available GPUs

```bash
nvidia-smi
```

Displays GPU cards, memory usage, utilization, and running processes. Choose a GPU with low memory usage and near 0% utilization.

| Command | Description |
|---------|-------------|
| `nvidia-smi` | Full GPU status |
| `nvidia-smi -L` | List GPUs with IDs and names |
| `nvidia-smi -i 2` | Status of GPU 2 only |
| `watch -n 2 nvidia-smi` | Refresh every 2 seconds (`Ctrl + C` to exit) |
| `nvidia-smi -l 5` | Repeat output every 5 seconds |
| `nvidia-smi --query-gpu=index,name,memory.used,memory.total,utilization.gpu --format=csv` | Compact CSV summary |
| `nvidia-smi --query-compute-apps=pid,used_memory --format=csv` | GPU processes and memory used |
| `nvidia-smi pmon -c 1` | Per-process GPU utilization snapshot |

### Check GPU status (compact view)

```bash
gpustat
```

Shows utilization, memory, and the user of each process. Install with `pip install gpustat` if unavailable.

| Command | Description |
|---------|-------------|
| `gpustat` | One-line summary per GPU |
| `gpustat -cp` | Include command names and PIDs |
| `gpustat -i 2` | Refresh every 2 seconds |
| `gpustat --json` | Output as JSON |

### Run a program on a specific GPU

```bash
CUDA_VISIBLE_DEVICES=2 python check_GPU.py
```

- `2` — GPU ID
- `check_GPU.py` — Python program

`CUDA_VISIBLE_DEVICES` exposes only the selected GPU(s) to the program, renumbered from zero. Inside your code, use `torch.device("cuda")` — **not** `cuda:2`.

| Command | GPUs visible to the program |
|---------|-----------------------------|
| `CUDA_VISIBLE_DEVICES=2 python train.py` | Physical GPU 2 (as `cuda:0`) |
| `CUDA_VISIBLE_DEVICES=1,3 python train.py` | Physical GPUs 1 and 3 (as `cuda:0`, `cuda:1`) |
| `CUDA_VISIBLE_DEVICES="" python train.py` | None (CPU only) |
| `python train.py` | All 7 GPUs |

Set a GPU for the entire terminal session:

```bash
export CUDA_VISIBLE_DEVICES=2
echo $CUDA_VISIBLE_DEVICES     # confirm the value
unset CUDA_VISIBLE_DEVICES     # remove it
```

> **Recommended:** Add `export CUDA_DEVICE_ORDER=PCI_BUS_ID` to `~/.bashrc` so GPU IDs in PyTorch match those shown by `nvidia-smi`.

### Sample output

Without `CUDA_VISIBLE_DEVICES` (all GPUs visible):

```text
Visible CUDA devices: 7

Logical cuda:0  NVIDIA A100-PCIE-40GB
Logical cuda:1  NVIDIA A100-PCIE-40GB
Logical cuda:2  NVIDIA A100-PCIE-40GB
Logical cuda:3  NVIDIA A100-PCIE-40GB
Logical cuda:4  Tesla V100-PCIE-32GB
Logical cuda:5  Tesla V100-PCIE-32GB
Logical cuda:6  Tesla V100-PCIE-32GB
```

With `CUDA_VISIBLE_DEVICES=2`:

```text
Visible CUDA devices: 1

Logical cuda:0  NVIDIA A100-PCIE-40GB
```

### Multi-GPU training

```bash
CUDA_VISIBLE_DEVICES=0,1 torchrun --nproc_per_node=2 train_ddp.py
```

Use GPUs of the same model (A100 with A100, V100 with V100) in one job.

---

## Running Programs in the Background

### nohup

To keep a program running after disconnecting:

```bash
CUDA_VISIBLE_DEVICES=2 nohup python check_GPU.py &
```

| Component | Description |
|-----------|-------------|
| `nohup` | Keeps the program running after logout |
| `&` | Runs the process in the background |

After running:

- A **Process ID (PID)** is returned.
- Output is saved to **`nohup.out`**.

### Check program output

| Command | Description |
|---------|-------------|
| `cat nohup.out` | Print the entire output |
| `tail -n 50 nohup.out` | Last 50 lines |
| `tail -f nohup.out` | Live view (`Ctrl + C` stops viewing, not the job) |
| `grep "loss" nohup.out` | Filter specific lines |



### Job control (current session)

| Command | Description |
|---------|-------------|
| `jobs` | List background jobs in this session |
| `fg %1` | Bring job 1 to the foreground |
| `Ctrl + Z` | Pause the foreground job |
| `bg %1` | Resume job 1 in the background |
| `disown %1` | Detach job 1 from the session |
| `echo $!` | PID of the last background job |

### tmux

| Action | Command |
|--------|---------|
| Start a session | `tmux new -s train` |
| Detach | `Ctrl + B`, then `D` |
| List sessions | `tmux ls` |
| Reattach | `tmux attach -t train` |
| Kill a session | `tmux kill-session -t train` |
| Split pane horizontally | `Ctrl + B`, then `"` |
| Split pane vertically | `Ctrl + B`, then `%` |
| Switch pane | `Ctrl + B`, then arrow key |
| Scroll output | `Ctrl + B`, then `[` (press `q` to exit) |

### screen (alternative to tmux)

| Action | Command |
|--------|---------|
| Start a session | `screen -S train` |
| Detach | `Ctrl + A`, then `D` |
| List sessions | `screen -ls` |
| Reattach | `screen -r train` |

---


## Managing Processes

### Monitor running processes

```bash
top
```

Shows running processes, active users, CPU and memory usage.

| Key (inside `top`) | Action |
|--------------------|--------|
| `q` | Quit |
| `u` | Filter by username |
| `M` | Sort by memory |
| `P` | Sort by CPU |
| `k` | Kill a process by PID |
| `1` | Show individual CPU cores |

| Command | Description |
|---------|-------------|
| `top -u $USER` | Show only your processes |
| `htop` | Interactive process viewer (if installed) |

### Find processes

| Command | Description |
|---------|-------------|
| `ps -u $USER` | List your processes |
| `ps -u $USER -f` | With full command lines |
| `ps -u $USER -f \| grep python` | Your Python processes |
| `pgrep -u $USER -a python` | Python processes with PIDs |
| `ps -p <PID> -o etime` | How long a process has been running |

### Stop processes

| Command | Description |
|---------|-------------|
| `Ctrl + C` | Stop a foreground program |
| `kill <PID>` | Graceful stop |
| `kill -9 <PID>` | Force stop (only if `kill` fails) |
| `pkill -u $USER -f train.py` | Stop your processes matching `train.py` |
| `killall -u $USER python` | Stop all your Python processes |

Confirm with `nvidia-smi` that GPU memory has been released.

---

## System Information

| Command | Description |
|---------|-------------|
| `nproc` | Number of CPU cores |
| `lscpu` | CPU details |
| `free -h` | RAM usage |
| `uptime` | Uptime and load average |
| `uname -a` | Kernel and OS information |
| `cat /etc/os-release` | Linux distribution and version |
| `nvcc --version` | CUDA Toolkit version (if installed system-wide) |
| `python --version` | Active Python version |

---

## Disk Usage

| Command | Description |
|---------|-------------|
| `df -h ~` | Free space on the home disk |
| `du -sh ~` | Total size of your home directory |
| `du -sh ~/*` | Size of each item in home |
| `du -sh ~/* \| sort -h` | Same, sorted by size |
| `du -sh ~/.cache ~/anaconda3/pkgs` | Size of common cache folders |
| `find ~ -size +1G` | Files larger than 1 GB |

Cleanup commands:

```bash
conda clean --all
pip cache purge
rm -rf ~/.cache/torch/hub/checkpoints/<unused-model>
```

---

## GPU Memory and Performance Tips

These techniques reduce GPU memory usage so your job fits on a shared GPU and leaves room for others.

| Technique | How | Effect |
|-----------|-----|--------|
| Reduce batch size | `batch_size=32` instead of `128` | Directly lowers activation memory |
| Mixed precision | `torch.autocast` (see below) | Roughly halves activation memory; faster on A100/V100 |
| Gradient accumulation | Step the optimizer every N batches | Large effective batch with small memory |
| No gradients during evaluation | `with torch.no_grad():` | Avoids storing activations |
| Free cached memory | `torch.cuda.empty_cache()` | Returns unused cached memory to the GPU |
| Pinned memory | `DataLoader(..., pin_memory=True)` | Faster CPU → GPU transfer |
| Moderate data workers | `num_workers=4` to `8` | Keeps the GPU busy without overloading shared CPUs |

### a. Mixed precision

```python
import torch

use_bf16 = torch.cuda.is_bf16_supported()          # True on A100, False on V100
dtype = torch.bfloat16 if use_bf16 else torch.float16
scaler = torch.amp.GradScaler("cuda", enabled=not use_bf16)

for x, y in loader:
    x, y = x.cuda(non_blocking=True), y.cuda(non_blocking=True)
    optimizer.zero_grad()
    with torch.autocast(device_type="cuda", dtype=dtype):
        loss = loss_fn(model(x), y)
    scaler.scale(loss).backward()
    scaler.step(optimizer)
    scaler.update()
```

### b. Gradient accumulation

```python
accum_steps = 4                                     # effective batch = batch_size x 4
for i, (x, y) in enumerate(loader):
    loss = loss_fn(model(x.cuda()), y.cuda()) / accum_steps
    loss.backward()
    if (i + 1) % accum_steps == 0:
        optimizer.step()
        optimizer.zero_grad()
```

### Measure memory usage

```python
print(f"Allocated: {torch.cuda.memory_allocated() / 1024**3:.2f} GB")
print(f"Peak:      {torch.cuda.max_memory_allocated() / 1024**3:.2f} GB")
print(torch.cuda.memory_summary())                  # detailed report
```

Cap a process at a fraction of the GPU (optional):

```python
torch.cuda.set_per_process_memory_fraction(0.5, 0)  # at most 50% of cuda:0
```

---

## Do's

- Check `nvidia-smi` or `gpustat` before starting any job.
- Always specify a GPU using `CUDA_VISIBLE_DEVICES`.
- Use only the number of GPUs your job requires.
- Test on a small subset before launching long runs.
- Save checkpoints regularly.
- Stop jobs you no longer need and release GPUs promptly.
- Shut down idle Jupyter kernels; they hold GPU memory.
- Do not share your account or terminate other users' processes.
- Report hardware or access issues to ICT.

---



## Quick Reference

```bash
# Connect
ssh <username>@<server-address>

# Environment
source ~/anaconda3/bin/activate
conda activate myenv

# Check GPUs
nvidia-smi
gpustat

# Run on GPU 2 in the background
CUDA_VISIBLE_DEVICES=2 nohup python -u train.py > train.log 2>&1 &

# Monitor
tail -f train.log
top -u $USER
ps -u $USER -f | grep python

# Stop
kill <PID>

# Disk
df -h ~
du -sh ~/* | sort -h

# Jupyter (server), then tunnel (laptop)
jupyter lab --no-browser --port=8890
ssh -N -L 8890:localhost:8890 iiitg

# TensorBoard
tensorboard --logdir runs --port 6007

# Git
git add . && git commit -m "message" && git push

# Auto-select a free GPU
./run_on_free_gpu.sh train.py
```

---

## Appendix A: check_GPU.py

```python
import torch

if not torch.cuda.is_available():
    print("CUDA is not available.")
    raise SystemExit(1)

n = torch.cuda.device_count()
print(f"Visible CUDA devices: {n}\n")

for i in range(n):
    print(f"Logical cuda:{i}  {torch.cuda.get_device_name(i)}")
```

Run:

```bash
python check_GPU.py                          # all GPUs
CUDA_VISIBLE_DEVICES=2 python check_GPU.py   # GPU 2 only
```

---

## Appendix B: run_on_free_gpu.sh

Selects the GPU with the least memory in use and launches your script on it in the background with a timestamped log.

```bash
#!/bin/bash
# Usage:
#   ./run_on_free_gpu.sh train.py --epochs 50
#   GPUS=0,1,2,3 ./run_on_free_gpu.sh train.py      # consider A100s only
#   MAX_USED=2000 ./run_on_free_gpu.sh train.py     # treat GPUs using < 2000 MiB as free

if [ -z "$1" ]; then
    echo "Usage: $0 <script.py> [args...]"
    exit 1
fi

export CUDA_DEVICE_ORDER=PCI_BUS_ID
MAX_USED=${MAX_USED:-1000}        # MiB
GPUS=${GPUS:-}                    # optional list, e.g. 0,1,2,3

QUERY="nvidia-smi --query-gpu=index,memory.used --format=csv,noheader,nounits"
[ -n "$GPUS" ] && QUERY="$QUERY -i $GPUS"

read -r GPU USED < <($QUERY | tr -d ' ' | sort -t',' -k2 -n | head -n1 | tr ',' ' ')

if [ "$USED" -gt "$MAX_USED" ]; then
    echo "No free GPU. Least used: GPU $GPU with ${USED} MiB in use."
    exit 1
fi

mkdir -p logs
LOG="logs/$(basename "$1" .py)_$(date +%Y%m%d_%H%M%S)_gpu${GPU}.log"
CUDA_VISIBLE_DEVICES=$GPU nohup python -u "$@" > "$LOG" 2>&1 &

echo "GPU    : $GPU (${USED} MiB in use before launch)"
echo "PID    : $!"
echo "Log    : $LOG"
```

Setup and usage:

```bash
chmod +x run_on_free_gpu.sh
conda activate myenv
./run_on_free_gpu.sh train.py --lr 0.001
tail -f logs/train_*.log
```

---

## Appendix C: run_experiments.sh

Runs several experiments one after another on the same GPU, each with its own log file.

```bash
#!/bin/bash
# Usage: nohup ./run_experiments.sh > logs/run_experiments.log 2>&1 &

source ~/anaconda3/bin/activate
conda activate myenv

export CUDA_DEVICE_ORDER=PCI_BUS_ID
export CUDA_VISIBLE_DEVICES=2

mkdir -p logs

for LR in 0.01 0.001 0.0001; do
    for BS in 32 64; do
        NAME="lr${LR}_bs${BS}"
        echo "[$(date '+%F %T')] Starting $NAME"
        python -u train.py --lr "$LR" --batch-size "$BS" > "logs/${NAME}.log" 2>&1
        echo "[$(date '+%F %T')] Finished $NAME (exit code $?)"
    done
done

echo "[$(date '+%F %T')] All experiments finished."
```

Setup and usage:

```bash
chmod +x run_experiments.sh
nohup ./run_experiments.sh > logs/run_experiments.log 2>&1 &
tail -f logs/run_experiments.log
```

`train.py` must accept the arguments used above, for example:

```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("--lr", type=float, default=1e-3)
parser.add_argument("--batch-size", type=int, default=64)
parser.add_argument("--epochs", type=int, default=50)
args = parser.parse_args()
```

---




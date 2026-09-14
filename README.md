# GPU Usage Guide – IIIT Guwahati

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

### 1️⃣ Install WinSCP

Download and install **WinSCP**.

### 2️⃣ Connect to the Server

1. Open **WinSCP**
2. Enter:
   - Hostname
   - Username
   - Password
3. Click **Login**

---

### 3️⃣ Install PuTTY

Download and install **PuTTY** if it is not already installed.

---

### 4️⃣ Open PuTTY from WinSCP

Inside **WinSCP**, open **PuTTY terminal**.

---

### 5️⃣ Login Using Credentials

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


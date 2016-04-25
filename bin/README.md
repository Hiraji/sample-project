# sr-code-style-check.sh

## Setup

You need to install Ansible in order to run this script.

Use following command to do so (it will install recent version in contrary to apt-get) 

```bash
sudo pip install ansible
```

## Usage

```bash
sr-code-style-check.sh <repository path (default: ./src)> <workspace path (default: .)> <code-style-check-type(default: code_style_check)>
```

## Results 

The results are written to *&lt;workspace&gt;/build/test_results/&lt;package_name&gt;* in XML format starting with *roslint* prefix.

## Examples

### All default parameters
```bash
 ~/workspaces/ros/sr-build-tools/bin/sr-code-style-check.sh
```

### Path to repository files and workspace specified
```bash
~/workspaces/ros/sr-build-tools/bin/sr-code-style-check.sh ~/workspaces/ros/shadow_ws/src/sr-visualization ~/workspaces/ros/shadow_ws
```

# Compile new rt-preempt kernel deb

## Prepare rt kernel

- Check available versions of rt preempt patch https://www.kernel.org/pub/linux/kernel/projects/rt
- Check corresponding kernel version https://www.kernel.org/pub/linux/kernel
- Edit `prepare_rt_kernel.sh` variables to fit the chosen versions
- Run `prepare_rt_kernel.sh`. It will open menuconfig, where you have to configure the preemption model.
- `Processor type and features` -> `Preemption Model`  set to Fully Preemptible Kernel (RT)

## Create deb

- Edit `create_rt_kernel_deb.sh` variable to fit the chosen version
- Run `create_rt_kernel_deb.sh` in the same directory where `prepare_rt_kernel.sh` was run


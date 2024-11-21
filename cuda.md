# ML Dev

## CUDA

[Ubuntu ](https://developer.nvidia.com/cuda-11-8-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu)

[cudnn](https://docs.nvidia.com/deeplearning/cudnn/support-matrix/index.html)

Download [TTL](https://zhuanlan.zhihu.com/p/501473091)

[Multiple cuda](https://www.cnblogs.com/yhjoker/p/10972795.html)

### Path Specification

Use command `vim ./bashrc`. Append the following commands. These links refer to general `cuda` instead of specific one.

```bash
export LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"
export PATH="/usr/local/cuda/bin:$PATH"
export PATH="/usr/local/cuda/bin/nvcc:$PATH"
```

Then, `source ./bashrc` to compile the configuration file.

### Installation
Only the first time, you need to install the driver.

[Cuda_11.8](https://developer.nvidia.com/cuda-11-8-0-download-archive?target_os=Linux)

But different cuda version requires different gcc version, please refer to the following table.

| CUDA Version                     | Max Supported GCC Version |
|----------------------------------|---------------------------|
| 12.4, 12.5                      | 13.2                      |
| 12.1, 12.2, 12.3                | 12.2                      |
| 12                              | 12.1                      |
| 11.4.1+, 11.5, 11.6, 11.7, 11.8 | 11                        |
| 11.1, 11.2, 11.3, 11.4.0        | 10                        |
| 11                              | 9                         |
| 10.1, 10.2                      | 8                         |
| 9.2, 10.0                       | 7                         |
| 9.0, 9.1                        | 6                         |
| 8                               | 5.3                       |
| 7                               | 4.9                       |
| 5.5, 6                          | 4.8                       |
| 4.2, 5                          | 4.6                       |
| 4.1                             | 4.5                       |
| 4.0                             | 4.4                       |

Check the current gcc version.
```bash
gcc --version
```
Then, use the `update-alternatives` to manage all the gcc versions. If i have `gcc-11` to use `cuda-11.8` for now, and switch to `cuda12.4` requires `gcc-13`. Replace all `X` to `13` in the following commands.

```bash
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-X X
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-X X
```

Switch among gcc versions by using

```bash
sudo update-alternatives --config gcc
```

### Switch CUDA

How to switch between CUDA versions?

For example, switch current cuda to `11.8`. Then use `nvcc -V` to check current real cuda version.

```bash
sudo ln -sfn /usr/local/cuda-11.8 /usr/local/cuda
```

### Troubleshoot

if error "too many soft link comes out", run

```bash
sudo rm /usr/local/cuda
```

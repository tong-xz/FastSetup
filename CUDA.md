# ML Dev

## CUDA

[Ubuntu ](https://developer.nvidia.com/cuda-11-8-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu)

[cudnn](https://docs.nvidia.com/deeplearning/cudnn/support-matrix/index.html)

Download [TTL](https://zhuanlan.zhihu.com/p/501473091)

[Multiple cuda](https://www.cnblogs.com/yhjoker/p/10972795.html)

Use command `vim ./zshrc`

```bash
export LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"
export PATH="/usr/local/cuda/bin:$PATH"
export PATH="/usr/local/cuda/bin/nvcc:$PATH"
```

Then, `source ./zshrc`


How to switch between CUDA versions?

change to another cuda version

sudo ln -sfn /usr/local/cuda-11.8 /usr/local/cuda


if error "too many soft link comes out", run

sudo rm /usr/local/cuda




## [Miniconda](https://docs.conda.io/projects/miniconda/en/latest/miniconda-install.html)







## 

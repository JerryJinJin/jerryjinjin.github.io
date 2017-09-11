---
title: Install PyTorch on Mac
date: 2017-05-09 16:27:56
tags: PyTorch
---

PyTorch 官网： <a>pytorch.org</a>

* 根据官网上提供命令进行安装，此处是在OSX系统下通过conda进行安装。

```
conda install pytorch torchvision -c soumith
```

* 但是使用conda安装失败，出现类似于下面的错误信息。

```
requests.exceptions.HTTPError: 401 Client Error: UNAUTHORIZED for url
conda.exceptions.CondaRuntimeError: Runtime error: HTTPError: 401 Client Error
```

* 使用如下命令解决了该问题。

```
conda update -c defaults conda
```

* 重新执行安装命令，顺利安装完毕。
* 接下来测试是否能够正常使用PyTorch，在python环境下执行`import torch`,出现如下错误。

```
import torch
Traceback (most recent call last):
File "", line 1, in 
File "/usr/local/lib/python3.6/site-packages/torch/init.py", line 53, in 
from torch._C import *
ImportError: dlopen(/usr/local/lib/python3.6/site-packages/torch/_C.cpython-36m-darwin.so, 10): Symbol not found: _PySlice_AdjustIndices
Referenced from: /usr/local/lib/python3.6/site-packages/torch/_C.cpython-36m-darwin.so
Expected in: flat namespace
in /usr/local/lib/python3.6/site-packages/torch/_C.cpython-36m-darwin.so
```

* 可能是由于PyTorch版本的问题，删除之前安装的PyTorch，重新执行下面的安装命令，安装0.1.11版本（默认是安装最新版本0.1.12）。

```
conda install pytorch=0.1.11 torchvision -c soumith
```

* 安装完毕，可以正常使用了。
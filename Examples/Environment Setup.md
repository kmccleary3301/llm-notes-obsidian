## Conda

Install Conda, preferably with [MiniConda](https://docs.conda.io/en/latest/miniconda.html).
You will also likely need to add it to your PATH.
This is most easily done by checking the option to add it to PATH on the installer if you're on Windows. On Linux it should do so automatically, but if it still doesn't work just look up how to add it to PATH.
On Windows, you need to run `conda init` in order to make it work.
Powershell will still not work, and you need to enable script permissions on the system.
Powershell is the default shell on vscode, so this bug can be very annoying.
To test, open a shell and run `conda`. The result should tell you if it worked or not.

## CUDA

Install CUDA toolkit [11.7](https://developer.nvidia.com/cuda-11-7-0-download-archive) or [11.8](https://developer.nvidia.com/cuda-11-8-0-download-archive), as almost all ML repos use torch versions that run on these.
Check that it's installed with `nvcc --version` in any shell.
Install the correct version of torch globally using [this website](https://pytorch.org/).
I recommend selecting conda instead of pip for your package manager.
Finally, test it in your shell like so:
```python
python
>> import torch
>> torch.cuda.is_available()
```
If everything's working properly, it should print `True`.

# plaidml-keras for AMD GPU's (Windows)
```python

Author -> Stefanos Ginargyros

```
## 1. PlaidML Windows Setup

Plaidml can be really tricky to install. In order to overcome all the potential Windows errors, follow carefully.

- Install Anaconda
- Install the latest Visual C++ from [here](https://support.microsoft.com/en-us/topic/the-latest-supported-visual-c-downloads-2647da03-1eea-4433-9aff-95f26a218cc0)
- Now RESTART!
- Create a conda virtual environment for plaidml

```
conda create -n plaidml
```

- Uninstall any conflicting or older version

```
pip uninstall plaidml
pip uninstall plaidml-keras
pip uninstall plaidbench

pip install plaidml==0.6.4
```

- Install plaidml-keras
```
pip install plaidml-keras plaidbench
```
- Setup plaidml (Choose between 1,2,3,4.. the one that represent your graphics card)
```
plaidml-setup
```
- Before running any test, downgrade h5py bellow version 3.0.0 because of conflicts. (I went for 2.10.0)
```
pip install h5py==2.10.0
```
- Now you can run any test you want, and verify your installation. Some of them are:

```
plaidbench keras mobilenet
```
or
```
plaidbench --batch-size 16 keras --train mobilenet
```
- Remember to set the batch size, to a number that doesn't exceed your GPU VRAM. For my Tahiti chip AMD-GPU (3 gigs of RAM) a good number for this test was --batch-size 8.



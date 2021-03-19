# Plaidml-Keras GPU for Windows
```python

Author -> Stefanos Ginargyros

```
## Setup

If you are here, you already now that Plaidml can be really tricky to install (especially in Windows). In order to overcome all the potential Windows errors, follow carefully.

- Install Anaconda from [here](https://docs.anaconda.com/anaconda/install/windows/)
- Install the latest Visual C++ from [here](https://support.microsoft.com/en-us/topic/the-latest-supported-visual-c-downloads-2647da03-1eea-4433-9aff-95f26a218cc0)
- Restart!
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
plaidbench --batch-size 8 keras --train mobilenet
```
- Remember to set the batch size, to a number that doesn't exceed your GPU VRAM. For my Tahiti chip AMD-GPU (3 gigs of RAM) a good number for this test was --batch-size 8.
- If everything went smoothly then by running AMD Randeon Software while testing with the above command, you should see something similar to this: 

<img src='https://github.com/stefgina/plaidml-keras-AMD-GPU/blob/main/plaidml4.png'>



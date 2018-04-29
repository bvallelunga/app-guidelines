# App Guidelines

This document is to help maintainers navigate the nuances of the Doppler marketplace. It will include tips to make sure imports work, hard dependencies, and restrictions placed by Doppler.


# Enviroment

All apps will be running on a [Python3](https://docs.python.org/3/) enviroment. These packages will be installed by defaults:
  - "requests",
  - "cement",
  - "colorlog",
  - "jsonmodels",
  - "tabulate",
  - "flask",
  - "persist-queue",
  - "keras",
  - "scikit-learn",
  - "scipy",
  - "pandas",
  - "numpy",
  - "torchvision",
  - "simplejson",
  - "[PyTorch](http://download.pytorch.org/whl/cu91/torch-0.3.1-cp35-cp35m-linux_x86_64.whl)"


# Hard Requirements

  - Model binary file (zip) must not be greater than 500mb
  - Model must be able to run the inference within 28 secs. **(No Exceptions)**
  - Model code must not log input data from user, Doppler will provide a standarized way to collect this data
  
# Tips and Tricks

** Importing Code**
Importing local files in Python3 can be pretty tricky so we recommend appending your entry point's current path.

``` py
# Add Current Directory to Path
import sys, os
sys.path.append(os.path.dirname(os.path.realpath(__file__)))

# Import Local Files
from encoder import Model
from utils import load_model_params
```

** Importing Binary Files**
We recommend using the full path when importing binary files.

```
MODEL_PARAMS_PATH = '{}/model'.format(os.path.dirname(os.path.realpath(__file__)))
```
  

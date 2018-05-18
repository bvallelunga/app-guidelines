# App Guidelines

This document is meant to help maintainers prepare their apps for the Doppler marketplace. It includes importing guidelines as well as a list of hard dependencies and app restrictions.


# Enviroment

All apps will be running in a [Python3](https://docs.python.org/3/) environment. The following packages will be installed by default:  - "requests",
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

### Importing Code
In order for relative imports to work properly, you must:
  1. add all files, with relative imports, to the `PYTHON PATH`
  2. remove explicit relative imports
``` py
# Add Current Directory to Path
import sys, os
sys.path.append(os.path.dirname(os.path.realpath(__file__)))

# Import Local Files
from encoder import Model
from utils import load_model_params
```

### Importing Binary Files
We recommend using the full path when importing binary files.

```
BASE_PATH = os.path.dirname(os.path.abspath(__file__))
MODEL_PARAMS_PATH = os.join.path(BASE_PATH, 'model')
```
  

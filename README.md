<div align="center">
  <a href="https://dagshub.com"><img src="dagshub_github.png" width=600 alt=""/></a><br><br>
</div>

[![Discord](https://img.shields.io/discord/698874030052212737)](https://discord.com/invite/9gU36Y6)
[![Tests](https://github.com/dagshub/client/actions/workflows/python-package.yml/badge.svg?branch=master)](https://github.com/DAGsHub/client/actions/workflows/python-package.yml)
[![pypi](https://img.shields.io/pypi/v/dagshub.svg)](https://pypi.python.org/pypi/dagshub)
[![Updates](https://pyup.io/repos/github/DAGsHub/client/shield.svg)](https://pyup.io/repos/github/DAGsHub/client/)
[![License](https://img.shields.io/pypi/l/dagshub)](/LICENSE)
<a href="https://twitter.com/TheRealDAGsHub" title="DagsHub on Twitter"><img src="https://img.shields.io/twitter/follow/TheRealDAGsHub.svg?style=social"></a>

# DagsHub Python client libraries
Use DagsHub to create reproducible versions of your data science research project, 
allow others to understand your project, and to contribute back to it.

DagsHub is built firmly around open, standard formats for your project. In particular:
* git
* [DVC](https://github.com/iterative/dvc)
* Standard data formats like YAML, JSON, CSV

Therefore, you can work with DagsHub regardless of your chosen programming language or frameworks. 

__This client library is meant to help you get started quickly in Python__, but it's purely optional - 
the data formats are very simple and you can choose to work with them directly. 



## Installation
```bash
pip install dagshub
```

## Guide
You can learn more by completing our short [tutorial](https://dagshub.com/docs/experiment-tutorial/overview/) or reading the [docs](https://dagshub.com/docs)

## Basic Usage
```python
from dagshub import dagshub_logger, DAGsHubLogger

# As a context manager:
with dagshub_logger() as logger:
    # Metrics:
    logger.log_metrics(loss=3.14, step_num=1)
    # OR:
    logger.log_metrics({'val_loss': 6.28}, step_num=2)
    
    # Hyperparameters:
    logger.log_hyperparams(lr=1e-4)
    # OR:
    logger.log_hyperparams({'optimizer': 'sgd'})
    

# As a normal Python object:
logger = DAGsHubLogger()
logger.log_hyperparams(num_layers=32)
logger.log_metrics(batches_per_second=100, step_num=42)
# ...
logger.save()
logger.close()
```

## Integrations with ML frameworks
The [basic DagsHub logger](https://github.com/DAGsHub/client/blob/master/dagshub/logger.py) is just plain Python, and requires no specific framework.

However, for convenience, we include some integrations with common ML frameworks, which can __just work__ right out of the box, 
without having to write any logging code on your own:

* [pytorch-lightning](https://github.com/DAGsHub/client/tree/master/dagshub/pytorch_lightning) – supports version 1.4.0 or higher
* [fastai v2](https://github.com/DAGsHub/client/tree/master/dagshub/fastai)
* [keras](https://github.com/DAGsHub/client/tree/master/dagshub/keras)
* More - soon to come!


---

Made with 🐶 by [DagsHub](https://dagshub.com/).

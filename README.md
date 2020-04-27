# Data Generation Process Modeling for Activity Recognition

This repository is the official implementation of [Data Generation Process Modeling for Activity Recognition](/doc/DataGenerationModelingForActivityRecognition.pdf).

<p align="center">
  <img src="https://user-images.githubusercontent.com/49691301/80390776-2e8e0300-88ad-11ea-9b1b-4a00bbb98e52.jpg" width=800px/>
</p>

**Figure:** The dynamics of body movements are often driven by large and intricate low-level interactions involving various body parts. These dynamics are part of an underlying data generation process. We propose to derive a model of the data generation process by reframing the problem as an exploration of the space of architectures responsible of relating together the data sources which are placed on different body parts.


## Requirements

To install requirements:

```setup
pip install -r requirements.txt
```

### Prerequisites
* `numpy`
* `TensorFlow`
* `scikit-optimize`
* `fanova` to install, please follow the steps [here](https://automl.github.io/fanova/install.html)

If you are using `pip` package manager, you can simply install all requirements via the following command(s):

    python -m virtualenv .env -p python3 [optional]
    source .env/bin/activate [optional]
    pip3 install -r requirements.txt

### Installing
#### Get the dataset
1. You can get the preview of the SHL dataset (`tar.gz` files) from [here](http://www.shl-dataset.org/download/#shldataset-preview). Make sure to put the downloaded files into `./data/` folder.
2. Run `extract_data.sh` script which will extract the dataset into `./generated/tmp/` folder.

## Running
### Bayesian optimization
In order to run Bayesian optimization, you can issue the following command:

    python3 shl-nas.py --run bayesopt
    
Additionally, you can specify a subset of the data generators you want to apply Bayesian optimization on as follows:

    python3 shl-nas.py --run bayesopt --position {bag|torso|hand|hips}

### Functional analysis of variance
You can find a complete notebook showing the functional analysis of variance inside `notebooks/` folder.

## Results

Our model achieves, noticeably, the following performance on different activity recognition datasets:

| Dataset | wo-DGP | w-HExp | w-DGP  |
| --------|--------| ------ |------  |
| USC-HAD | 72.1%  | 75.38% | 89.33% |
| HTC-TMD | 74.4%  | 77.16% | 78.9%  |
| US-TMD  | 71.32% | 80.28% | 83.64% |
| SHL     | 70.86% | 77.18% | 88.7%  |

- **wo-DGP**: without incorporating the data generation process
- **w-HExp**: incorporating the data generation process constructed by human experts
- **w-DGP**: incorporating the data generation process derived using our approach

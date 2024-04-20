# Mixture of Enhanced Visual Features (MEVF)

![Overview of bilinear attention networks](misc/Diagram_vqa_final.png)

### Prerequisites

[VQA-RAD dataset](https://www.nature.com/articles/sdata2018251#data-citations)
Please install dependencies by running following command:
```
pip install -r requirements.txt
```

### Preprocessing

All data should be downloaded via [link](https://vision.aioz.io/f/777a3737ee904924bf0d/?dl=1). The downloaded file should be extracted to `data_RAD/` directory.

The **MAML** model `data_RAD/pretrained_maml.weights` is trained by using official source code [link](https://github.com/cbfinn/maml).
The **CDAE** model `data_RAD/pretrained_ae.pth` is trained by code provided in `train_cdae.py`. 

The result json file can be found in the directory `results/`.
![Accuracy of the model with different customisations](misc/results_vqa.png)

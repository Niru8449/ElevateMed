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

### Training
Train MEVF model with Stacked Attention Network (SAN)
```
$ python3 main.py --model SAN --use_RAD --RAD_dir data_RAD --maml --autoencoder --output saved_models/SAN_MEVF
```
Train MEVF model with Bilinear Attention Network (BAN)
```
$ python3 main.py --model BAN --use_RAD --RAD_dir data_RAD --maml --autoencoder --output saved_models/BAN_MEVF
```
The training scores will be printed every epoch.

### Pretrained models and Testing
In this repo, we include the pre-trained weight of MAML and CDAE which are used for initializing the feature extraction modules.

The **MAML** model `data_RAD/pretrained_maml.weights` is trained by using official source code [link](https://github.com/cbfinn/maml).

The **CDAE** model `data_RAD/pretrained_ae.pth` is trained by code provided in `train_cdae.py`. For reproducing the pretrained model, please check the instruction provided in that file.

For `SAN_MEVF` pretrained model. Please download the [link](https://vision.aioz.io/f/fdc6572bc26f4dd684f4/?dl=1) and move to `saved_models/SAN_MEVF/`. The trained `SAN_MEVF` model can be tested in VQA-RAD test set via:
```
$ python3 test.py --model SAN --use_RAD --RAD_dir data_RAD --maml --autoencoder --input saved_models/SAN_MEVF --epoch 19 --output results/SAN_MEVF
```
For `BAN_MEVF` pretrained model. Please download the [link](https://vision.aioz.io/f/882e8a6f32704013943d/?dl=1) and move to `saved_models/BAN_MEVF/`. The trained `BAN_MEVF` model can be tested in VQA-RAD test set via:
```
$ python3 test.py --model BAN --use_RAD --RAD_dir data_RAD --maml --autoencoder --input saved_models/BAN_MEVF --epoch 19 --output results/BAN_MEVF
```
The result json file can be found in the directory `results/`.


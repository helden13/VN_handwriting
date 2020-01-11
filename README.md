# Cinamon AI Challenge - Handwritten text recognition 

_minhdh, HCMC 2019_

The data can be download at [Cinnamon AI Challenge](https://drive.google.com/drive/folders/1Qa2YA6w6V5MaNV-qxqhsHHoYFRK5JB39)

Please unzip the data in this folder structure to run the code:

```
|--data/
|----raw/
|------0825_DataSamples_1/
|------0916_DataSamples_2/
|------1015_Private_Test/
|--src/
```

The solution is mainly based on [Arthur Flor's Solution](https://medium.com/@arthurflor23/handwritten-text-recognition-using-tensorflow-2-0-f4352b7afe16) on another datasets. Also many thanks to [@pbcquoc](https://github.com/pbcquoc), the winner on the challenge, for his [sharing](https://pbcquoc.github.io/vietnamese-ocr/).

## Getting start

### Data preprocessing

Move to `/src` and run this to transform the data

```
python transform.py --path ../data/raw/0916_DataSamples_2 --type train --transform
python transform.py --path ../data/raw/1015_Private_Test --type test --transform
```

Two new folders `train/` and `test/` and two `json` files containing the labels will be created in `data/`. The folders `train/` and `test/` contain the preprocessed images. You can also run

```
python transform.py --path ../data/raw/0825_DataSamples_1 --type val --transform
```

to create a `val/` set with 15 samples.

**Showing examples**

```
python transform.py --type [train or test or val] --sample
```
This will open a OpenCV window showing the preprocessed images (50 samples) one by one. The labels of the images will be shown in the terminal window.

### Model training

To start training the model, run:

```
python train.py --train
```

For testing, run:

```
python train.py --test --path [path to the test images]
```

Example `python3 train.py --test --path ../data/test`. Then predicted texts and the ground true texts will be stored in `predictions_text.txt`.
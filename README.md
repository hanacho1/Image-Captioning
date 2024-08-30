## Image captioning
This project is an example of retraining and testing an image captioning model based on the Show, Attend, and Tell model.

## Table of Contents
1. [Overview](#overview)
2. [Installation](#installation)
3. [Training](#training)
4. [Testing](#testing)

## Overview
This project involves the following key steps:
1. Dataset Download
I utilized the Flickr 8k Dataset from Kaggle.[flickr8k dataset](https://www.kaggle.com/datasets/adityajn105/flickr8k)
2. Data Preprocessing
3. Model Training and Inference

## Install
```bash
!pip install -r requirements.txt 
```

## Training
Before starting the training process, data preparation and conversion are necessary.
1. Preprocessing
```bash
!python create_input_files.py
```
2. Model training
```bash
!python train.py --data_folder /content/drive/MyDrive/a-PyTorch-Tutorial-to-Image-Captioning/data/Flicker8k_Dataset --data_name flickr8k_5_cap_per_img_5_min_word_freq --save_name 'caption_model_flickr8k' --batch_size 8 --workers 1 --epochs 10 --encoder_lr 1e-4 --decoder_lr 4e-4 --grad_clip 5. --fine_tune_encoder --dropout 0.5
```

## Testing
Test images are saved in the 'test_result' folder.  
["The trained model can be downloaded from Google Drive."](https://drive.google.com/drive/folders/11vJ9A_AaDPN6FBFdYcmcY1MUfR5t_l8j?usp=sharing)
```bash
!python caption.py --img='/content/drive/MyDrive/a-PyTorch-Tutorial-to-Image-Captioning/test/test1.jpg' --model='/content/drive/MyDrive/a-PyTorch-Tutorial-to-Image-Captioning/BEST_checkpoint_flickr8k_5_cap_per_img_5_min_word_freq.pth.tar' --word_map='/content/drive/MyDrive/a-PyTorch-Tutorial-to-Image-Captioning/data/Flicker8k_Dataset/WORDMAP_flickr8k_5_cap_per_img_5_min_word_freq.json' --beam_size=5
```

| query | ![Query Image](https://github.com/hanacho1/Image-Captioning/blob/main/test_result/test2.jpg) |
|-------|------------------------------------------------------------|
| result| ![Result Image](https://github.com/hanacho1/Image-Captioning/blob/main/test_result/test2_output.png) |


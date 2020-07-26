# PLR-OSNet for  Person Re-identification

Learning Diverse Features with Part-Level Resolution for Person Re-Identication, PRCV2020.

## Introduction

- The code is developed based on Pytorch framework.
- Our proposed method has achieved the state-of-the-art results on the three popular person Re-ID datasets.[[link]](https://paperswithcode.com/paper/learning-diverse-features-with-part-level)

## Results(without re-rank)
|                  | rank-1 | mAP  |
| :----------------| :----: | :--: |
| Market1501       | 95.6  	| 88.9 |
| DukeMTMC         | 91.6   | 81.2 |
| CUHK03-Labeled   | 84.6   | 80.5 |
| CUHK03-Detected  | 80.4   | 77.2 |

## Get Stared
1. clone code to your own folder

   ```
   git clone https://github.com/AI-NERC-NUPT/PLR-OSNet.git
   ```
   
2. Install prerequisites

   - pytorch >=1.1.0
   - torchvision >= 0.3.0
   - yacs >= 0.1.6
   - tb-nightly>=2.0.0
   - Cython >= 0.29.12
   - pytorch-ignite>=0.1.2
   
3. Prepare Datasets
   
    You can create a directory to store reid datasets under this repo via
   
   ```bash
   cd PLR-OSNet
   mkdir data
   ```
   
   (1) Market1501
   
   The data structure would like:
   
   ```bash
   data
       market1501
           Market-1501-v15.09.15
               bounding_box_train/
               bounding_box_test/
               query/
   ```
   
   (2) DukeMTMC-ReID
   
   The data structure would like:
   
   ```bash
   data
       dukemtmc-reid
           DukeMTMC-reID
               bounding_box_train/
               bounding_box_test/
               query/
   ```
   
   (3) CUHK03
   
   The data structure would like:

   
     ```bash
   data 
       cuhk03
           CUHK03_labeled
               bounding_box_train/
               bounding_box_test/
               query/
           CUHK03_detected
               bounding_box_train/
               bounding_box_test/
               query/
     ```

## Train

**scripts/train.sh**

```
python ../main.py \
	--config-file ../configs/im_plr_osnet_triplet_cuhk03_256x128.yaml \
	--transforms random_flip random_erase\
	--root ./data/ \
	--gpu-devices 4
```

The above `train.sh` is used for training cuhk03 dataset. You can modify the config file to train other datasets. 

```
market1501 --> configs/im_plr_osnet_triplet_market1501_256x128 .yaml
dukemtmcreid --> configs/im_plr_osnet_triplet_dukemtmcreid_256x128 .yaml
```

Finally ,you can run `train.sh` file for training.

```
cd scripts/train.sh
bash train.sh
```

## Datasets

- Market1501 

  <https://www.cvfoundation.org/openaccess/content_iccv_2015/papers/Zheng_Scalable_Person_Re-Identification_ICCV_2015_paper.pdf>

- DukeMTMC-reID

  https://arxiv.org/abs/1701.07717

- CUHK03 

  https://www.cvfoundation.org/openaccess/content_cvpr_2014/papers/Li_DeepReID_Deep_Filter_2014_CVPR_paper.pdf
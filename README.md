# LMT++: Adaptively Collaborating LLMs with Multi-specialized Teachers for Continual VQA in Robotic Surgical Videos


## Introduction
* This repository contains the PyTorch implementation for our paper "LMT++: Adaptively Collaborating LLMs with Multi-specialized Teachers for Continual VQA in Robotic Surgical Videos", which has been submitted to IEEE Transactions on Medical Imaging (currently under major revision).

* For the original ICRA 2024 implementation, please refer to our conference version repository, see [here](https://github.com/yuyangdu01/LLM-CL-VQA).

* [Our demo video](https://youtu.be/sSCRLyY355c)
[![](https://i.ytimg.com/vi/sSCRLyY355c/maxresdefault.jpg)](https://youtu.be/sSCRLyY355c "")


## Data Preparation
* For datasets, we use [EndoVis17](https://arxiv.org/abs/2305.11692), [EndoVis18](https://arxiv.org/abs/2206.11053), [DAISI-VQA](DAISI_VQA). 

* How we constructed the DAISI-VQA dataset:

  The original DAISI dataset contains images and instructional texts of various surgical procedures on different organs. Each procedure consists of multiple images with corresponding instructional texts. We first clean the original DAISI dataset by deleting irrelevant images and confusing descriptions. We then generate QA pairs according to the text description for each image. Eventually, we obtained a new VQA dataset referred to as DAISI-VQA. Please see our paper for details about using in-context learning (ICL) for QA pair generation.

* Training and test data split

   EndoVis17: a VQA dataset obtained from 5 surgical videos. We use 376 QA pairs in the training set and 96 QA pairs in the testing set.
  
   EndoVis18: a VQA dataset obtained from 14 surgical videos. We use 9014 QA pairs in the training set and 2769 QA pairs in the testing set.
  
   DAISI-VQA: in total 545 QA pairs in the dataset. 80% of the data is used in the training set, while the rest 20% is used in the testing set.

## Environment & Setup
* See the environment and setups in our [Tutorial in Jupyter Notebook](t4_code/OurMethod_GitHub_OpenSource.ipynb).
  
## Training
* We train the model under a continual learning (CL) framework.

* Step 1: In time slot #1, we train the model with EndoVis17 dataset.

* Step 2: In time slot #2, we train the model with EndoVis18 dataset.
  
* Then in time slot #3, we train the model with DAISI-VQA.

## Testing
* After the training in time slot #1, we test the model on EndoVis17.

* After the training in time slot #2, we test the model on EndoVis17 and EndoVis18 to see if the new model forgets the knowledge in EndoVis17.

* After the training in time slot #3, we test the model on EndoVis17 EndoVis18, and DAISI-VQA to see if the new model forgets the knowledge in EndoVis17 and EndoVis18.


## Citation
If this repository is useful for your research, please cite:
```
@inproceedings{chen2024llm,
  title={LLM-Assisted Multi-Teacher Continual Learning for Visual Question Answering in Robotic Surgery},
  author={Chen, Kexin and Du, Yuyang and You, Tao and Islam, Mobarakol and Guo, Ziyu and Jin, Yueming and Chen, Guangyong and Heng, Pheng-Ann},
  booktitle={2024 IEEE International Conference on Robotics and Automation (ICRA)},
  year={2024},
  organization={IEEE}
}
```
### Questions
For further questions about the code or the paper, please feel free to raise an issue.


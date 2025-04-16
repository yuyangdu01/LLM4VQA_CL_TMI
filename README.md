# LMT++: Adaptively Collaborating LLMs with Multi-specialized Teachers for Continual VQA in Robotic Surgical Videos


## Introduction
* This repository contains the PyTorch implementation for our paper "LMT++: Adaptively Collaborating LLMs with Multi-specialized Teachers for Continual VQA in Robotic Surgical Videos", which has been submitted to IEEE Transactions on Medical Imaging (currently under major revision).

* For the original ICRA 2024 implementation, please refer to our conference version repository, see [here](https://github.com/yuyangdu01/LLM-CL-VQA).

* [Our demo video](https://youtu.be/sSCRLyY355c)
[![](https://i.ytimg.com/vi/sSCRLyY355c/maxresdefault.jpg)](https://youtu.be/sSCRLyY355c "")


## Data Preparation
* For datasets, we use [EndoVis17](https://arxiv.org/abs/2305.11692), [EndoVis18](https://arxiv.org/abs/2206.11053), [DAISI-VQA](https://github.com/yuyangdu01/LLM-CL-VQA/tree/main/DAISI_VQA), [LRSP-VQA](LRSP_VQA)

* How we constructed the LRSP-VQA dataset:

  The LRSP-VQA dataset was built using 36 robotic surgery videos from YouTube, segmented into 150 phase-aligned clips to maintain instrument consistency. From these, over 10,000 frames were extracted and paired with corresponding transcribed surgical narrations. Using GPT-3.5, QA pairs were automatically generated from these textual descriptions (following DAISI-VQA's methodology), followed by expert validation to ensure accuracy.


* Training and test data split

   EndoVis17: a VQA dataset obtained from 5 surgical videos. We use 376 QA pairs in the training set and 96 QA pairs in the testing set.
  
   EndoVis18: a VQA dataset obtained from 14 surgical videos. We use 9014 QA pairs in the training set and 2769 QA pairs in the testing set.
  
   DAISI-VQA: in total 545 QA pairs in the dataset. 80% of the data is used in the training set, while the rest 20% is used in the testing set.

   LRSP-VQA: in total 1077 QA pairs in the dataset. 80% of the data is used in the training set, while the rest 20% is used in the testing set.

## Environment & Setup
* See the environment and setups in our [Tutorial in Jupyter Notebook](T4_code/Our_Method.ipynb).
  
## Training
* We train the model under a continual learning (CL) framework.

* Step 1: In time slot #1, we train the model with EndoVis17 dataset.

* Step 2: In time slot #2, we train the model with EndoVis18 dataset.

* Step 3: In time slot #3, we train the model with DAISI-VQA dataset.
  
* Then in time slot #4, we train the model with LRSP-VQA.

## Testing
* After the training in time slot #1, we test the model on EndoVis17.

* After the training in time slot #2, we test the model on EndoVis17 and EndoVis18 to see if the new model forgets the knowledge in EndoVis17.

* After the training in time slot #3, we test the model on EndoVis17 EndoVis18, and DAISI-VQA to see if the new model forgets the knowledge in EndoVis17 and EndoVis18.

* After the training in time slot #4, we test the model on EndoVis17 EndoVis18, DAISI-VQA and LRSP-VQA to see if the new model forgets the knowledge in EndoVis17，EndoVis18 and DAISI-VQA.


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


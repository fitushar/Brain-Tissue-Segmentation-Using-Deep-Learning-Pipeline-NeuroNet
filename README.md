# Brain Tissue Segmentation Using NeuroNet With Different Pre-processing Techniques
This Repository is for the MISA Course final project which was Brain tissue segmentation. we adopt NeuroNet which is a comprehensive brain image segmentation tool based on a novel multi-output CNN architecture which has been trained and tuned using IBSR18 data. If you use this model in your work please refer to the Original NeuroNet Paper and DLTK at https://github.com/DLTK/models/tree/master/ukbb_neuronet_brain_segmentation

If our work help in your task or project please site the work at https://ieeexplore.ieee.org/document/8858515 (Pre-print https://arxiv.org/abs/1904.00068 ). This work is been accepted for presented at 3rd International Conference on Imaging, Vision & Pattern Recognition (IVPR),2019.

# Citation
```ruby
F. I. Tushar, B. Alyafi, M. K. Hasan and L. Dahal, "Brain Tissue Segmentation Using NeuroNet With Different Pre-processing Techniques," 2019 Joint 8th International Conference on Informatics, Electronics & Vision (ICIEV) and 2019 3rd International Conference on Imaging, Vision & Pattern Recognition (icIVPR), Spokane, WA, USA, 2019, pp. 223-227.
```
# Overview
Automatic segmentation of MRI brain images is one of the vital steps for quantitative analysis of brain for further inspection. Since manual segmentation of brain tissues (white matter (WM), gray matter (GM) and cerebrospinal fluid (CSF)) is a time-consuming and tedious task that engages valuable human resources, hence,  automatic brain tissue segmentation draws an enormous amount of attention in medical imaging. In this project, NeuroNet has been adopted to segment the brain which uses Residual Network (ResNet) in encoder and Fully Convolution Network (FCN) in the decoder. To achieve the best performance, various hyper-parameters have been tuned, while, network parameters (kernel and bias) were initialized using the NeuroNet pre-trained model. Different pre-processing pipelines have also been introduced to get best a robust trained model. The performance of the segmented validation images were measured quantitatively using Dice Similarity Co-efficient (DSC) and were reported in the best case as 0.8986±0.0174 for CSF, 0.9412 ± 0.0086 for GM, and 0.9335 ± 0.0166 for WM. We worked out that keeping the original patch size and using histogram preprocessing with 4000 steps had the highest achievable performance.
![model Architecture](https://github.com/fitushar/Brain-Tissue-Segmentation-Using-Deep-Learning-Pipeline-NeuroNet/blob/master/Images/architecture.PNG)

In this work two different pre-processing pipelines were implemented. To see the effect on the performance of the deep CNN with different pre-processing scheme. Figure  below shown the overview of the pre-processing pipelines.

![Pre_Processing pipeline](https://github.com/fitushar/Brain-Tissue-Segmentation-Using-Deep-Learning-Pipeline-NeuroNet/blob/master/Images/Preprocessing_pipelines.PNG)

![Pre_Processing pipeline](https://github.com/fitushar/Brain-Tissue-Segmentation-Using-Deep-Learning-Pipeline-NeuroNet/blob/master/Images/example_preprpcessed.png)

# How to Run the Code
To run and model and re-produce the best results thins steps need to perform.

1.	Run Notebook “MISA_Project_PreProcesing_Step(1)_Registration.ipynb” to perform the registration of the Volumes to MNI template.
2.	Run Notebook “MISA_Project_PreProcesing_Step(2)_Normalization.ipynb” to Perform Preprocessing (Pre-processing pipeline-2 mentioned in report) and to create the excel files that containing the path of the training , validation and testing data. Network Read the data from excel files that have the path of the data.
3.	Folder “Model” Contain the pretrained model, Download the Weights from here https://goo.gl/VmhGYc
4.	To run the code please the command “python train.py --config config_spm_tissue.json”
5.	In the file “config_spm_tissue.json” to maintain and configure model

      model_path": put ur model weights path (spm_tissue folder)

6.	To prepare the Testing Data and After segmentation to bring it back to the original spacing use this Notebook “PreparingTestingData.ipynb”
7.	To run the testing ““python deploy.py --config config_spm_tissue.json””
8.	Finaly to Compute the Dice and Box plot Run the “Evaluation_MISA_Project.ipynb”


![dsc](https://github.com/fitushar/Brain-Tissue-Segmentation-Using-Deep-Learning-Pipeline-NeuroNet/blob/master/Images/5_2.png)
![overlay](https://github.com/fitushar/Brain-Tissue-Segmentation-Using-Deep-Learning-Pipeline-NeuroNet/blob/master/Images/overlay_val14.png)



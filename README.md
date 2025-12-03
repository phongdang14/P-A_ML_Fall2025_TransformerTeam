# Course: Machine Learning (Fall 2025)
Instructor: Dr. Michela Negro

The wiki page of the course can be found via this [link](https://github.com/nmik/P-A_ML_Fall2025/wiki).

## Team: Transformer
Members: Valarie Milton, Phong Dang (owner of this repository), Trang Huynh, Eric Borowski, Nageeb Zaman

## Objecttive
We perform supernova classifications using three different ML algorithms:
- Multi-layer perceptron neural network (MLP)
- Support vector machine (SVM)
- Boosted decision tree (BDT)

## Concluding remarks
- Data preprocessing is very important, which in our case is necessary to handle outliers.
- Model 2 outperforms Model 1 even though it has less data. Probably because it has more features.
- BDT classifier is the most effective, which agrees with the paper. Meanwhile, SVM classifier does not work very well.
- Downsampling does not improve classification. The reason might be that our downsampling process results in a too small dataset, making it difficult for the classifiers to learn.
- In Model 2, we did a better job than the paper. Yay 😎!

## Acknowledgement
This project was largely motivated by the work of Michelle Lochner et al. (ApJ Supplement Series, 225:31, 2016), which can be accessed via this [link](https://iopscience.iop.org/article/10.3847/0067-0049/225/2/31).

## Repository structure
- The main notebook is ```Team transformer.ipynb```, which contains the main analysis and results of the project. It was run on Google Colab, thus at the top, you can see it is mounted to Google Drive. When you run this notebook locally, two changes need to be made as instructed in the notebook.
- Folder ```data/``` contains all the data used for the training.
- Folder ```supplement/``` contains all the draft notebooks that trained the two feature extraction models seperately for each classifier. 

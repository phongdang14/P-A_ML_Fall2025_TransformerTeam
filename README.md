# Course: Machine Learning (Fall 2025)
Instructor: Dr. Michela Negro

The wiki page of the course can be found via this [link](https://github.com/nmik/P-A_ML_Fall2025/wiki).

## Team: Transformer
Members: Valarie Milton, Phong Dang (owner of this repository), Trang Huynh, Eric Borowski, Nageeb Zaman

## Objective
We perform supernova classifications using three different ML algorithms:
- Multi-layer perceptron neural network (MLP)
- Support vector machine (SVM)
- Boosted decision tree (BDT)

[EB WORKING HERE]
## Motivations
- why do we care about classfiying SNe

## Caveats 
- treat light curves in different bands as discrete events (4500 * 5 light curves) but we know that many of these light curves in different bands correspond to the same SN (~4500 real events)
  - probably affects accuracy of classification (if more r' band light curves go into creating the trained model, it will be weighted more heavily to that light curve morphology) **show plot of well-sampled light curve with slightly different evolutions in different bands**
  - could be valuable to include color information in the model, maybe more physics to discover (beyond scope of this work)
[EB WORKING HERE]

## Data Source
- [Open Supernova Catalog Database](https://iopscience.iop.org/article/10.3847/1538-4357/835/1/64):
  - We obtained all observed SNe discovered from pre-1990 to 2024 [AstroCats](https://github.com/astrocatalogs/astrocats)
- [Center for Astrophysics Supernova Data Archive](https://lweb.cfa.harvard.edu/supernova/SNarchive.html):
  - 64 stripped-envelope CCSNe from [Bianco et al. (2014)](https://ui.adsabs.harvard.edu/abs/2014ApJS..213...19B/abstract)
  - (60 Type II Supernova Light Curves and Spectra From the CfA) from [Hicken M., et al. (2017)](https://iopscience.iop.org/article/10.3847/1538-4365/aa8ef4)

## Feature extraction
### Model 1:
- 5 fitting parameters ($`A, \phi, \sigma, k, \psi`$) per filter band by [Newling et al. (2011)](https://academic.oup.com/mnras/article/414/3/1987/1035457)
  $$ F(t) = A (\frac{t-\phi}{\sigma})^k \exp(-\frac{t-\phi}{\sigma}) e^k $$
  
### Model 2:
- 6 fitting parameters ($`A, B, t_0, t_1, T_{fall}, T_{rise}`$) per filter band by [Karpenka et al. (2013)](https://academic.oup.com/mnras/article/429/2/1278/1038192)
  
$$F(t) = A[1+B(t-t_1)^2] \frac{\exp[-(t-t_0)/T_{\text{fall}}]}{1+\exp[-(t-t_0)/T_{\text{rise}}]} $$

## Concluding remarks
- Data preprocessing is very important, which in our case is necessary to handle outliers and the extreme difference between the scales of the features.
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

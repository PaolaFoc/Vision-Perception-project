# Vision & Perception project
Student: Paola Fochetti, 1759100 \
The main goal of the project is to give a face to a character's book by building a gan able to generate faces starting from a textual description. \
[Here](https://drive.google.com/drive/folders/1w2ErKRgulfJaPdxAECsFwf1IOHyd0qNn?usp=share_link) you can find the drive folder where tthe code was developed.

## Datasets
Three datasets are used, two are image datasets and are used for training in the first phase, while the thirsd one is a textual dataset used in the second phase.
1. [Flickr](https://www.kaggle.com/datasets/arnaud58/flickrfaceshq-dataset-ffhq) \
It contains 52000 images of size 512x512
2. [CelebA](https://drive.google.com/drive/folders/1YRRaC3LWLHorVhFNJPzVqLrUlA10eLEJ) \
It contains 30000 images
3. [Face2text](https://zenodo.org/record/6583553/files/face2text_v2.0.zip?download=1) \
It's a textual dataset. It contains faces' descriptions that are more detailed than those contained in CelebA.

## Approach
The project can be divided into two phases:
1. building a gan that generate faces from random noise: \
the structure chosen is a DCgan. Generator and discriminator are build following this [article](https://arxiv.org/pdf/1511.06434.pdf) and are trained in an adversarial modality. 
2. inserting the textual description as input for the generator:\
in this phase only the generator is trained, using as loss the similarity score between the generated immage and the associated caption. The score is provided using the pretrained CLIP architecture.

## Code and relative folder
The file [gan.py](https://github.com/PaolaFoc/Vision-Perception-project/blob/main/gan.py) contains all the code developed for the project. 
The original code was developed in a colab notebook, that can be found in this [drive folder](https://drive.google.com/drive/folders/1w2ErKRgulfJaPdxAECsFwf1IOHyd0qNn?usp=share_link).\
The folder contains:
1. the three datasets *FLickr*, *CelebA* and *Face2tex*t;
2. *AdversarialTrainImages*, that contains all the images generated from a fixed noise at each epoch of adversarial training;
3. *AdversarialTrainEpochs*, that contains the networks' weights and related data for each epoch of adversarial training;
4. *ClipTrainImages*, that contains all the images generated from a fixed caption at each epoch of training in the second phase;
5. *ClipTrainEpochs*, that contains the networks' weights and related data for each epoch of training in the second phase;
6. *gan.ipynb*, the original, and runnable, notebook in which the code was developed. To run the code you need to add a shortcut to the home directory of you drive.

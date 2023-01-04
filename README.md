# RESNET50GeoGuessr
RESNET50 trained to guess countries based on Google street view images from a Kaggle dataset

This was a final project for CS229: Machine Leaning at Stanford. Project partners were Jeffrey Heo and Eric Werner. 

Geoguessr is an online game where the player tries to guess the geographic location of a Google street-view image. Points are awarded proportional to the precision of the guess, so a close guess earns more points than a far-off guess. For this project, we sought to create a computer vision (CV) model to play a modified version of Geoguessr where, instead of guessing the coordinates of a given street view image, the model would learn to predict the country of the location. Our project tackled a multi-class image classification task where the input to our algorithm is a 224 x 224 RGB screenshot of a geoguessr question.

We used a pretrained ResNet-50 to take the image input and output a predicted country label, using both feature extraction and finetuning. Unlike the actual Geoguessr objective, which would be more closely modeled as a regression task of pinpointing exact geographic coordinates, our project classifies countries based on underlying traits of a country, such as climate, foliage, natural landscapes, street signs and road markings. Street views of heavily-urbanized and population-dense Korea, for example, will differ significantly with that of Dutch cities built around canals. The prospect of a neural network learning the nuances of street views of different countries inspired us to build this project.

Our model achieved 40.3% accuracy on the test set from feature extraction and 72.5% accuracy on the test set from fine tuning. 

We designed a custom loss function that includes both the Cross Entropy Loss (for catagorization error) and the Haversine distance (distance on the globe between the guessed country and the true country). The Haversine term punishes far away guesses more than guesses that are closer to the true country. We ran hyperparameter training the weightings of the Haversine distance to obtain an optimal score on the validation set. 



Link to full paper: https://docs.google.com/document/d/169pKD2p0KkXbdJ4wBnowt5giBIMCu5g8JDN3ZZMxX6c/edit?usp=sharing

# Dashtoon-assignment
## Neural Style Transfer (Dashtoon Assignment IIT KGP)


---


**Name:** Tuhin Subhra De

**Roll:** 19CE36007

---
Dataset used: https://www.kaggle.com/datasets/duttadebadri/image-classification

Information about dataset: The dataset (size = 3 GB) contains several images belonging to categories like Travel, Food, Art and Architecture.

## Procedure (PyTorch):
1. We train a vanilla Convolutional Neural Network (CNN) model from scratch on the dataset. The model is a classifier which classifies a given sample into 4 different classes with some probablity. This way we can obtain the intermediate features from each of the images when passed through the model.
2. For training the CNN classifer we use Cross-Entropy loss function and train it for 10 epochs. The final loss for trainset and testset are 0.9 and 0.89 respectively.
3. We define two distances, one for the content Dc and one for the style Ds. Dc measures how different the content is between two images while Ds measures how different the style is between two images. Then, we take a third image, the input, and transform it to minimize both its content-distance with the content-image and its style-distance with the style-image.

### Style Image
We construct a feature space on top of each layer's filter responses to capture the style content of the input image. This feature space is based on the spatial correlations among the filter responses across the feature maps. The filter correlations at different layers reflect the texture information of the input image. This allows us to create images that match the style of a given image at different scales, while ignoring the global structure. We call this multi-scale representation the style representation.

### Content Image
The image is represented differently at different levels of the convolutional neural network. The deeper we go into the network, the more the representations focus on the structural features or the content of the image rather than the pixel details. We can use the feature maps of each layer to reconstruct the images and see how they are represented. The reconstruction from the lower layer will look exactly like the original image. However, the reconstruction from the higher layer will only show the high-level content and that is why we call the feature responses from the higher layer as the content representation.

We then run the styling process for 800 steps minimizing the content and style loss. The final losses are *Style Loss : 44892.402344 Content Loss: 127.815811*


**Two selected images:**


![image](https://github.com/Gituhin/Dashtoon-assignment/assets/75536336/7ba32ca3-b810-410b-89e2-c19152927fb2)

![image](https://github.com/Gituhin/Dashtoon-assignment/assets/75536336/a967ab6e-395d-4aac-a686-338956897fb4)


**Output Image**:

![image](https://github.com/Gituhin/Dashtoon-assignment/assets/75536336/65dcc901-3965-4de4-92d0-79eced6405fa)


### Limitations and Improvements:
We observe that there is a slight style transfer between the images. It is not much prominent. This can be due to that fact of limited capacity of base CNN model. This can be improved by fine training the base model and increasing the number of convolutional layers for much better feature extraction.

# Satellite_Image_Classification_By_CNN

For satellite image classification, I use a convolutional neural network (cNN) architecture. I collected the data from a publicly available data source. First of all, I preprocess the data and clean it, then I convert the data source into a CSV file. Then I split the data set between 80% for training and 20% for testing. After splitting, I run the deep learning model using TensorFlow and Keras, especially in CNN architecture. I use the convolutional 2D architecture and max pulling for this model. For the activation function, I use Relu in the deep neural network model and the softmax activation function in the output layer. I ran the DNN model only for five epochs, and my output accuracy was around 85%. I find different things in the data and make some visualizations. I added all the visualizations to the Readme.MD folder. I found the loss and accuracy visualization for training and validation split, and then I found some other things from the data, like wanting to make a confusion matrix for this data set. In the advanced prediction model, I want to create a system where if we input data from a URL, we will find the output of the image using our classification model.


Findings of our Model :
======================= 



|Dataset values   |Dataset time series |Dataset faceted distributions  |
|:---------------:  |:----------------:|:------------------------:|
|![Dataset_values]|![Dataset_time_series]|![Dataset_faceted_distributions]  |


|Dataset distributions |categorical distributions| Accuracy Graph |
|:-------------------:|:-----------------------:|:---------------:|
|![Dataset_distributions]|![categorical_distributions]|![Accuracy_Graph]|


|Loss Graph    | Confussion Matrix  | Epoches Accuracy |
|:-------------------:|:-----------------------:|:---------------:|
|![Loss_Graph]|![Confussion_Matrix]|![Epoches_Accuracy]|


CNN Architecture of this model :
=================================
![ ](https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/CNN%20model%20architecture.png)



[Dataset_values]: https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/values.png
[Dataset_time_series]: https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/time%20series.png
[Dataset_faceted_distributions]: https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/faceted%20distributions.png
[Dataset_distributions]:  https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/distributions.png
[categorical_distributions]:  https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/categorical%20distributions.png
[Accuracy_Graph]: https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/accuracy%20for%20training%20and%20validation.png
[Loss_Graph]: https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/loss%20for%20training%20and%20Validation.png
[Confussion_Matrix]:https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/confussion%20matrix.png
[Epoches_Accuracy]: https://github.com/hasansust32/Satellite_Image_Classification_By_CNN/blob/main/findings_image/epoches%20accuracy.png



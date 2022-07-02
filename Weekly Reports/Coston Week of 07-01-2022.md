## Coston- Week of 06/27/2022-07/01/2022

# 1. At least 2 of the 3 subsections should have material

# 1.1 Papers Read

[https://arxiv.org/abs/2106.04370#:~:text=SCONE%3A%20Supernova%20Classification%20with%20a%20Convolutional%20Neural%20Network,neural%20network%20framework%20typically%20used%20for%20image%20recognition.](SCONE: Supernova Classification with a Convolutional Neural Network)

This article discusses the algorithm SCONE which is able to photometric classify supernova Ia. To accomplish this,
the light curve data is preprocessed into heatmaps. Through Gaussian processes, these heatmaps have limited issues 
with any irregularities that may occur between various filters. All of the data is then run through a convolution 
neural network. A convolution neural network takes an image and assigns various levels of importance to different 
parts/aspects of the image. This is done through alternation convolutional and pooling layers which are then 
followed by fully-connected layers. After all this, the group achieved 99.93 ± 0.06% training accuracy, 
99.71 ± 0.2% validation accuracy, and  99.73 ±  0.26% test accuracy.


# 1.2 Code Written

    model = Sequential()
    model.add(Dense(128, activation="relu", input_dim=nDim))
    #model.add(Dense(64, activation="relu"))
    model.add(Dense(10, activation="sigmoid"))

    callback = EarlyStopping(monitor='val_loss',
                             patience=5,
                             min_delta=0.001)
    opt = keras.optimizers.adam_v2.Adam(learning_rate=0.00001)
    model.compile(loss="sparse_categorical_crossentropy", optimizer=opt)

    fit = model.fit(Xtrn, Ytrn,
                    validation_data=(Xtst, Ytst),
                    batch_size=50, epochs=50,
                    verbose=1, callbacks=[callback])

    plot_model_loss(fit)

Upon exploring the google notebook Willow provided there are two methods that I have altered. 
This google notebook uses neural networks to classify MNIST data. The above code is the heart 
of the neural network. I studied how changing the layers (number of layers, activation code, 
size), batch size, and epochs would affect the neural network. The change would be studied by 
comping the loss function plots and the accuracy of each change. Figure 1 shows the plot of 
the code above.

The below code was a way for me to see the prediction and likelihood of that prediction for a 
specific image. Rather than finding the overall accuracy of the model, I was instead seeing the 
accuracy for a specific image. The output of the below code is seen in figure 2.

    pred = model.predict(Xtst)
    index = 3333
    plot_mnist(Xtst[index])
    arr = np.argmax(pred, axis = 1)
    num = arr[index]
    precent = (pred[index][num] * 100).round(2) 
    print("The model predicted that this image is the number", num) 
    print("with a percentage of", precent, "%")

# 1.3 Other (algorithm, discussion with experts, went to a conference)
	
  This week, for SOURCE, I presented a short 5-minute presentation on my research to my fellow 
  research assistants. Since the presentation was for an audience of various levels of background 
  in physics, I just gave a general overview and background of supernovae and neural networks.

# 2. Figures (at least 1 figure)


The model predicted that this image is the number 9
with a percentage of 99.1 %

# 3 Results (required)
This week gained a better grasp on neural networks and their components techniques through the 
exploration of the MNIST through the Google collab notebook, HW10_MNIST.ipynb, 
[https://playground.tensorflow.org](TensorFlow), and through my presentation.  I am continuing to 
learn more aspects of python as I continue to alter various codes. As the week progressed, I began 
to learn more about SCONE and how they were able to create a photometric SNe Ia classification algorithm. 

# 4 Planning (required)
For next week, I intend to work through the two Google collab notebooks that have been prepared to 
run SCONE. I intend to run the program first with PLAsTiCC data with the hopes of achieving the same 
results as they did in SCONE. Once that is successful, I hope to begin altering the code to not only 
run with ELAsTiCC data but to improve the classification of type II supernovae as well.



# Coston- Week of 06/20-24/2022

# 1. At least 2 of the 3 subsections should have material

# 1.1 Papers Read
[On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?](https://dl.acm.org/doi/pdf/10.1145/3442188.3445922) 
This article explains the various ethical problems and the cases surrounding natural language processing (NLP). The first ethical issue that 
the scholars go on to discuss is the environmental impact NPLs have. Training these programs takes a vast amount of energy which does not 
always come from renewable sources thus, they have a large impact on carbon emissions. Secondly, these NPLs are programmed by humans which 
greatly impacts what NPLs learn. For instance, a lack of diversity in the training sample often alienates specific races and languages 
(typically minorities). Stereotypes and other forms of bias can be programmed into the NPLs. Language also changes much faster than these 
programs can learn thus NPLs are often playing catch up. Ultimately they are massive datasets that are harmful to more marginalized groups. 

# 1.2 Code Written

      from sklearn.metrics import confusion_matrix
      #confusion_matrix ~ a matrix to evaluate the accuracy of a classification
      def plot_percentage_confusion_matrix(y_true, y_pred,
                                normalize=True,
                                title='',
                                cmap=plt.cm.Blues):      
          if normalize:
                title = title + ' Normalized confusion matrix as percentages'
          else:
                title = title + ' Confusion matrix, without normalization as percentages'

          # Compute confusion matrix
          cm = confusion_matrix(y_true, y_pred)
          cm_sum = np.sum(cm)
          pcm = (cm / cm_sum).round(2)

          pl.imshow(pcm, cmap="bone")
          pl.text(0,0, pcm[0][0])
          pl.text(1,1, pcm[1][1])
          pl.text(0,1, pcm[1][0], color="w", ha="center")
          pl.text(1,0, pcm[0][1], color="w", ha="center")
          pl.xticks([0,1], labels=["N", "P"])
          pl.yticks([0,1], labels=["N", "P"])
          pl.title(title)
          pl.colorbar()
          pl.clim(0, 1) 

Upon exploring the google notebook provided the two methods that I have altered. The above code prints a percentage confusion matrix 
rather than the numerical confusion matrix that was initially used in the notebook. In addition to changing the matrix to percentages, 
I also changed the colorbar to go from 0.0 to 1.0. The first time I ran the function, the maximum value of the color bar was around 0.7 
(or 70%) which was the maximum value within the confusion matrix. Thus, I changed the range to run from 0 to 1 (0% to 100%). 
All of this can be seen in figure 1.

The below code has been modified to add labels on the normalized confusion matrix. To complete this challenge, I modified the parameters 
given to the function to accept a data frame of the name of the targets which would be used as the label normalized confusion matrix. 
Once the data frame is passed to the function, the pl.xticks and pl.yticks methods organize the labels onto the plot. All of this can 
be seen in figure 2.

    from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay
    def plot_confusion_matrix(y_true, y_pred, name_of_target = None,
                              normalize=True,
                              title='',
                              cmap=pl.cm.Blues):     
        if normalize:
              title = title + ' Normalized confusion matrix'
        else:
              title = title + ' Confusion matrix, without normalization'
        # Compute confusion matrix
        cm = confusion_matrix(y_true, y_pred)

        pl.imshow(cm, cmap=cmap)
        pl.title(title)
        pl.xlabel('Predicted Label')
        pl.ylabel('True Label')
        pl.colorbar()
        y = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, ]
        pl.xticks(ticks = y , labels = name_of_target)
        pl.yticks(ticks = y , labels = name_of_target)

       plot_confusion_matrix(rf0.predict(testdata0), 
                          test_target0, 
                          name_of_target = np.unique(allfeatures['(target)'])    )

# 1.3 Other (algorithm, discussion with experts, went to a conference)

My one-on-one meeting with Willow was a basic introduction to neural networks. We reviewed the feedforward neural networks that she discussed
in her presentation on transformers from last week. In addition, we talked about general neural networks, backpropagation, and activation 
functions. We also went through Willow’s previous homework assignment to look through MNIST and how to code and run a neural network.
This afternoon I intend to attend the journal club this afternoon. I will add the information about that later today.

# 2. Figures (at least 1 figure)
![download](https://user-images.githubusercontent.com/107265822/175563564-bb78e88f-46c5-492a-b238-242b7ecee389.png)

Firgure 1: shows a percentage confusion matrix of the random forest based on the classification of the DDf.

![Figure 2](https://user-images.githubusercontent.com/107265822/175561780-bd06127b-a45b-42ac-865d-0b8ac6b9969a.png)


Figure 2: Shows a confusion matric of the random forest based on the classification of the target.


# 3 Results

This week gained a better grasp on machine learning techniques through the meetings of the week and the exploration of the PLAsTiCC through
the Google collab notebook, MLPNS2021 exam.  I am now more familiar with python and how to modify the code to receive different outcomes. 
As the week progressed, I began to learn more about how neural networks function and how to implement them. Willow introduced me to more 
background on neural networks. I am in a better place to start coding and running simple neural networks.

# 4 Planning 

For next week, I intend to work through Willow’s Google collab notebook, HW10_MNIST.ipynb, to study the components and code of the neural networks 
and their manipulation. I plan to evaluate how changes to the neural network affect the accuracy of the program. In addition, I plan to read the 
articles Dr. Bianco mentioned in our one-on-one meeting earlier in the week.

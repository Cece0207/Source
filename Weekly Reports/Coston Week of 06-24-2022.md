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
![Figure 1](data:image/png;base64,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)
Firgure 1: shows a percentage confusion matrix of the random forest based on the classification of the DDf.

![Figure 2](https://user-images.githubusercontent.com/107265822/175561780-bd06127b-a45b-42ac-865d-0b8ac6b9969a.png)
Figure 2: Shows a confusion matric of the random forest based on the classification of the target.


# 3 Results
 (required)

This week gained a better grasp on machine learning techniques through the meetings of the week and the exploration of the PLAsTiCC through
the Google collab notebook, MLPNS2021 exam.  I am now more familiar with python and how to modify the code to receive different outcomes. 
As the week progressed, I began to learn more about how neural networks function and how to implement them. Willow introduced me to more 
background on neural networks. I am in a better place to start coding and running simple neural networks.

# 4 Planning (required)

For next week, I intend to work through Willow’s Google collab notebook, HW10_MNIST.ipynb, to study the components and code of the neural networks 
and their manipulation. I plan to evaluate how changes to the neural network affect the accuracy of the program. In addition, I plan to read the 
articles Dr. Bianco mentioned in our one-on-one meeting earlier in the week.

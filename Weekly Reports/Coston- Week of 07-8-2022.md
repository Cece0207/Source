#Coston- Week of 07/4/2022-07/08/2022

##1. At least 2 of the 3 subsections should have material

###1.1 Papers Read

No papers were read this week.

###1.2 Code Written
 

Upon exploring the google notebook, savePlasticcAsFITS, there are two methods that I with the help of Willow created. The goal of these methods is to isolate the data for when the supernova occurs. The above code applies a function that finds the index of the MJD for when the supernova is present. This is accomplished by first finding the MJD for the maximum flux. The function finds the difference between each MJD observation. Afterward, a new array is created which notes when the difference between the MJD observation is greater than thirty. Each of these notes is either the beginning or end of a range of data. Finally, we just need to find what range contains the maximum MJD. The final range is saved as a series which can be seen in Figure 1.

The below code plots the MJD and flux within the range that was found in the above code. To spread the plot, I increased the x-axis by 20 (10 points below the lost point and 10 points above the highest point). This was done so that points would not rest at the edge of the plot. The plot can be seen in Figure 2.
 

###1.3 Other (algorithm, discussion with experts, went to a conference)
	
  This week, for SOURCE, I joined Dr. Rossi for lunch. Along with a few other SOURCE students, Professor Tania L. Roth and Professor Velia Fowler joined as well. The lunch was spent discussing both current and past research experiences. 
Through my weekly meeting with Dr. Fed, I learned more about convolutional neural networks since SCONE used convolutional neural networks to run the program. The main difference is that the convolutional neural networks analyze images by focusing on the patterns within the image.

##2. Figures (at least 1 figure)
	The above figure represents the outcome of the code seen above. The chart prints the beginning and final index of the MJD that contains the supernova. This index is found by locating where the maximum flux is. This range then helps in creating the plot of the data including the supernova data which is seen below. This range allows us the limit the data that the plot charts hence, only showing the desired data. Overall these methods help us in our future run-through of SCONE data since the SCONE heatmaps are only created at the instance of the supernova.

##3 Results (required)
This week gained a better grasp of python and the manipulation of data through the exploration of the PLASTIC data through the Google collab notebook, savePlasticcAsFITS. I am continuing to learn more aspects of neural networks as I continue to meet with Dr. Fedrica and Willow. I also have a better understanding of how to find supernova given a dataset and how SCONE was able to manipulate their data for their needs as well. 

##4 Planning (required)
For next week, I intend to work through the two Google collab notebooks that have been prepared to run SCONE. I intend to run the program first with PLAsTiCC data with the hopes of achieving the same results as they did in SCONE. Once that is successful, I hope to begin altering the code to not only run with ELAsTiCC data but to improve the classification of type II supernovae as well. This is the same as my previous week but since we are still waiting on resources from others I was unable to start. I hope everything will be up and running soon.



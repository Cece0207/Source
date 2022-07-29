# Coston- Week of 07/25/2022-07/29/2022

## 1. At least 2 of the 3 subsections should have material

### 1.1 Papers Read

No papers were read this week.

### 1.2 Code Written

With the difficulties of downloading pyCharm we have decided to move back to Google collab notebooks as well as move on to working with ELAsTiCC data. This week I have worked on completing two parts of manipulating the ELAsTiCC data set in order to run it through our manipulation of the SCONE program.
 
[ELASTIC_lc](https://github.com/Somayeh91/ELASTICC_lc) 

First, we have to access the ELAsTiCC data set. With the help of Somayeh Khakpash, I was able to download the ELAsTiCC files into google drive. Above is the link to her original GitHub repo. However, since copying it over to a google collab notebook, I have made a few changes in order for it to run properly within the notebook. 

Once, the data has been read in, it needs to be reformatted in order to run with the SCONE code that we have already worked on. The code above shows how I began to test the manipulation of the data. I first covered all of the data into a pandas DataFrame and stacked the data so that there was only one column, as seen in Figure 1. This column was a list of lists thus, we had to separate both the lists and the contents of each list. This was done by the following line of code and had an output that can be seen in Figure 2. 

To make the DataFrame easier to read and understand, I renamed and deleted unnecessary columns. The code and be seen below while the output can be seen in Figure 3.

Finally, I plotted the data to compare to previous light curves that I have plotted. Again, the code can be seen below while the output can be seen in Figure 4. The work I have done to get this is only for one section of the entire ELAsTiCC data. When trying to apply similar methods to the full data set, I ran into several errors hence I chose to take a smaller portion of the data and go step by step. 

### 1.3 Other (algorithm, discussion with experts, went to a conference)
	This week, many of the members of FASTLab went to the BOOM! conference. In preparation for their talks, Willow Fox Fortino and Xiaolong Li presented their work to the group. Willow discussed low-resolution spectroscopy while Xiaolong gave two presentations one on unknown unknowns and the second on the detection of light echoes. This not only taught me more about their respective topics but also about what makes a good presentation. 

## 2. Figures (at least 1 figure)

Figure 1:
Here is the stacked DataFrame of the ELAsTiCC data set. There is a total of 40 objects for the data that I downloaded. Hence the 0 to 39 that label to outermost rows. Each object has numerous observations. The list of lists proved the information on the observations. The lists include information such as the mjd, passband, flux, and flux error to name a few.

Figure 2:
This is after breaking the list of list into individual columns for each value. But this only shows object 0 as I was having trouble completing this separation for each object at the same time.

Figure 3:
This is a reorganized DataFrame of Figure 2. That now shows the MJD, passband, flux, and flux error for each observation of object 0.

Figure 4:
This shows a plotted version of the data from figure 3. In a similar manner to previous light curve scatter plots. The flux is plotted as a function of mjd with the flux error taken into account by the error bars on the plot.	

## 3 Results (required)

This week gained a better grasp of debugging code and GitHub through the beginning of the manipulation of the ELAsTiCC data set. Since we are unable to run pyCharm we have gone back to using GitHub and Google collab notebooks. I now have a better understanding of how to get and share code between the two software. Since the ELAsTiCC is not in the same format as the PLAsTiCC I have also gained a better understand of manipulating DataFrames.

## 4 Planning (required)

For next week, I intend to work through the manipulation of the ELAsTiCC data and be able to create the heatmaps needed to run the SCONE code. I still need to make final touches to the formatting of the heatmaps before looking to run the neural networks on them. Along with this, I will continue to work on writing my final paper for the SOURCE program.





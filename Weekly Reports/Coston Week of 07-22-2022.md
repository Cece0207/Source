# Coston- Week of 07/18/2022-07/22/2022

## 1. At least 2 of the 3 subsections should have material

### 1.1 Papers Read

No papers were read this week.

### 1.2 Code Written

With the increase of classes and code, we have transferred the code to GitHub and have begun editing the code within 
pyCharm. Here I will discuss the two main Google collab notebooks that have now been altered to work in pyCharm

(splitdata.ipynb)[https://github.com/Cece0207/reSCONE/blob/85abf6914a51555c9c76f0c12ce1b4f5dfb2f910/splitdata.ipynb] 

This is run within a jupyter notebook. It splits a light curve data file into 144 files that each have 10 supernovas 
within them (aside from the last file that online has 9 supernovas). The path to each of these files, both their light 
curve and metadata, are then saved as a list within the config file. Afterward, cuts are played to the list to ensure 
that they are using quality cuts. These quality cuts are then saved within a hd5f file.

(createHeatmaps.ipynb)[https://github.com/Cece0207/reSCONE/blob/85abf6914a51555c9c76f0c12ce1b4f5dfb2f910/createHeatmaps.ipynb]

This also runs within a jupyter notebook. This is able to call the class create_heatmaps.heatmaps_types which can be 
found (here)[https://github.com/Cece0207/reSCONE/tree/main/scone/create_heatmaps]. By using the other classes and 
methods within  create_heatmaps.heatmaps_types, we are able to create two heat maps and a light curve of each supernova 
that we had saved in the hd5f file from above. A piece of the outcome can be viewed in the figures below. 

### 1.3 Other (algorithm, discussion with experts, went to a conference)
	This week, for SOURCE, I joined Dr. Fedrica and a few other members of the program for a research seminar and lunch. 
  The time was spent explaining Dr. Fedrica's journey to what she is doing now along with the current research she is
  part of. Riley Clarke also gave a short explanation of his research as well.  

## 2. Figures (at least 1 figure)
<img width="439" alt="image" src="https://user-images.githubusercontent.com/107265822/180478595-1c92eb74-ed7f-4f30-8f34-ab05dcbad649.png">

	The above figure represents the outcome of the code provided by the hyperlinks. The code prints out two heatmaps
  and the light curve per object. The object above is Supernova 730. The first heatmap is based on the flux while 
  the second is created based on the flux error. Now that we are able to create heatmaps, we can begin the process 
  of training the neural network. The light curve of the object only shows the times at which the supernova is present. 
  Below are two more versions of the light curve 730. The first shows the inter-duration that the PLAsTiCC data set 
  provides. The second shows the time at which the supernova occurs. Note that the supernova occurs in the section 
  that has the highest flux. For object 730 this is in the third and last position of the recording of data.
  
![download](https://user-images.githubusercontent.com/107265822/180478834-729d2950-f501-41b3-b270-fef74ef2f970.png)

![download](https://user-images.githubusercontent.com/107265822/180478846-61206d50-8d1d-4143-a20c-b9416c9e877c.png)

## 3 Results (required)
This week gained a better grasp of debugging code through the continuation of the manipulation of the SCONE code. 
We have now branched out of the Google collab notebooks and have begun coding in pyCharm. Through going through 
every line I have a better understanding of the relationship between parent and child classes. We have also been 
able to recreate the heatmaps of the SCONE data.  

## 4 Planning (required)
For next week, I intend to work through the pyCharm to make some final touches to the formatting of the heatmaps 
before looking to run the neural networks on them. I intend to run the program first with PLAsTiCC data with the 
hopes of achieving the same results as they did in SCONE. Along with this, I plan to prepare and present two 
presentations in the following week. The first of which is for the SOURCE program and is a breakdown of what I 
have accomplished so far within the program. The second presentation is for Friday at the journal club. 




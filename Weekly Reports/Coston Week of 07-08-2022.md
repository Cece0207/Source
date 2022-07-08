# Coston- Week of 07/4/2022-07/08/2022

## 1. At least 2 of the 3 subsections should have material

### 1.1 Papers Read

No papers were read this week.

### 1.2 Code Written
 
			def func(x):

			    mjd = np.array(x["MJD"])
			    flux = np.array(x["FLUXCAL"])
			    argmax_flux = np.argmax(flux)
			    max_flux = flux[argmax_flux]
			    max_mjd = mjd[argmax_flux]

			    # Find the MJD difference in each observation
			    diffs = np.diff(x["MJD"], append=x["MJD"].iloc[-1])

			    # Find out where these MJD differences are greater than 30 days.
			    # The array `inds` will index the `mjd` or `flux` arrays.
			    inds = np.where(diffs > 30)[0]

			    # The `inds` array denotes the ends of seasons. Let us add indices to the
			    # array so that it denotes the start and end of each season.
			    for ind in inds:
				# Adding the index after the one that already appears. If `ind` denotes
				# the index for the end of one season, then `ind + 1` denotes the index
				# for the beginning of the next season.
				inds = np.append(inds, ind + 1)

			    # Add 0 to the list of inds. This is the index for the start of the first
			    # season.
			    inds = np.append(inds, 0)

			    # Here we add the the very last index for the array. This denotes the end
			    # of the last season.
			    inds = np.append(inds, len(mjd) - 1)

			    # Now we have the indices for the beginning and end of each season.
			    # Let's put them in order.
			    inds = np.sort(inds)

			    # Now let's reshape this array so that `inds[0]` will be the range for the
			    # first season, `inds[1]` will be the range for the second season, and so on.
			    inds = inds.reshape((int(inds.size / 2), 2))

			    # Now we loop through each of these ranges and figure out which one
			    # `max_mjd` belongs to.
			    for mjd_range in inds:
				start = mjd[mjd_range[0]]
				end = mjd[mjd_range[1]]
				if start <= max_mjd <= end:
				    SN_range = mjd_range
				    break

			    return pd.Series({"SN_range": SN_range,
					      #"argmax_flux": argmax_flux
					      })

			grouped = lcvsforfits.groupby(["SNID"]).apply(func)
			grouped
			
Upon exploring the google notebook, savePlasticcAsFITS, there are two methods that I with the help of Willow created. The goal of these methods is to isolate the data for when the supernova occurs. The above code applies a function that finds the index of the MJD for when the supernova is present. This is accomplished by first finding the MJD for the maximum flux. The function finds the difference between each MJD observation. Afterward, a new array is created which notes when the difference between the MJD observation is greater than thirty. Each of these notes is either the beginning or end of a range of data. Finally, we just need to find what range contains the maximum MJD. The final range is saved as a series which can be seen in Figure 1.

The below code plots the MJD and flux within the range that was found in the above code. To spread the plot, I increased the x-axis by 20 (10 points below the lost point and 10 points above the highest point). This was done so that points would not rest at the edge of the plot. The plot can be seen in Figure 2.
 
		 import matplotlib.pyplot as pl

		for i, SNID in enumerate(np.unique(lcvsforfits["SNID"])):
		  if i == 1:
		    break

		  pl.figure(figsize=(12,6))
		  pl.title("SNID")

		  good_flux = lcvsforfits.loc[lcvsforfits["SNID"] == SNID]["FLUXCAL"]
		  data_mjd =  lcvsforfits.loc[lcvsforfits["SNID"] == SNID]["MJD"]

		  good_flux = np.array(good_flux)
		  data_mjd = np.array(data_mjd)

		  SN_range = grouped[grouped.index == SNID]["SN_range"].iloc[0]
		  start = data_mjd[SN_range[0]] - 10
		  stop = data_mjd[SN_range[1]] + 10
		  #argmax_flux = grouped[grouped.index == SNID]["argmax_flux"].iloc[0]

		  pl.plot(data_mjd, good_flux, marker= 'x', ls="")
		  pl.xlim(start, stop)
		  pl.xlabel("Time (Modified Julian Day)")
		  pl.ylabel("Fluxcal")
		  pl.title("Light Curve Object %.f"%SNID )


### 1.3 Other (algorithm, discussion with experts, went to a conference)
	
This week, for SOURCE, I joined Dr. Rossi for lunch. Along with a few other SOURCE students, Professor Tania L. Roth and Professor Velia Fowler joined as well. The lunch was spent discussing both current and past research experiences. 
Through my weekly meeting with Dr. Fed, I learned more about convolutional neural networks since SCONE used convolutional neural networks to run the program. The main difference is that the convolutional neural networks analyze images by focusing on the patterns within the image.

## 2. Figures (at least 1 figure)


	SN_range
SNID	
730	[222, 329]
745	[125, 229]
1124	[231, 351]
1598	[231, 351]
1632	[0, 121]
...	...
130639669	[24, 69]
130659834	[60, 99]
130678775	[70, 117]
130698059	[18, 66]
130755807	[47, 61]

The above figure represents the outcome of the code seen above. The chart prints the beginning and final index of the MJD that contains the supernova. This index is found by locating where the maximum flux is. This range then helps in creating the plot of the data including the supernova data which is seen below. This range allows us the limit the data that the plot charts hence, only showing the desired data. Overall these methods help us in our future run-through of SCONE data since the SCONE heatmaps are only created at the instance of the supernova.

![download](https://user-images.githubusercontent.com/107265822/178046519-633d1415-82c7-4b5f-9f6e-2b30f0043cde.png)

## 3 Results (required)
This week gained a better grasp of python and the manipulation of data through the exploration of the PLASTIC data through the Google collab notebook, savePlasticcAsFITS. I am continuing to learn more aspects of neural networks as I continue to meet with Dr. Fedrica and Willow. I also have a better understanding of how to find supernova given a dataset and how SCONE was able to manipulate their data for their needs as well. 

## 4 Planning (required)
For next week, I intend to work through the two Google collab notebooks that have been prepared to run SCONE. I intend to run the program first with PLAsTiCC data with the hopes of achieving the same results as they did in SCONE. Once that is successful, I hope to begin altering the code to not only run with ELAsTiCC data but to improve the classification of type II supernovae as well. This is the same as my previous week but since we are still waiting on resources from others I was unable to start. I hope everything will be up and running soon.



# Coston- Week of 07/11/2022-07/15/2022

## 1. At least 2 of the 3 subsections should have material

### 1.1 Papers Read
No papers were read this week.

### 1.2 Code Written

          import pandas as pd
          import numpy as np
          import os
          import yaml
          import argparse

          #parser = argparse.ArgumentParser(description='create heatmaps from lightcurve data')
          #parser.add_argument('--config_path', type=str, help='absolute or relative path to your yml config file, i.e. "/user/files/create_heatmaps_config.yml"')
          #parser.add_argument('--lc_files', type=str)
          #parser.add_argument('--metadata_files', type=str)
          #parser.add_argument('--num_splits', type=int, default=0, help='number of files to split into')
          #args = parser.parse_args()

          #with open(args.config_path, "r") as cfgfile:
            #  config = yaml.load(cfgfile)

          #for j, file in enumerate(args.lc_files):
          def slit_datafile(lcdata_path, metadata_path): 
              """ Splits a light curve data file into n files for n supernova
                  Input: 
                  lcdata_path:(string) path to the file containing the light curve data
                  metadata_path: (string) path to the file containing the metadata
                  Output:
                  n: (int) number of files that were saved
              """

              SN_TYPE_ID_MAP = snid_to_name
              metadata = pd.read_csv(metadata_path)
              lcdata = pd.read_csv(lcdata_path) 
              lcdata_ids = np.array(metadata[(metadata.true_target.isin(SN_TYPE_ID_MAP.keys()))&(metadata.ddf_bool == 1)].object_id)
              print("total unique sne: {}".format(len(lcdata_ids)))

              split_lcdata_ids = np.array_split(lcdata_ids, 3)
              lcdata_rows = 0
              new_metadata_paths = []
              new_lcdata_paths = []
              for i, subarray in enumerate(split_lcdata_ids):
                  metadata_split = metadata[metadata['object_id'].isin(subarray)]
                  lcdata_split = lcdata[lcdata['object_id'].isin(subarray)]
                  lcdata_rows += len(lcdata_split)
                  assert len(metadata_split) == len(subarray)
                  print("file {} has {} sne with {} lcdata rows".format(i, len(metadata_split), len(lcdata_split)))

                  metadata_split.to_csv("{}_{:03d}.csv".format(metadata_path.split(".")[0], i))
                  lcdata_split.to_csv("{}_{:03d}.csv".format(lcdata_path.split(".")[0], i))

                  new_metadata_paths.append("{}_{:03d}.csv".format(metadata_path.split(".")[0], i)) #extra dashes for writing to config yml
                  new_lcdata_paths.append("{}_{:03d}.csv".format(lcdata_path.split(".")[0], i))
              print("total lcdata rows written: {}, out of total: {}".format(lcdata_rows, len(lcdata[lcdata['object_id'].isin(lcdata_ids)])))
              assert lcdata_rows == len(lcdata[lcdata['object_id'].isin(lcdata_ids)])

             # config["metadata_paths"] += new_metadata_paths
              #config["lcdata_paths"] += new_lcdata_paths
              #config["metadata_paths"].remove(METADATA_PATH)
              #config["lcdata_paths"].remove(LCDATA_PATH)
              #with open(args.config_path, "w") as cfgfile:
               #   cfgfile.write(yaml.dump(config))

              return len(lcdata_ids), new_metadata_paths, new_lcdata_paths 
    
Upon working through the SCONE data, I have successfully run a few parts of the code. 
First of which is [split_data_files.py](https://github.com/helenqu/scone/blob/main/legacy/split_data_files.py). The original code can be seen by following the 
hyperlink while my edits are above. The main change in the code is the use of argparse. 
Within the notebook we were not able to use the argpase functions thus we had to find 
workarounds. Thus, we created a function instead. Along with argpase, we originally 
did not use the config file. This caused us to directly pass whatever the code required. 
The output of this function can be seen in Figure 1.

                  def calculate_peakmjd(metadata, lcdata):
                      peak_mjd_calculated = []
                      for snid in metadata['object_id']:
                          sn_data = lcdata[lcdata['object_id'] == snid]
                          #sn_data = lcdata.loc['object_id', snid]
                          sn_metadata = metadata[metadata['object_id'] == snid]

                          mjd = np.array(sn_data['mjd'])
                          flux = np.array(sn_data['flux'])
                          flux_err = np.array(sn_data['flux_err'])
                          snrs = flux**2 / flux_err**2
                          mask = snrs > 5
                          mjd = mjd[mask]
                          snrs = snrs[mask]
                          if len(mjd) == 0 or len(snrs) == 0:
                              print(snid)
                          peak_mjd_calculated.append(np.sum(mjd * snrs) / np.sum(snrs))
                      return peak_mjd_calculated
            
The second of which is [data_cuts.py](https://github.com/helenqu/scone/blob/main/legacy/data_cuts.py). Again the original code can be seen by following the 
hyperlink however since this has a larger amount of code on a few piece of my edits are 
included here. This rest can be seen within this [Google collab notebook](https://colab.research.google.com/drive/168kuI2K3JW9dZl8bdToQi2DrlMQ96ujE#scrollTo=yC3WqsGrVUco). Above is 
calculate_peakmjd function. This function along with the function Willow and I created 
last week strive to achieve the same goal. However they do it slightly differently. The 
only error I had to fix within the SCONE code is the formatting of the sn_data. The way 
the original code used the .loc method did not work with in the notebook. After fixing 
the error, the function ran, however, the values are slightly different than those found 
in the previous week. The outcome can be seen in Figure 2.

### 1.3 Other (algorithm, discussion with experts, went to a conference)

This Monday, during my SOURCE activities, a few graduate students joined the workshop to 
provide incent into their graduate school experiences. Overall, the students focused on 
how they applied to their programs and the support or lack of support they received from 
the University of Delaware. 

Through the weekly group meetings, I learned about unit testing since many of the members 
of the group had spent the last week in a workshop learning to code and use unit testing. 
Unit testing individually tests small parts of a program to examine how accurately it is 
performing its proper function.

## 2. Figures (at least 1 figure)

<img width="512" alt="image" src="https://user-images.githubusercontent.com/107265822/179253362-ca1886a0-2ac3-4b15-a837-a9f7d3ea9bef.png">

Figure 1: The above figure shows the output of the slit_datafile function. To run this 
  function a string of path to the file that contains the light curve data and a string 
  of path to the file that contains the metadata must be passed. This functions splits 
  the data into three files. The number files can be changed by altering the 
  split_lcdata_ids array. When creating the array the method .array_split is used. We 
  pass the method what data we want to split while the number indectates how many 
  sections that we want to create. The outcome shows the total number of unique supernova, 
  how many supernova and light curve data rows per file, and the direct path to both the 
  metadata and light curve data for each file.
  
  <img width="509" alt="image" src="https://user-images.githubusercontent.com/107265822/179253185-e990220d-7ba0-4e72-b5e2-f02e65a5eb57.png">

Figure 2: The above figure shows the output of the function calculate_peakmjd. To run this 
  function an array of the metadata and an array of  light curve data must be passed. Above, 
  we can see that I only asked for the peak mjd for the supernova with the ID 730. Without that, 
  the function will print the mjd values for all the supernova. As we can see this code gave the 
  value of 60043.477 for the peak mjd while mine gave 60535.3177 for the peak mjd. I intend to 
  look further into these differnce in the future.

## 3 Results (required)

This week gained a better grasp of python and the manipulation of data through the exploration of 
SCONE through the Google collab notebook, runSCONEwithPLASTICCAsFITS. Since I have been traversing 
the SCONE code into a Google collab notebook, there have been many problems that I have had to work 
through. Through the help of Dr. Fedrica and Willow, I have learned good practices for adapting and 
solving errors within code. Through meticulous going through each line of SCONE, I have gained a much 
better understanding of how they manipulate their data for their needs as well. 

## 4 Planning (required)

For next week, I intend to continue working through the Google collab notebooks that have been prepared 
to run SCONE. By the end of the week, I would like to be able to recreate the heatmaps of SCONE. I hope 
to have this done before the weekly group meetings, so I can show my findings. The next step would be to 
run the conventional neural network. Once that is completed, I would have successfully run SCONE with the 
PLAsTiCC dataset.




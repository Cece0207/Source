# Coston- Week of 06/13-17/2022

# 1. At least 2 of the 3 subsections should have material

# 1.1 Papers Read
[The PLAsTiCC Astronomy "Starter Kit”](https://www.kaggle.com/code/michaelapers/the-plasticc-astronomy-starter-kit) 
This notebook on Kaggle provides a clear introduction to PLAsTiCC that was done on Kaggle. The notebook started by describing the basic
knowledge of astrophysical phenomena that code be helpful to the average coder. This included basic information on the Large Synoptic
Survey Telescope (LSST) which has since been renamed to Legacy Survey of Space and Time, information on light curves and their properties,
stellar and galactic coordinates, and redshifting. The notebook also inclined information on the history of astronomers studying the night sky. 
Within the light curve section, the notebook provided code that demonstrated one way to format the light curve data that the PLAsTiCC challenge provides. 

# 1.2 Code Written
     #WWW
    def quadfit(x):
        d = {}
    
        tmp_ = np.polyfit(x['mjd']-x.iloc[0]['mjd'], x['fluxnormed'], 2)
        d['QUAD_a'] = tmp_[0]
        d['QUAD_b'] = tmp_[1]
        d['QUAD_c'] = tmp_[2]
        return pd.Series(d, index=['QUAD_a', 'QUAD_b', 'QUAD_c'])
    
    linfits = lcvs.groupby(["object_id", "passband"]).apply(linfit)
    #.apply passed a function, that function in run through the dataframe 
    
Upon exploring the google notebook provided I have been working through the code to better understand python and machine learning methods.
Both Dr. Bianco and Willow helped me to understand various pieces of the code. The code above was written by Willow. This function is a variation 
of a function already in the notebook. Quadfit finds a quadratic line of best fit for the standardized data. The original function ran np.polyfit for
each parameter. This new function runs np.polyfit once and increments through the function.

# 1.3 Other (algorithm, discussion with experts, went to a conference)
	
  The one-on-one meeting was a basic introduction to machine learning. We covered the loss function, random forest, and gradient boost classifiers. 
	
  During the full-body meeting, Willow gave a presentation on the article Attention is All You Need. She covered feedforward neural networks, 
  encoders and decoders, and transformers.

# 2. Figures (at least 1 figure)
N/A
. . .

# 3 Results (required)

This week gained a better grasp on machine learning techniques through the meetings of the week and the exploration of the Photometric 
LSST Astronomical Time-series Classification Challenge (PLAsTiCC) through the Google collab notebook, MLPNS2021 exam.  The Kaggle notebook,
The PLAsTiCC Astronomy "Starter Kit”,  to better understand the basic code behind the project. Overall, I have gained a much better understanding 
of not only python but how astrophysics are using it to assist in their research.

# 4 Planning (required)

For next week, I intend to continue working through the Google collab notebook, MLPNS2021 exam, to study the components and code of the time series 
and their manipulation. In addition, I plan to read [On the Danger of Stochastic Parrots](https://dl.acm.org/doi/pdf/10.1145/3442188.3445922)
and [Reproducibility of Scientific Results](https://plato.stanford.edu/entries/scientific-reproducibility/). And be prepared to discuss neural 
networks with Willow on Wednesday.


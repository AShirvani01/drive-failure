# Drive Failure Risk Factors
This repository contains my final project and code for STA475: Survival Analysis @ UofT. 
Python and SQL was used to compile and store the data. Analysis was done in R. The final project was in the form of an infographic.
## Objective
The goal of this analysis was to evaluate the risk factors (brand and
capacity) associated with time to drive failure.

## Acknowledgements
The data used in this analysis was sourced from [BackBlaze](https://www.backblaze.com/cloud-storage/resources/hard-drive-test-data),
an open cloud storage company that publishes survival data on the drives in their data centers.

## Reflection
I initially thought this project was fairly straight forward and wouldn’t take too long, but I actually
encountered a lot of difficulties, some of which I never solved. I found this time-to-failure data for
drives that was massive, so writing a python script to upload everything to SQL was tedious but
simple. Same with data cleaning. It was simple but tedious. There were around 170 different
models so I thought it would be better interpretation and computation wise to create a brand
covariate. At first, I was planning on using Cox Proportional Hazard models for the data, but I
quickly found that the proportional hazards assumption was violated. The covariates themselves
were constant, however their respective coefficients varied with time, which was a big problem. I
spent a long time reading forums and sections of textbooks looking for different methods of relaxing
the assumption (stratification, dividing up the data, different types of transformations). All the
methods I tried were either ineffective or computationally infeasible given such a massive dataset.
AFT models showed similar violations, which led me to consider using nonparametric methods. I
thought KM estimates would be too simple, so I explored Random Survival Forests as they seemed
to have good performance. However, I quickly realized that I’m not really interested in a model with
good predictive performance. I'm looking for interpretability. That was the whole idea of a poster, right? So
finally, I settled for using just KM estimates and log-rank tests knowing that there wasn’t much
interpretation to be had. Although frustrating, more time-consuming than expected, and a
lackluster analysis in the final poster, I gained a better understanding of various methods of dealing
with survival data that might be useful in the future.

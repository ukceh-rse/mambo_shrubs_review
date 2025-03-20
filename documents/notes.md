# Notes

_Trying to keep as much as possible in a review report/presentation, but notes in passing can go here first_

## Aims

The MAMBO project has more ambition than it does time. There are some research prototypes for shrub extraction and characterisation from different remote sensing data sources. There are analytical methods which are designed to accept output from these models. There's not much glue work, an overview of "could be" and a project need to be able to run a tutorial workshop for partners, on a platform with open registration, in Summer 2025. The PIs have expressed a preference for Colab for this.

### Wishlist

In rough order of priority (mine). In practise there are only two months of dedicated work hours, short term. A well-tested onboarding notebook tutorial is the non-negotiable part. Integration with the analysis package (providing it real output data) is the most "valuable" part and should be done as early as possible, even if we end up replacing some of the methods.

The rest is more aspirational - it seems better (at project start) to have a recipe book for infrastructure choices which overlaps with other Digital Research Infrastructure project needs (and funding availability) than it does to have half built infrastructure (like evocative pipelines) - in a way, the longer we wait the more likely it is the needs of MAMBO will be met elsewhere.

* Reproduce the existing work and evaluate open source projects that could either augment or replace it
* Consistent, data-versioned way of passing the outputs to the next phase in the project (outwith our control)
* Minimum viable notebook walkthrough of model reuse, with a prepared dataset
* Code / data / models packaged in ways that would allow for ease of automation
* Minimum viable pipeline that automates the work in the notebook
* Proof of concept architecture for the larger picture [see existing diagrams] picking out both reusable open source components and alignment with other UKCEH / NERC infrastructure projects (especially on data catalogue and access services)

## Software

The first two are researcher prototypes, the last one is the analytical method that we should be feeding data into, and that the onboarding notebooks should cover.

•	Shrub mask preprocessing: https://github.com/barbedorafael/shrub-prepro ; 
•	Attention U-Net model pipeline: https://github.com/barbedorafael/att-unet-shrub-id ; 
•	Allometry https://github.com/douglask3/BRAMBLE/blob/main/development_notebook.ipynb

Can we reproduce all these, what data or weights are not included, and where's a suitable online service or catalogue for accessing them?

## Data and data sharing

This is going to be an early and ongoing issue

* Reproducibility of prototypes (storage of models, example training data, demo inference data - this last could be derived from a STAC catalogue)
* Hosting for workshops (needs ease of access from externally hosted notebook)

DroneDB looks very promising for data management / catalogue access. Michael Tso et al did a WebODM prototype for the same group in 2022. 

### Data sources

External data is listed in the Data Management Plan

https://www.data.gov.uk/dataset/f0db0249-f17b-4036-9e65-309148c97ce4/national-lidar-programme - DEFRA LIDAR, 1m resolution in 5km tiles, OGL

The DMP also says:

* Provenance information will be stored when running the workflow, and we will build this into
our workflow.
* The script/workflow/model will be annotated or commented to be made understandable.
* All of our data can become completely open immediately.
* Our research data will be peer-reviewed through a data journal.


### Storage options 

* [JASMIN s3](https://help.jasmin.ac.uk/docs/short-term-project-storage/managing-a-gws) - does setting this up involve direct NERC funding? 

## Background

(https://www.sciencedirect.com/science/article/abs/pii/S1077314221000655)

Ruiliang Pu's review paper from 2021 on state of the art of remote sensing tree mapping

https://notebooklm.google.com/notebook/faca1d84-2082-4224-964b-f492ad4c9aa2?_gl=1*15qi2sg*_ga*NDI3NDU0MTIyLjE3NDIzMDEzMzU.*_ga_W0LDH41ZCB*MTc0MjMwMTMzNS4xLjAuMTc0MjMwMTMzNS42MC4wLjA.&original_referer=https:%2F%2Fnotebooklm.google%23&pli=1

Very experimental NotebookLM instance with the paper above and a couple of different "awesome lists" for context

## Utils

https://www.getbibtex.com/ - for citation generation

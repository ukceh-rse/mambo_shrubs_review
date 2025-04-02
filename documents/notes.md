# Notes

_Trying to keep as much as possible in a review report/presentation, but notes in passing can go here first_

## Aims

MAMBO WP4 has ambitious longer-term goals and relatively limited shorter-term time. What we have available are

* Research prototypes for shrub extraction and characterisation from different remote sensing data sources. 
* Analytical methods which are designed to accept output from these models and estimate biomass
* An image and data collection which includes drone-borne top-down imagery and LIDAR point clouds

The aims of this phase of development (engaging a Research Software Engineer for a couple of months) are

* Make the data discoverable and reusable
* "Glue work" on a reproducible workflow, reusing the existing model and/or a pretrained one developed elsewhere for shrub height estimation from a combination of imagery, terrains/surface models, and LIDAR
* Provide an overview of "could be" with recommended off-the-shelf open source components for a more full and automated workflow, also describing infrastructure needs to support it

We need to be able to run a tutorial workshop for partners, on a platform with open registration, in Summer 2025. The PIs have expressed a preference for Colab for this.

### Wishlist

In rough order of priority (_mine - JW_). In practise there are only two months of dedicated work hours, short term. A well-tested onboarding notebook tutorial is the non-negotiable part. Integration with the analysis package (providing it real output data) is the most "valuable" part and should be done as early as possible, even if we end up replacing some of the methods.

It seems better (at project start) to have a recipe book for infrastructure choices which overlaps with other Digital Research Infrastructure project needs (and funding availability) than it does to have half built infrastructure (like evocative pipelines) - in a way, the longer we wait the more likely it is the needs of MAMBO will be met elsewhere.

* Reproduce the existing work and evaluate open source projects that could either augment or replace it
* Consistent, data-versioned way of passing the outputs to the next phase in the project (outwith our control)
* Minimum viable notebook walkthrough of model reuse, with a prepared dataset
* Code / data / models packaged in ways that would allow for ease of automation
* Minimum viable pipeline that automates the work in the notebook
* Proof of concept architecture for the larger picture [see existing diagrams] picking out both reusable open source components and alignment with other UKCEH / NERC infrastructure projects (especially on data catalogue and access services)

## Software

The first two are researcher prototypes, the last one is the analytical method that we should be feeding data into, and that the onboarding notebooks should cover.

* Shrub mask preprocessing: https://github.com/barbedorafael/shrub-prepro ; 
* Attention U-Net model pipeline: https://github.com/barbedorafael/att-unet-shrub-id ; 
* Allometry https://github.com/douglask3/BRAMBLE/blob/main/development_notebook.ipynb

Can we reproduce all these, what data or weights are not included, and where's a suitable online service or catalogue for accessing them? 

_Update: we have a data dump which includes imagery, point clouds, model training code, processing utilities and early reports to sort through - data and models to s3, extra reusable code to Github_

There's another project, `shrub_height` which is not in a repository yet, only in the data collection. Reproducing this and publishing it is an early step we can take in parallel with data management struggles.

## Data and data sharing

This is going to be an early and ongoing issue:

* Reproducibility of prototypes (storage of models, example training data, demo inference data - this last could be derived from a STAC catalogue)
* Hosting for workshops (needs ease of access from externally hosted notebook)

[DroneDB](https://github.com/DroneDB) looks very promising for data management / catalogue access. Michael Tso et al did a WebODM prototype for the same group in 2022. 

### Data sources

External data is listed in the Data Management Plan

https://www.data.gov.uk/dataset/f0db0249-f17b-4036-9e65-309148c97ce4/national-lidar-programme - DEFRA LIDAR, 1m resolution in 5km tiles, OGL

The DMP also says:

* Provenance information will be stored when running the workflow, and we will build this into
our workflow.
* The script/workflow/model will be annotated or commented to be made understandable.
* All of our data can become completely open immediately.
* Our research data will be peer-reviewed through a data journal.

### Data indexing and discovery

Data available in object storage, with associated STAC catalogue. Depending how large the STAC index files are, they could be held in a git repo, or in another bucket and tracked via DVC.

* [Walkthrough of creating STAC catalogue from programmatically readable metadata](https://stacspec.org/en/tutorials/2-create-stac-catalog-python/)

There's also questions of format conversion and optimisation - e.g. to COG or COPC (Cloud Optimised Point Cloud). There's probably relevant work in FDRI (the focus is on timeseries but the background in optimisation of storage / chunk sizing etc will be similar).

Depends on what we have in the data, the next step ideally would be to find existing utilities that we can point at a large geodata collection and generate a catalogue outline.

This not only helps us meet the requirements of the DMP but offers a means of search and download from a notebook which could live anywhere, that's reasonably reproducible.

### Storage options 

* [JASMIN s3](https://help.jasmin.ac.uk/docs/short-term-project-storage/managing-a-gws) - does setting this up involve direct NERC funding? 

We have an existing GWS with object storage configured, to which I'm arranging access. It would simplify things (e.g. running a notebook-based workshop without having to give people credentials that may be stored insecurely) if we can make the data world-readable to anyone who knows the URL, can we envisage issues with this? (ecological site sensitivity, GDPR concerns, other?)

See [s3.md](s3.md) for walkthrough notes on working with s3 storage.

## Background

See [references.bib](references.bib) for a BibTex reference collection.

[Ruiliang Pu's review paper from 2021 on state of the art of remote sensing tree mapping](https://www.sciencedirect.com/science/article/abs/pii/S1077314221000655)

[experimental NotebookLM instance](https://notebooklm.google.com/notebook/faca1d84-2082-4224-964b-f492ad4c9aa2?_gl=1*15qi2sg*_ga*NDI3NDU0MTIyLjE3NDIzMDEzMzU.*_ga_W0LDH41ZCB*MTc0MjMwMTMzNS4xLjAuMTc0MjMwMTMzNS42MC4wLjA.&original_referer=https:%2F%2Fnotebooklm.google%23&pli=1) with the paper above and a couple of different "awesome lists" for context - probably not an experiment I would repeat!

## Utils

https://www.getbibtex.com/ - for citation generation

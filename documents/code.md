# Notes on code 

Always going need a balance struck between working on detail that improves automation, and meeting project goals.

## shrub-height

* https://github.com/ukceh-rse/shrub-height

Script collections which need run manually in sequence are a good candidate for wrapping in `dvc` pipelines.

Basis for making this `pip` installable as a package, even if a lot of it is designed to be run from the commandline.

Minimal tests for any code that we touch, especially focused on the modelling stages 

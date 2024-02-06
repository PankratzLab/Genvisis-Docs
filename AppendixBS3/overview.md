# Overview

Genvisis can read data that is located in an Amazon S3 environment. This is useful for storing **.sampRAF** and **.mdRAF** files after they have been generated from source files, as they may be dozens or hundreds of gigabytes in size. Genvisis cannot write to files that are stored in an S3 environment, so **.sampRAF** and **.mdRAF** files should be moved after the steps that create these files have been run (e.g., Parse Sample Files or Transpose Marker Files to Sample Files).

This section does not explain how to set up an S3 environment, only how to work with an existing one.

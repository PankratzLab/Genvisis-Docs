# Link Genvisis to an S3 Environment

  .sampRAF and .mdRAF files can be stored in an S3 environment and still read by Genvisis.
Since samples/ and transposed/ account for the majority of space used by a project, storing sample data with S3 is a useful way to free up space in your working environment while still being able to run projects.
Open the properties file of your Genvisis project and edit the sample and marker data directories to point to the S3 environment:

SAMPLE\_DIRECTORY=s3://myNewBucket/remoteFolder/Samples/./
MARKER\_DATA\_DIRECTORY=s3://myNewBucket/remoteFolder/Transposed/./


Note the ./ at the end of the path.  This is necessary to establish the connection.
If you open the properties window in the Genvisis GUI and save any changes there, the double slash after s3: will be reduced to one slash by the auto formatting.  This will break the connection.  You will need to open the properties file in a text editor and add the double slashes.

## Upload Files with S3

### view list of commands
s3cmd -h

### make a bucket
s3cmd mb s3://myNewBucket/

### list contents of bucket
s3cmd ls s3://myNewBucket/

### upload a file to the bucket
s3cmd put ~/localFile.txt s3://myNewBucket/

### upload a folder to the bucket
### will place contents of localFolder into myNewBucket
S3cmd -r put ~/localFolder/ s3://myNewBucket/

### will create a folder in myNewBucket named remoteFolder and place contents of localFolder there
s3cmd -r put ~/localFolder/ s3://myNewBucket/remoteFolder/

### download file from bucket
s3cmd get s3://myNewBucket/localFile.txt ~/

### delete a file from the bucket
s3cmd del s3://myNewBucket/localFile.txt

### delete a folder from the bucket
S3cmd -r del s3://myNewBucket/remoteFolder/

### matching files will be downloaded/uploaded with the most recent version overwriting the older version
s3cmd sync extras/ s3://myNewBucket/remoteFolder/

### synchronize with verbose output and ignore md5 checksum errors
s3cmd -v --no-check-md5 sync extras/ s3://myNewBucket/remoteFolder/

	
Note: Buckets have a flat structure instead of a hierarchical one.  This means that the traditional folder structure doesn’t actually exist.  All files are stored in the bucket, and any “folders” are part of the file name.  
Eg. s3://myNewBucket/remoteFolder/sample.cnv is a file named remoteFolder/sample.cnv stored in the bucket myNewBucket.  When navigating a bucket, the folders that are shown are just for user convenience and don’t actually exist.  To create a “folder” within a bucket, put a file with the folder name as a prefix.

If you receive md5 checksum errors while syncing, this may be due to a bug in s3cmd and not an actual difference in files.
https://stackoverflow.com/questions/13390271/aws-s3-s3cmd-warning-md5-signatures-do-not-match-what-do
sync will repeatedly download/upload files when md5 checksums don’t match.
This can be alleviated with -no-check-md5
The sync command will also run much faster without md5 checks.  It will compare file sizes and dates instead.
The --no-check-md5 flag is the only way to sync directories with terabytes of data; however, it’s also important to verify the md5s afterward. 
This can be done manually after the fact since s3cmd is silent and can take days to run, and thus will hit any time limits.  
S3 saves large files in chunks and reports an md5 of all the chunks’ md5s. 
s3md5.sh can be used to reproduce this process:

s3cmd ls -l s3://myNewBucket/remoteFolder/ABC123.*
2018-04-05 21:43 18.7911312943G  688f06319ee675b1a1b6f6325ea272c9-19  STANDARD  s3://myNewBucket/remoteFolder/ABC123.recab.cram
2018-04-05 21:43 1605.02734375k  8369610020c9247dbfd89a41d5cb3403  STANDARD  s3://myNewBucket/remoteFolder/ABC123.recab.cram.crai

md5sum ABC123.recab.cram
130a7f34b12dfa3d4187eb76b49e4ff0  ABC123.recab.cram

md5sum ABC123.recab.cram.crai
8369610020c9247dbfd89a41d5cb3403  ABC123.recab.cram.crai

s3md5.sh 1024 ABC123.recab.cram
688f06319ee675b1a1b6f6325ea272c9-19


You’ll need to know what chunk size was used to upload the file. You can double check what your multipart_chunk_size_mb is in ~/.s3cfg but it should be the default value of 1024. The -19 extension in the md5 checksum signifies the chunk count.

# Create a Bucket and Grant Users Access

1. Create a bucket with **s3cmd mb s3://myNewBucket/**
2. Set permissions for each [ID] that you want to have access to the bucket:
s3cmd --acl-grant=full_control:[ID] setacl s3://[BUCKET]
s3cmd -r --acl-grant=full_control:[ID] setacl s3://[BUCKET]/


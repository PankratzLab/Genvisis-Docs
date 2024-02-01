# Set Up Credentials For S3 Access

1. In your home directory, create the sub directory .aws/ and enter it from a terminal.
    * Linux/Mac: $HOME/.aws
    * Windows: C:\Users\username\.aws

2. Run **s3cmd --configure** to be taken through configuration details, most of which should be left as-is.
3. The previous step will create the file **~/.s3cfg**. Rename this file **credentials** (no file extension).
4. Inside the **credentials** file, rename **access_key** and **secret_key** to **aws_access_key_id** and **aws_secret_access_key**, respectively.
5. If you receive an error when creating **.s3cfg**, copy the following text into a new file named **credentials** instead:

[default]
delete_removed = False
dry_run = False
encoding = UTF-8
encrypt = False
follow_symlinks = False
force = False
get_continue = False
gpg_command = /usr/bin/gpg
gpg_decrypt = %(gpg_command)s -d --verbose --no-use-agent --batch --yes --passphrase-fd %(passphrase_fd)s -o %(output_file)s %(input_file)s
gpg_encrypt = %(gpg_command)s -c --verbose --no-use-agent --batch --yes --passphrase-fd %(passphrase_fd)s -o %(output_file)s %(input_file)s
gpg_passphrase = test
guess_mime_type = True
host_base = 
host_bucket = 
human_readable_sizes = Yes
list_md5 = False
log_target_prefix =
preserve_attrs = True
progress_meter = True
proxy_host =
proxy_port = 0
recursive = False
recv_chunk = 1048576
reduced_redundancy = False
multipart_chunk_size_mb = 1024
send_chunk = 1048576
skip_existing = False
socket_timeout = 300
urlencoding_mode = normal
use_https = True
verbosity = WARNING

aws_access_key_id=
aws_secret_access_key=

sharing_address=


6. Edit **host_base** and **host_bucket** 
When running **s3cmd --configure**, you will see

Use "s3.amazonaws.com" for S3 Endpoint and not modify it to the target Amazon S3.
S3 Endpoint [s3. …]:

Use "%(bucket)s.s3.amazonaws.com" to the target Amazon S3. "%(bucket)s" and "%(location)s" vars can be used
if the target S3 system supports dns based buckets.
DNS-style bucket+hostname:port template for accessing a bucket [%(bucket)s.s3. …]:

    a. Set **host_base** to the value in brackets for **S3 Endpoint**.
    b. Set **host_bucket** to the value in brackets for **DNS-style bucket+hostname:port template for accessing a bucket**.
    c. Edit **aws_access_key_id** and **aws_secret_access_key**, both of which will be displayed when running **s3cmd --configure** or can be found with the command **s3info**.
    d. Edit **sharing_address**, which is your user id for the local environment where you are storing the credentials file.

### Discovering Bucket Names

http://BUCKETNAME.s3.amazonaws.com/FILENAME.ext 

or

http://s3.amazonaws.com/BUCKETNAME/FILENAME.ext

---

### Listing the Contents of Buckets

`curl http://BUCKETNAME.s3.amazonaws.com/`

`aws s3 ls s3://BUCKETNAME/ --no-sign-request`

The option --no-sign-request allows you to request data from S3 without being an AWS Customer. 

---


### Downloading Objects

Downloading an object from S3 is also easy. You can use curl:

`curl http://irs-form-990.s3.amazonaws.com/201101319349101615_public.xml`

or the AWS CLI:

`aws s3 cp s3://irs-form-990/201101319349101615_public.xml <destination> --no-sign-request`

Note the two different URIs for an object. Objects can be addressed with http:// or via s3://



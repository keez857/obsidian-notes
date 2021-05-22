We can now go to 10.200.100.100/resources

We already have Thomas' creds from earlier

user: Thomas
pass: i<3ruby

We now reach the upload page.

We need to bypass the two filters discussed earlier.

The first one can be bypassed by changing the extension to `.jpeg.php`

The second getimagesize() filter we will need to use exiftool

We will also need to bypass AV on Thomas' machine
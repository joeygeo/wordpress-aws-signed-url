# AWS Signed URL Plugin #

## Introduction ##
This plugin will generate a Signed URL to enable private content to be served through Amazon CloudFront. A CloudFront
key pair has to be created to configure the plugin and the CloudFront distribution configured appropriately. 
Full details of this process can be found in the 
[AWS documentation](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/PrivateContent.html)

This plugin does not manage the process of getting Media Assets on to Amazon S3 or modify the Domain name for AWS based
media. In order to do that a plugin such as Delicious Brains' [WP Offload S3](https://wordpress.org/plugins/amazon-s3-and-cloudfront/)
should be used.


## How To Setup ##
* Download zip of this repo, and install it as a plugin to your wordpress site.
* Activate the plugin, and visit the plugin's Settings page
  
  ![image](https://github.com/coversine/wordpress-aws-signed-url/assets/12219781/78a899c2-18de-43b0-8d74-e8174f0820e7)

* Enter the Cloudfront Key Pair ID, which is available from the AWS Console => Cloudfront => Key Management | Public Keys
* Place the private key file (in PEM format) in a safe location of website storage; ideally above the root folder, so its not available to internet.
* Provide the file path of above private key file into the plugin settings.
* As third option to settings, you can specify a default expires value for any url generated by this plugin.

## How To Use ##
* Plugin provides a shortcode to sign the cloudfront urls: `[wpsign minutes=3]https://duu6jstwl.cloudfront.net/myimage.png[/wpsign]`
* Above will automatically resolve to a signed url in frontend.
* The `minutes` argument is optional; if its missing, then the default plugin setting for URL Lifetime will be used. 

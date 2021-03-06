# AWS::CloudFront::Distribution Origin<a name="aws-properties-cloudfront-distribution-origin"></a>

A complex type that describes the Amazon S3 bucket, HTTP server \(for example, a web server\), Amazon MediaStore, or other server from which CloudFront gets your files\. This can also be an origin group, if you’ve created an origin group\. You must specify at least one origin or origin group\.

For the current quota \(limit\) on the number of origins or origin groups that you can specify for a distribution, see [Quotas](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cloudfront-limits.html) in the *Amazon CloudFront Developer Guide*\.

**Note**  
If you use CloudFormation to create a CloudFront distribution and an S3 bucket origin at the same time, the distribution might return `HTTP 307 Temporary Redirect` responses for up to 24 hours\. It can take up to 24 hours for the S3 bucket name to propagate to all AWS Regions\. When the propagation is complete, the CloudFront distribution will automatically stop sending these redirect responses; you don’t need to take any action\. For more information, see [Why am I getting an HTTP 307 Temporary Redirect response from Amazon S3?](http://aws.amazon.com/premiumsupport/knowledge-center/s3-http-307-response/) and [Temporary Request Redirection](https://docs.aws.amazon.com/AmazonS3/latest/dev/Redirects.html#TemporaryRedirection)\.

## Syntax<a name="aws-properties-cloudfront-distribution-origin-syntax"></a>

To declare this entity in your AWS CloudFormation template, use the following syntax:

### JSON<a name="aws-properties-cloudfront-distribution-origin-syntax.json"></a>

```
{
  "[CustomOriginConfig](#cfn-cloudfront-distribution-origin-customoriginconfig)" : [CustomOriginConfig](aws-properties-cloudfront-distribution-customoriginconfig.md),
  "[DomainName](#cfn-cloudfront-distribution-origin-domainname)" : String,
  "[Id](#cfn-cloudfront-distribution-origin-id)" : String,
  "[OriginCustomHeaders](#cfn-cloudfront-distribution-origin-origincustomheaders)" : [ [OriginCustomHeader](aws-properties-cloudfront-distribution-origincustomheader.md), ... ],
  "[OriginPath](#cfn-cloudfront-distribution-origin-originpath)" : String,
  "[S3OriginConfig](#cfn-cloudfront-distribution-origin-s3originconfig)" : [S3OriginConfig](aws-properties-cloudfront-distribution-s3originconfig.md)
}
```

### YAML<a name="aws-properties-cloudfront-distribution-origin-syntax.yaml"></a>

```
  [CustomOriginConfig](#cfn-cloudfront-distribution-origin-customoriginconfig): 
    [CustomOriginConfig](aws-properties-cloudfront-distribution-customoriginconfig.md)
  [DomainName](#cfn-cloudfront-distribution-origin-domainname): String
  [Id](#cfn-cloudfront-distribution-origin-id): String
  [OriginCustomHeaders](#cfn-cloudfront-distribution-origin-origincustomheaders): 
    - [OriginCustomHeader](aws-properties-cloudfront-distribution-origincustomheader.md)
  [OriginPath](#cfn-cloudfront-distribution-origin-originpath): String
  [S3OriginConfig](#cfn-cloudfront-distribution-origin-s3originconfig): 
    [S3OriginConfig](aws-properties-cloudfront-distribution-s3originconfig.md)
```

## Properties<a name="aws-properties-cloudfront-distribution-origin-properties"></a>

`CustomOriginConfig`  <a name="cfn-cloudfront-distribution-origin-customoriginconfig"></a>
A complex type that contains information about a custom origin or an Amazon S3 bucket that is configured as a static website\. If the origin is an Amazon S3 bucket that is *not* configured as a static website, use the `S3OriginConfig` element instead\.  
*Required*: Conditional  
*Type*: [CustomOriginConfig](aws-properties-cloudfront-distribution-customoriginconfig.md)  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`DomainName`  <a name="cfn-cloudfront-distribution-origin-domainname"></a>
 **Amazon S3 origins**: The DNS name of the Amazon S3 bucket from which you want CloudFront to get objects for this origin, for example, `my-aws-bucket.s3.amazonaws.com`\. For S3 buckets configured as a static website, use `CustomOriginConfig` instead\.  
For more information about specifying this value for different types of origins, see [Origin Domain Name](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-values-specify.html#DownloadDistValuesDomainName) in the *Amazon CloudFront Developer Guide*\.  
Constraints for Amazon S3 origins:  
+ If you configured Amazon S3 Transfer Acceleration for your bucket, don't specify the `s3-accelerate` endpoint for `DomainName`\.
+ If you configured your bucket as a static website, use `CustomOriginConfig` instead\.
+ The bucket name must be between 3 and 63 characters long \(inclusive\)\.
+ The bucket name must contain only lowercase characters, numbers, periods, underscores, and dashes\.
+ The bucket name must not contain adjacent periods\.
 **Custom Origins**: The DNS domain name for the HTTP server from which you want CloudFront to get objects for this origin, for example, `www.example.com`\.   
Constraints for custom origins:  
+  `DomainName` must be a valid DNS name that contains only a\-z, A\-Z, 0\-9, dot \(\.\), hyphen \(\-\), or underscore \(\_\) characters\.
+ The name cannot exceed 128 characters\.
*Required*: Yes  
*Type*: String  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`Id`  <a name="cfn-cloudfront-distribution-origin-id"></a>
A unique identifier for the origin or origin group\. The value of `Id` must be unique within the distribution\.  
When you specify the value of `TargetOriginId` for the default cache behavior or for another cache behavior, you indicate the origin to which you want the cache behavior to route requests by specifying the value of the `Id` element for that origin\. When a request matches the path pattern for that cache behavior, CloudFront routes the request to the specified origin\. For more information, see [Cache Behavior Settings](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-values-specify.html#DownloadDistValuesCacheBehavior) in the *Amazon CloudFront Developer Guide*\.  
*Required*: Yes  
*Type*: String  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`OriginCustomHeaders`  <a name="cfn-cloudfront-distribution-origin-origincustomheaders"></a>
A complex type that contains names and values for the custom headers that you want\.  
*Required*: No  
*Type*: List of [OriginCustomHeader](aws-properties-cloudfront-distribution-origincustomheader.md)  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`OriginPath`  <a name="cfn-cloudfront-distribution-origin-originpath"></a>
An optional element that causes CloudFront to request your content from a directory in your Amazon S3 bucket or your custom origin\. When you include the `OriginPath` element, specify the directory name, beginning with a `/`\. CloudFront appends the directory name to the value of `DomainName`, for example, `example.com/production`\. Do not include a `/` at the end of the directory name\.  
For example, suppose you've specified the following values for your distribution:  
+  `DomainName`: An Amazon S3 bucket named `myawsbucket`\.
+  `OriginPath`: `/production` 
+  `CNAME`: `example.com` 
When a user enters `example.com/index.html` in a browser, CloudFront sends a request to Amazon S3 for `myawsbucket/production/index.html`\.  
When a user enters `example.com/acme/index.html` in a browser, CloudFront sends a request to Amazon S3 for `myawsbucket/production/acme/index.html`\.  
*Required*: No  
*Type*: String  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

`S3OriginConfig`  <a name="cfn-cloudfront-distribution-origin-s3originconfig"></a>
A complex type that contains information about the Amazon S3 origin\. If the origin is a custom origin or an S3 bucket that is configured as a website endpoint, use the `CustomOriginConfig` element instead\.  
*Required*: Conditional  
*Type*: [S3OriginConfig](aws-properties-cloudfront-distribution-s3originconfig.md)  
*Update requires*: [No interruption](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html#update-no-interrupt)

## See Also<a name="aws-properties-cloudfront-distribution-origin--seealso"></a>
+  [Origin](https://docs.aws.amazon.com/cloudfront/latest/APIReference/API_Origin.html) in the *Amazon CloudFront API Reference* 
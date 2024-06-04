## Overview

Hosting a static website on S3 is a cost-effective and scalable solution, ideal for blogs, portfolios, documentation sites, and more.

## Introduction
This README provides instructions on how to create a static website hosted on Amazon S3 (Simple Storage Service) by the process of adding an S3 bucket using Route 53 for domain routing. Route 53 is Amazon Web Services' highly available and scalable Domain Name System (DNS) web service.

## Prerequisites
Before you begin, ensure you have the following:
- An AWS account with permissions to create Route 53 hosted zones and manage S3 buckets.
- A registered domain name that you want to associate with your S3 bucket.

## Steps to Create S3 Bucket for Static Website Hosting

**Step 1** : Creating a S3 Bucket
To create a bucket
1. Sign in to the AWS Management Console and open the Amazon S3 console at
2. Choose Create bucket.
3. Enter the Bucket name.
4. Choose the Region where you want to create the bucket.
  Choose a Region that is geographically close to you to minimize latency and costs,
  or to address regulatory requirements. The Region that you choose
  determines your Amazon S3 website endpoint. For more information, see Website endpoints.
5. To accept the default settings and create the bucket, choose Create.
log_ing

<img width="855" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/77fb7e1c-11b6-404a-989c-8f361ce06ee5">

**Step 2**: Enable static website hosting
To enable static website hosting
1. In the Buckets list, choose the name of the bucket that you want to enable static website hosting for.
choose bucket

3. Choose Properties.
choose properties

3.Under Static website hosting, choose Edit.
select staic web hosting

4. Choose Use this bucket to host a website.
5. Under Static website hosting, choose Enable.
enable hosting

7. In Index document, enter the file name of the index document, typically index.html.
The index document name is case sensitive and must exactly match the file name of the HTML index document that you plan to upload to your S3 bucket. When you configure a bucket for website hosting, you must specify an index document. Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders

8. (Optional) To provide your own custom error document for 4XX class errors, in Error document, enter the custom error document file name.
The error document name is case sensitive and must exactly match the file name of the HTML error document that you plan to upload to your S3 bucket. If you don't specify a custom error document and an error occurs, Amazon S3 returns a default HTML error document.

9. (Optional) If you want to specify advanced redirection rules, in Redirection rules, enter JSON to describe the rules.
For example, you can conditionally route requests according to specific object key names or prefixes in the request.

option

10. Choose Save changes.
Amazon S3 enables static website hosting for your bucket. At the bottom of the page, under Static website hosting, you see the website endpoint for your bucket.

select staic web hosting

12. Now scorll down and Under Static website hosting, note the Endpoint.
The Endpoint is the Amazon S3 website endpoint for your bucket. After you finish configuring your bucket as a static website, you can use this endpoint to test your website.

note endpoints
<img width="485" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/7ff5f29a-be74-454c-be72-e2477779fb42">


**Step 3**: Edit Block Public Access settings
By default, Amazon S3 blocks public access to your account and buckets. If you want to use a bucket to host a static website, you can use these steps to edit your block public access settings.

1. Choose the name of the bucket that you have configured as a static website.
2. Choose Permissions.
choose permission

3. Under Block public access (bucket settings), choose Edit.
permission edit

4. Clear Block all public access, and choose Save changes.
permisson diselectt and save changes
<img width="763" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/f39dcff9-3698-44c0-a020-d5125ac669ad">


**Step 4**: Add a bucket policy that makes your bucket content publicly available
1. Under Buckets, choose the name of your bucket.
2. Choose Permissions.
3. Under Bucket Policy, choose Edit.
bucket policy

4. To grant public read access for your website, copy the following bucket policy, and paste it in the Bucket policy editor.
                    {
    "Version": "2012-10-17",
    "Id": "Policy1717472412383",
    "Statement": [
        {
            "Sid": "Stmt1717472407772",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::mytestdevops.com/*"
        }
    ]
}
<img width="250" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/2e6d4c57-cc27-4e3c-a163-8047904f2a52">


5. Choose Save changes.
A message appears indicating that the bucket policy has been successfully added. If you see an error that says Policy has invalid resource, confirm that the bucket name in the bucket policy matches your bucket name. If you get an error message and cannot save the bucket policy, check your account and bucket Block Public Access settings to confirm that you allow public access to the bucket.

**Step 5**: Configure an index document
When you enable static website hosting for your bucket, you enter the name of the index document (for example, index.html). After you enable static website hosting for the bucket, you upload an HTML file with this index document name to your bucket.

1. Create an index.html file.

2. Save the index file locally.
3 In the Buckets list, choose the name of the bucket that you want to use to host a static website.
choose bucket

4. Enable static website hosting for your bucket, and enter the exact name of your index document (for example, index.html).
5. To upload the index document to your bucket, do one of the following:
a) Drag and drop the index file into the console bucket listing. b) Choose Upload, and follow the prompts to choose and upload the index file.

<img width="839" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/f3170fdb-b51c-40d9-9665-b313fad35623">

Step 6: Test your website endpoint
At the bottom of the page, under Static website hosting, choose your Bucket website endpoint.
<img width="706" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/d8efd5f8-8f95-4a1c-99f8-ccd0839d64c8">

 ## output 1****** : **with out Route 53 **
<img width="758" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/2b56924a-bf2c-4a1b-8703-de8e4ba54635">

Follow below steps to use route 53 
6 **Create a Route 53 Hosted Zone:**
    - Navigate to the Route 53 service in the AWS Management Console.
    - Click on "Create hosted zone."
    - Enter your domain name and click "Create."
    <img width="751" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/14691885-0042-47bb-8300-9d852f626a45">


7. **Add a Record Set:**
    - Inside your hosted zone, click on "Create record set."
    - Enter your subdomain (if applicable) and select "Alias" as the type.
    - Choose your S3 bucket from the dropdown list.
    - Save the changes.
    - <img width="661" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/c704b086-d303-4139-8d81-ca3916e8a049">


8. **Configure DNS Records:**
    - Depending on your requirements, you may want to configure additional DNS records such as MX records for email services, TXT records for SPF/DKIM verification, etc. Follow the prompts in Route 53 to add these records.
    - <img width="671" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/5810c1b9-730b-4582-a05d-53d8ba6c9aa1">


9. **Wait for DNS Propagation:**
    - It may take some time for the changes to propagate through the DNS system. DNS propagation typically takes a few minutes to several hours.

10. **Test Your Website:**
    - Once DNS propagation is complete, you should be able to access your website using the domain name you configured.
    - 
      ## Output after using Route 53
      <img width="814" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/e032f7c8-20be-45ae-af63-c0b525b80737">

##  Textual representation

<img width="243" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/2c47d659-ec03-46ac-8154-8c447b71c00b">

            

* Route 53 now resolves requests for the domain "mytestdevops.com".
* S3 Bucket Hosting serves the content for "mytestdevops.com".
The flow remains the same, with the user's browser making requests to Route 53, which then resolves the domain to the S3 bucket hosting the static website files. Finally, the static content is rendered in the user's web browser.

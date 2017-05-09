---
title: "Enabling HTTPS Engagement Tracking on SparkPost"
description: "SparkPost supports HTTPS engagement tracking for customers via self-service for all SparkPost customers. To enable SSL engagement tracking for a domain, additional configuration for SSL keys is required."
---

## Overview

SparkPost supports HTTPS engagement tracking for customers via self-service for all SparkPost customers. To enable SSL engagement tracking for a domain, additional configuration for SSL keys is required.

## Configuring SSL Certificates

In order for HTTPS engagement tracking to be enabled on SparkPost, our service needs to present a valid certificate that will be trusted by the email recipient’s browser.  SparkPost does not manage certificates for customer engagement tracking domains, as we are not the record owner for our customers’ domains. 

As a workaround, you may use a Content Delivery Network (CDN) service, such as CloudFlare or Fastly to manage certificates and keys for any custom engagement tracking domains you configure.  These services forward traffic onwards to SparkPost so that HTTPS tracking can be performed. 

## Step by Step Guide with CloudFlare

The following is a sample guide for use with CloudFlare; please note, the steps to configure your chosen CDN will likely differ from CloudFlare in workflow. Please refer to your CDN's documentation and contact their respective support departments if you have any questions.

1.	Create CloudFlare account
2.	Go to “DNS” tab on the CloudFlare UI
3.	Add domain and then add the following Cloudflare NS records:
  
  	NS	aron.ns.cloudflare.com
	
  	NS	peyton.ns.cloudflare.com (these values can be found under the DNS tab on the Cloudflare UI) 

	**Example:**

	Using the domain "isaackim.info", below is a command line DIG command to confirm that the NS records have been updated to reflect the required changes:

![](media/ios-universal-links/UL-workflow-final_original.png)

4. Add a new CNAME entry that points your domain to sparkpost.com

**Example:**

Using an engagement tracking domain of "isaackim.info" in SparkPost, the appropriate CNAME record under the DNS tab of CloudFlare has been added.

5. Navigate to the Page Rules settings for the domain.
6. Create a page rule for the domain that sets SSL to “Full”. This is required for how CloudFlare will validate the certificate on the origin. 
	
More information on SSL options for Cloudflare can be found [here](https://support.cloudflare.com/hc/en-us/articles/200170416). 

7. Turn the page rule "on."
8. Reach out to SparkPost Support and request that HTTPS engagement tracking be enabled on your account. They will verify the configuration and enable the setting on your account.

## Additional Resources for Content Delivery Networks

For a list of CDN providers (any of which can integrate with SparkPost to enable HTTPS engagement tracking), this [page](http://www.cdn-advisor.com/articles/).
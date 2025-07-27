# Amazon AMI charges are billed separately from AWS infrastructure charges

![amazon_web_service_logo_1](amazon_web_service_logo_1.png)

This post lists the thread from a case I opened with Amazon to get clarity on whether AMI charges are billed separately from AWS infrastructure charges.

**Thread**

**Can I use the d2.8xlarge FPGA Developer AMI instance for free?**

Under Contact Us at \[[link](http://aws.amazon.com/marketplace/help/contact-us?ref_=footer_nav_contact_us)\]

Regarding: Account and Billing Support

Service: Marketplace

Category: Maketplace Buyer Request

Subject: Can I use the d2.8xlarge FPGA Developer AMI instance for free?

Description:

I would like to use the FPGA Developer AMI instance listed at:

[https://aws.amazon.com/marketplace/server/procurement?productId=40257ab5-6688-4c95-97d1-e251a40fd1fc](http://aws.amazon.com/marketplace/server/procurement?productId=40257ab5-6688-4c95-97d1-e251a40fd1fc) 

I am currently in the "free tier."

From [https://aws.amazon.com/s/dm/optimization/server-side-test/free-tier/free_o/](http://aws.amazon.com/s/dm/optimization/server-side-test/free-tier/free_o/) I see that a Free Tier qualifies for:

"750 hours of Amazon EC2 Linux t2.micro instance usage (1 GiB of memory and 32-bit and 64-bit platform support) – enough hours to run continuously each month\*"

On

[https://aws.amazon.com/marketplace/server/procurement?productId=40257ab5-6688-4c95-97d1-e251a40fd1fc](http://aws.amazon.com/marketplace/server/procurement?productId=40257ab5-6688-4c95-97d1-e251a40fd1fc)

...all of the tiers are listed as $0 Software/hr.

So can I use any of these for free? How many hours can I use them for free?

Answer

Hi there,

I understand you'd like to use the FPGA Developer AMI, and I'm happy to provide more information about the costs. With Marketplace AMIs, the software charges are billed separately from the AWS Infrastructure charges.

Since the FPGA AMI has a software charge of $0, that means you will not be charged for the AMI regardless of instance type, however, there are still charges for the instance itself. Your account is covered by the Free Tier, which means that you could run the FPGA AMI on a t2.micro instance for 750 hours a month for free.

If you used a d2.8xlarge instance, this would not be covered under the Free Tier, so you would accrue charges for the d2.8xlarge instance, but not for the FPGA AMI itself.

Please let us know if you have any questions!

Best regards,

Jude Y.

Amazon Web Services

**References**

AWS image from \[[link](http://aws.amazon.com/)\] via Google image search
### Step 1: Request a Certificate in the AWS Management Console

1. **Login to AWS Console:**
    
    - Go to the [AWS Management Console](https://aws.amazon.com/console/).
    - Navigate to **Services** and choose **Certificate Manager** under the "Security, Identity & Compliance" section.
2. **Request a New Certificate:**
    
    - In ACM, click **Request a certificate**.
3. **Choose the Certificate Type:**
    
    - Choose **Request a public certificate** and click **Next**.
4. **Enter Domain Name:**
    
    - Under **Domain Name**, type the domain name you want to secure, e.g., `example.com`.
    - You can add additional names (like `www.example.com`) if needed.
5. **Select Validation Method:**
    
    - Choose **DNS validation**. This is the simplest method to validate your domain ownership.
6. **Review and Confirm:**
    
    - Review the request and click **Confirm and request**.

### Step 2: Validate Domain Ownership via DNS

1. **Get Validation Information:**
    
    - After requesting the certificate, you’ll be taken to the **Validation** page.
    - For DNS validation, ACM will provide a CNAME record that you need to add to your DNS settings.
    
    The CNAME record will look something like this:
    
    - **Name:** `_xyz1234.example.com.`
    - **Value:** `_abcdef.acm-validations.aws.`
2. **Add the CNAME Record to Your DNS Provider:**
    
    - Go to your DNS provider (e.g., Route 53, GoDaddy, etc.).
    - Add a new **CNAME record** with the provided **Name** and **Value**.
        - For **Name**, enter `_xyz1234.example.com.`
        - For **Value**, enter `_abcdef.acm-validations.aws.`
    
    If you’re using **Amazon Route 53** as your DNS provider, you can add the record directly from the ACM console:
    
    - In ACM, under **Validation**, you will see a button for **Create record in Route 53**. Click it, and ACM will automatically add the CNAME record for you.
3. **Wait for DNS Propagation:**
    
    - It can take some time for the DNS record to propagate, anywhere from a few minutes to an hour.
4. **Certificate Status:**
    
    - Once the CNAME record has propagated, AWS will automatically validate the domain ownership.
    - You can monitor the status of your certificate request in ACM. When the validation is complete, the status will change to **Issued**.

### Step 3: Use the Certificate

Once your certificate is issued, you can use it with AWS services like Elastic Load Balancer (ELB), CloudFront, etc.

For example, to associate it with an ELB:

1. **Navigate to Elastic Load Balancing:**
    
    - Go to the **EC2** dashboard and click on **Load Balancers**.
2. **Modify the Load Balancer:**
    
    - Select your load balancer and click **Listeners**.
    - Click **View/edit listeners**.
    - Add an **HTTPS** listener on port 443 (if not already added).
    - Under the **SSL Certificate** section, select the certificate you just created from the drop-down list.
3. **Save Changes:**
    
    - Click **Save** to associate the certificate with your load balancer.
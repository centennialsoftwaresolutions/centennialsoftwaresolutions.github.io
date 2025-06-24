# Connect a Device to AWS through a MachineQ Gateway Run-through

![flowchart_1](flowchart_1.png)

This post is a run-through of the "Connect your MachineQ device through a MachineQ Output Profile directly to Amazon Web Services (AWS)." doc located at \[[<u><span>link</span></u>](https://docs.dev.machineq.net/docs/mq-central/aws.html)\]. Using a **Guppy** from digital Matter and **MachineQ Multi-Tech MultiConnect® Conduit™** Access Point.

**<u><span>Before you Start</span></u>**

Connect your Guppy to your MachineQ Multi-Tech MultiConnect® Conduit™ Access Point using \[[<u><span>these</span></u>](https://www.centennialsoftwaresolutions.com/blog/lora-guppy-care-and-feeding)\] instructions.

**<u><span>Steps</span></u>**

> **Create a Thing on AWS**

> 1\. Navigate to, and sign in to your AWS account.

I. Sign in at \[[<u><span>link</span></u>](https://signin.aws.amazon.com/)\]

**Note**: if you don't have an account you can create one on the same page. A **Free** account is fine.

II. (A) Enter your **AWS Email address** and click (B) **Next**

![enter_aws_email_adress_2](enter_aws_email_adress_2.png)

III. (A) Enter your **Password** and click (B) **Next**

![enter_password_3](enter_password_3.png)

> 2\. Enter the IoT home page by either selecting IoT Core from the AWS services menu, or by searching IoT Core.

I. (A) Enter **IoT Core** and (B) click **IoT Core**

![look_up_iot_core_4](look_up_iot_core_4.png)

II. You may see this page. If you do click **Get started**

![click_get_started_5](click_get_started_5.png)

> 3\. On the left hand side, there will be a menu. Choose **Manage** to expand the menu, and then **Things**.

(A) Click **Manage** then (B) **Things**

![manage_things_6](manage_things_6.png)

> 4\. If this is your first time on AWS, you will see that you do not have any things. Choose **Register a Thing**. If you have created a thing before, choose Create from the top right. Choose Create a single thing.

I. Click **Register a thing**

![register_a_thing_7](register_a_thing_7.png)

II. Click the **Create a single thing** button

![create_single_thing_8](create_single_thing_8.png)

> 5\. Enter a name for the thing, and choose **Next**.

I. Name your device **myDevice\_Guppy**

![add_mydevice_guppy_9](add_mydevice_guppy_9.png)

II. Leave **Apply a type to this thing** unset,

![no_type_selected_10](no_type_selected_10.png)

**Add this thing to a group** unset and

![no_group_set_11](no_group_set_11.png)

**Set searchable thing attributes (optional)** unset

![searchable_thing_attributes_unset_12](searchable_thing_attributes_unset_12.png)

3\. Click the **Next** button

![click_next_13](click_next_13.png)

> 6\. Choose Create certificate.

![create_certificate_14](create_certificate_14.png)

> Click on the links to download the **x509 certificate**, **public key**, and **private key**. Save these files to a location you can remember, you will need to enter them into MachineQ. Also download the **root CA for AWS**. Choose **Activate**, and then **Attach a policy**.

I. Create a folder on your PC called **c:\\awscerts**

II. (A) Click to download the **certificate for the thing**, (B) the **public key** and (C) the **private key** to the folder

![download_certificate_public_private_15](download_certificate_public_private_15.png)

III. Click **Download** to select a root CA for AWS IoT (takes you to \[[<u><span>this</span></u>](https://docs.aws.amazon.com/iot/latest/developerguide/managing-device-certs.html#server-authentication)\] page) (skipping this step)

![download_root_ca_16](download_root_ca_16.png)

...then click RSA 2048 bit key: Amazon Root CA

![rsa_2048_bit_key_17](rsa_2048_bit_key_17.png)

You'll see:

![certificate_18](certificate_18.png)

Save this file (AmazonRootCA1.pem at \[[<u><span>link</span></u>](https://www.amazontrust.com/repository/AmazonRootCA1.pem)\]) to **c:\\awscerts**

IV. Click **Activate**

![activate_19](activate_19.png)

You'll see:

![certificate_activated_20](certificate_activated_20.png)

...then the Activation notification disappears:

![activation_notification_disappears_21](activation_notification_disappears_21.png)

Note: you can click **Deactivate** then **Activate** again. You'll see notifications each time.

V. Click **Attach a policy**

![attach_a_policy_22](attach_a_policy_22.png)

Neither 7 or 8 apply for me (yet):

> 7\. Once on the policy screen, choose Create a new policy. 8\. On the Create a policy page, in the Name field, type a name for the policy. In the Action field, type iot:\*. In the Resource ARN field, type \*. Select the Allow check box. This allows your MachineQ Device to publish messages to AWS IoT.

...instead I see:

![policy_page_23](policy_page_23.png)

Click **Register Thing**

![register_thing_24](register_thing_24.png)

I see:

![successfully_registered_your_thing_25](successfully_registered_your_thing_25.png)

Back to 7 and 8:

> 7\. Once on the policy screen, choose Create a new policy. 8\. On the Create a policy page, in the Name field, type a name for the policy. In the Action field, type iot:\*. In the Resource ARN field, type \*. Select the Allow check box. This allows your MachineQ Device to publish messages to AWS IoT.

I. (A) Click **Secure**, (B) click **Policies** and (C) **Create a policy**

![create_a_policy_26](create_a_policy_26.png)

II. Do this:

(A) Name the policy **myDevice\_Guppy\_Policy**

(B) Set **Action** to **iot:\***

(C) Set **Resource ARN** to **\***

(D) Set **Effect** to **Allow**

(E) Click the **Create** button

![define_policy_27](define_policy_27.png)

I saw:

![successfully_created_policy_28](successfully_created_policy_28.png)

> 9\. In the menu on the left, choose Secure, and then Certificates.

![certificates_29](certificates_29.png)

> 10\. In the box for the certificate you created, choose ... to open a drop-down menu, and then choose Attach policy.

Click the **3 dots** and click **Attach policy**

![attach_policy_30](attach_policy_30.png)

> 13\. In the Attach things to certificate(s) dialog box, select the check box next to the thing you created to represent your MachineQ Device, and then choose Attach.

(A) Click the checkbox by **myDevice\_Guppy\_Policy** the click (B) **Attach**

![mydevice_guppy_policy_31](mydevice_guppy_policy_31.png)

I see:

![successfully_attached_policy_32](successfully_attached_policy_32.png)

> 14\. In the left menu, click on Manage. Click on the newly created device. You will see your device information here.

I. (A) Click **Manage** and (B) click **myDevice\_Guppy**

![manege_mydevice_guppy_33](manege_mydevice_guppy_33.png)

I see:

![mydevice_guppy_thing_page_34](mydevice_guppy_thing_page_34.png)

II. Save the **Amazon Resource Name** in a Notepad and save it to **c:\\awskeys** at **ARN.txt**

> 15\. In the left menu, choose Interact. Your Endpoint is found under the HTTPS section. Keep a note if this, you will need to enter it into your MachineQ Output Profile.

I. Click **Interact**

![interact_35](interact_35.png)

I see:

![interact_page_36](interact_page_36.png)

II. Save this string to **https.txt** in **c:\\awskeys**. This will be what you use in the **Endpoint** field.

> **Connect Your AWS Thing to MachineQ**

> Navigate back to Creating an Output Profile from MachineQ.

I. Sign into https://mqcentral.machineq.net/

II. Click **LOG IN**

![log_in_mqcentral_37](log_in_mqcentral_37.png)

III. Enter your **Username** and **Password** and click **SUBMIT**

![enter_machineq_username_and_password_38](enter_machineq_username_and_password_38.png)

IV. Click **Integrations**

![integrations_39](integrations_39.png)

V. Click **ADD OUTPUT PROFILE**

![add_output_profile_40](add_output_profile_40.png)

VI. Click **add aws profile**

![add_aws_profile_41](add_aws_profile_41.png)

VII. Enter **test-aws** for the **Output Profile Name**

![test_aws_output_profile_name_42](test_aws_output_profile_name_42.png)

Steps 3,4,5,6 distill down into:

> 3\. Find your certificate and private key files. They will likely be in your Downloads folder, and be titled like this (certificate number)-certificate.pem.cert, and (certificate number)-private.pem.key. 4\. Right click on your certificate file, and choose Open With. Open with your favorite text editor (for example, Notepad or TextEdit). 5\. Copy all text into the x509 Certificate prompt. This includes the header and footer dashes. created 6\. Open the private key with the text editor, and copy all text into the PrivateKey prompt.

![aws_profiles_43](aws_profiles_43.png)

> 7\. This is an example of a completed profile. Click Submit at the bottom of the screen.

Click **Submit**

![completed_profile_44](completed_profile_44.png)

I see:

![new_output_profile_created_45](new_output_profile_created_45.png)

There is one more instruction missing.

I. Click Devices

![devices_46](devices_46.png)

II. Find your Guppy and click **Details**

![guppy_details_47](guppy_details_47.png)

III. Click **Edit**

![edit_guppy_48](edit_guppy_48.png)

IV. (A) Click the **Output Profile** drop down, (B) click **test-aws** and (C) click **SUBMIT**

![output_profile_test_aws_49](output_profile_test_aws_49.png)

> **Confirm Your Data Through AWS**

> 1\. Confirm that your data is being sent to AWS by navigating back to AWS. 2\. Choose Test on the left hand side.

![click_test_50](click_test_50.png)

> 3\. Go to Subscribe to a topic. Enter # in the Subscription Topic field, and click Subscribe to topic.

(A) Enter **#** and (B) click **Subscribe to topic**

![subscribe_to_topic_51](subscribe_to_topic_51.png)

I see:

![mtqq_client_52](mtqq_client_52.png)

In a few seconds (seen this take a few minutes) I see (Chrome window zoomed out):

![test_working_53](test_working_53.png)

See it working here:

(video_unavalible)

**<u><span>References</span></u>**

-   machineQ MultiConnect Conduit Access Point at \[[<u><span>link</span></u>](https://store.machineq.com/store/products/multiconnect-conduit-ap?taxon_id=10)\] - $200.00 for Ethernet backhaul, $260.00 for AT&T LTE
    
-   Guppy from digital Matter at \[[<u><span>link</span></u>](https://www.digitalmatter.com/Devices/Lorawan-IOT/Guppy-LoRaWAN)\]
    
-   mQCentral docs at \[[<u><span>link</span></u>](https://docs.dev.machineq.net/docs/mq-central/)\]
    
-   machineQ Dashboard at \[[<u><span>link</span></u>](https://mqcentral.machineq.net/dashboard)\]
    
-   machineQ Store at \[[<u><span>link</span></u>](https://store.machineq.com/)\]
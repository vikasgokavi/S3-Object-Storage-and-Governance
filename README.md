# S3-Object-Storage-and-Governance
"S3 Object Storage and Governance" project utilizes Amazon S3 for data storage, access management through permissions and policies, and versioning for compliance.

## OBJECTIVES​:

Create a bucket in Amazon S3​

Add an object to a bucket​

Manage access permissions on an object and a bucket​

Create a bucket policy​

Use bucket versioning​

### PROJECT SCENARIO​

We work for a company using Amazon S3 for data storage. An application residing on an EC2 instance needs to push reporting data to an S3 bucket daily. We are tasked with creating an S3 bucket for our company to use for storing this report data. For a successful deployment, we need to ensure the EC2 instance has enough privileges to be able to upload and retrieve data from the S3 bucket. For security reasons, only the EC2 instance can write data to the S3 bucket. The files in the S3 bucket also require protection against accidental deletion.

## Task 1: Create a bucket​
You are new to Amazon S3 and want to test the features and security of S3 as you configure the environment to hold the EC2 report data. You know that every object in Amazon S3 is stored in a bucket so creating a new bucket to hold the reports is the first thing on your task list.​

In this task, you create a bucket to hold your EC2 report data and then examine the different bucket configuration options.​

At the top-left of the AWS Management Console, on the menu choose S3.​

 You can also search for S3 at the top of the services menu.​

<img width="589" alt="Screenshot 2024-03-23 184447" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/afb15836-6e7f-4c63-bf80-82fc4fd4f691">

1.Choose Create bucket​
Leave Region at its default value. -Selecting a particular region allows you to optimize latency, minimize costs, or address regulatory requirements. Objects stored in a region never leave that region unless you explicitly transfer them to another region.​

 Bucket names must be between 3 and 63 characters long and consist of only lowercase letters, numbers, or hyphens. The bucket name must be globally unique across all of Amazon S3, regardless of account or region, and cannot be changed after the bucket is created. As you enter a bucket name, a help box displays showing any violations of the naming rules. Refer to the Amazon S3 bucket naming rules in the Additional resources section at the end of the lab for more information​
Under the General configuration section, name your bucket: ​

reportbucket(NUMBER)​

 Replace NUMBER in the bucket name with a random number. This ensures that you have a unique name.​

Example Bucket Name - ​

reportbucket7763476​

​<img width="960" alt="Screenshot 2024-03-23 184939" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/561c4622-3a7a-49cc-866b-4d150a70c4df">

2.In the Object Ownership section, configure:​

 ACLs enabled​

 Object writer​

 <img width="960" alt="Screenshot 2024-03-23 190530" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/331700f2-aeac-4374-b3ba-3fe4dc3fcaa4">

 3.Scroll to the bottom and choose Create bucket​

 <img width="960" alt="Screenshot 2024-03-23 190734" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/4f2f21a3-0d0d-4737-b4ac-b029c4376cbe">

 <img width="960" alt="Screenshot 2024-03-23 191044" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/1b26ecf8-dd4e-4037-a722-520f3581f7dc">

 ### Task 2: Upload an object to the bucket​
Now that you have a bucket created for your report data, you are ready to work with objects. An object can be any kind of file: a text file, a photo, a video, a zip file, and so on. When you add an object to Amazon S3, you have the option of including metadata with the object and setting permissions to control access to the object.​

In this task you test uploading objects to your reportbucket. You have a screencapture of a daily report and want to upload this image to your S3 bucket.​

Right-click this link new-report.png, choose Save link as, and save the file locally.​

In the S3 Management Console, find and select the bucket that starts with the name reportbucket and click on the name.​

​<img width="960" alt="Screenshot 2024-03-23 191818" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/d32e4f04-d703-4bc9-896c-4fdbf3e77bdc">

1.Choose Upload​

<img width="960" alt="Screenshot 2024-03-23 192125" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/50fa7652-2e06-4671-900f-1d531b617d7a">


This launches an upload wizard. Use this wizard to upload files either by selecting them from a file chooser or by dragging them to the S3 window.​

2.Choose Add files​

<img width="960" alt="Screenshot 2024-03-23 192315" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/102d4655-909a-48c2-9bcd-35361da6a758">

3.Browse to and select the new-report.png file that you downloaded previously.​

​<img width="960" alt="Screenshot 2024-03-23 192720" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/6b2edde0-d647-4e17-9a61-4048eea3fad6">

4.Scroll down and choose Upload​

​<img width="960" alt="Screenshot 2024-03-23 192817" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/6fcb9316-9848-4abe-810a-9ef3402f2861">

5.Your file is successfully uploaded when the green bar indicating Upload succeeded appears.​

 If the file does not display in the bucket within a few seconds of uploading it, you may need to choose the  refresh button at the top-right.​

6.In the Upload: status section, choose Close.​

​<img width="960" alt="Screenshot 2024-03-23 192938" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/dc638930-fff0-4ddb-9179-88300f7bdaf0">

### Task 3: Manage access permissions on an object and a bucket​.

Make an object public​

Security is a priority in Amazon S3. Before you configure your EC2 instance to connect to the reportbucket, you want to test the bucket and object settings for security.​

In this task, you configure permissions on your bucket and your object to test accessibility.​
First, you attempt to access the object to confirm that it is private by default.​

In the reportbucket overview page, on the objects tab, locate the new-report.png object, and choose the new-report.png file name.​

The new-report.png overview page opens. Notice that the navigation in the top-left updates with a link to return to the bucket overview page.​

In the Object overview section, locate and copy the Object URL link.​

The link should look similar to: https://reportbucket7763476.s3.amazonaws.com/new-report.png​

​<img width="960" alt="Screenshot 2024-03-23 200157" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/ddd88eca-8e77-4b12-a287-f9197d0212e1">

2.Open a new browser tab and paste the Object URL link into the address field, and then press Enter.​

​You receive an Access Denied error. This is because objects in Amazon S3 are private by default.​

Now that you’ve confirmed the default security of S3 is private, you want to test how to make the object publicly accessible.​

<img width="960" alt="Screenshot 2024-03-23 200323" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/30eea3e6-9291-47a3-9edc-a1939971395d">

3.You should still be on the new-report.png Object overview tab.​
Choose the Object actions button and Make public via ACL, which will be the last item in the list.​

Notice the warning Public access is blocked because Block Public Access settings are turned on for this bucket. This error displays because this bucket is configured not to allow public access. The bucket settings override any permissions applied to individual objects. If you want the object to viewable by the general public, you need to turn off Block Public Access (BPA).​
Choose Close to return to the object overview.​

<img width="960" alt="Screenshot 2024-03-23 201455" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/87c3bedb-f04f-41bd-b95f-cbc0fa4f7cd0">

4.Use the navigation at the top to go back to the main reportbucket overview page.​

Choose the Permissions tab.​

​<img width="960" alt="Screenshot 2024-03-23 202221" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/6cf607cf-3bfe-4103-a080-bad10df60c15">

5.Under Block public access (bucket settings), choose Edit to change the settings.​
Deselect the Block all public access option, and then leave all other options deselected.​

Notice that all of the individual options remain deselected. When deselecting all public access, you must then select the individual options that apply to your situation and security objectives. Both ACLs and bucket policies are used later in the lab, so they all remain deselected in this task. In a production environment, it is recommended to use the least permissive settings possible. Refer to the Amazon S3 block public access link in the Additional Resources section at the end of the lab for more information.​

Choose Save changes​

​<img width="960" alt="Screenshot 2024-03-23 202655" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/bd77d411-f333-4f08-97be-b033f1f85b43">

6.A dialogue box opens asking you to confirm your changes. Type ​

confirm​

 in the field, and then choose Confirm​

​<img width="960" alt="Screenshot 2024-03-23 202820" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/566c381c-5a88-4b14-9304-e1002acd3df1">

7.A Successfully edited bucket settings for Block Public Access message displays at the top of the window​
​
<img width="960" alt="Screenshot 2024-03-23 202922" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/8c9861c5-b8e0-4470-93b5-a2f58fdbd5fa">

8.Choose the Objects tab.​

Choose the new-report.png file name.​

On the new-report.png overview page, choose the Object actions button and select Make public via ACL.​

Notice the warning: When public read access is enabled and not blocked by Block Public Access settings, anyone in the world can access the specified objects. This is designed to remind you that if you make the object public then everyone in the world will be able to read the object.​

<img width="960" alt="Screenshot 2024-03-23 204908" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/c9e1c84d-68b1-4d97-8b1e-6a5a28db57e4">

9.Choose Make public and read the warning at the top of the window indicating that it “Failed to edit public access” again this is due to BPA being enabled.​

Choose Close to return to the object overview.​

​<img width="960" alt="Screenshot 2024-03-23 205044" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/b54e26e1-36f2-4733-9432-603e5df012ac">

<img width="960" alt="Screenshot 2024-03-23 205230" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/0c849550-8dcc-4fac-ba6c-7ec5d617aa9a">

10.Return to the other browser tab that displayed Access Denied for the new-report.png and refresh  the page.​
The new-report.png now displays properly because it is publicly accessible.​

Close the web browser tab that displays your new-report.png image and return to the tab with the Amazon S3 Management Console.​

In this example, you granted read access to just one specific object. If you wish to grant access to the entire bucket, you need to use a bucket policy, which is covered later in this lab.​

​<img width="960" alt="Screenshot 2024-03-23 205744" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/b5866fa7-20c1-4f1e-82f0-de2450371eb2">

In the next task, you work with your EC2 instance to confirm connectivity to the S3 bucket.​

### Task 4: Test connectivity from the EC2 instance​
In this task, you connect to your Amazon Elastic Compute Cloud (Amazon EC2) instance to test connectivity and security to the S3 reportbucket.​

You should already be logged into the AWS Managment Console. If not, follow the steps in the Start Lab section to log in to the AWS Management Console.​

On the  menu, choose EC2.​

<img width="960" alt="Screenshot 2024-03-23 210401" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/e066bdd0-3f06-4854-bd04-26b539acd2d0">

1.On the EC2 Dashboard, under the Resources section, choose Instances (running).​

Select  Bastion Host and choose Connect​

<img width="960" alt="Screenshot 2024-03-23 210640" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/334e136a-0225-42ee-bce8-2a432fa95a3d">

2.In the Connect to instance window:​

For Connection method, select Session Manager.​

 Session Manager enables you to connect to the bastion host instance without the need for specific ports to be open on your firewall or Amazon Virtual Private Cloud (Amazon VPC) security group. Refer to AWS Systems Manager Session Manager in the Additional resources section at the end of this lab for more information.​

Choose Connect​

<img width="960" alt="Screenshot 2024-03-23 210801" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/90aaa03e-b48e-4ac5-9af4-4da066919570">

3.A new browser tab or window opens with a connection to the bastion host instance.​ You are now connected to the EC2 instance that holds the reporting application. Because Session Manager uses https port 443, it does not require you to open SSH port 22 to the outside world, you are satisfied with this security feature. Now you want to see how EC2 interacts with your S3 bucket.​ In the bastion host session, enter the following command to change to home directory (/home/ssm-user/): ​cd ~​ The output returns you to the command prompt.​ Enter the following command to verify you are in the home directory:​ pwd​ The output should be:​ /home/ssm-user​ You are now in the ssm-user’s home directory where you will run all of the commands in this lab.​ Enter the following command to list all of your S3 buckets.​ aws s3 ls​ The output should look similar to this:​ 2020-11-11 22:27:28 ql-cf-templates-1603924046-5d95cf473a39fe4e-us-west-2​ 2020-11-11 22:27:49 qltrail-lab-59350-1603924067​ 2020-11-11 22:34:46 reportbucket987987​ You see the reportbucket you created as well as lab auto-generated buckets.​ Note: During the creating of the lab enviornment, both an Instance Profile (which defines who you are for authentication) and a Role (which defines what you can do after you authenticate), have been automatically added for the EC2 instance to allow the EC2 instance to list the S3 buckets and objects.​​

Enter the following command to list all objects in your reportbucket. Remember to change the number at the end of the reportbucket name, to match the name of the bucket you created. ​

​

aws s3 ls s3://reportbucket(NUMBER) ​

​

The command looks similar to this: aws s3 ls s3://reportbucket987987 ​

​

The output should look like this: ​

​

2020-11-11 15:46:34      86065 new-report.png ​

​

There is currently just one object in your bucket called new-report.png. ​

​

Type the following to change directories into the reports directory. ​

​

cd reports ​

​

The output returns you to the command prompt. ​

​

Type the following to list the contents of the directory. ​

​

ls ​

​

The output shows some files created in your reports directory to test the application. ​

​

dolphins.jpg files.zip report-test.txt  report-test1.txt report-test2.txt report-test3.txt  whale.jpg ​

​

Type the following to see if you can copy a file to the S3 bucket. ​

​

aws s3 cp report-test1.txt s3://reportbucket(NUMBER) ​

​

The command looks similar to this: aws s3 cp report-test1.txt s3://reportbucket987987 ​

​

The output indicates an error upload failed. This is because we have read-only rights to the bucket and do not have the permissions to perform the PutObject operation. ​

​

Leave this window open and go back to the AWS Console tab. ​

​

In the next task you create a bucket policy to add the PutOperation. ​

​![image](https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/5ee695dc-d942-40c3-b0a0-31ef4d1b956c)

4.Create a bucket policy​

A bucket policy is a set of permissions associated with an S3 bucket. It is used to control access to an entire bucket or to specific directories within a bucket.​

In this task, you use the AWS Policy Generator to create a bucket policy to enable read and write access from the EC2 instance to the bucket to ensure your reporting application can successfully write to S3.​
Right-click this link sample-file.txt, choose Save link as, and save the file locally.​

Return to the AWS Management Console, go to the menu and select S3.​

​<img width="960" alt="Screenshot 2024-03-23 215606" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/f6b8273a-b49c-47e3-9834-98de52bd3ac5">

5.In the S3 Management Console tab, select the name of your bucket.​

Choose Upload and use the same upload process as in the previous task to upload the sample-file.txt.​

​<img width="467" alt="Screenshot 2024-03-23 215951" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/9be4b450-add0-4bb9-8aaa-975a823cf085">

<img width="960" alt="Screenshot 2024-03-23 220058" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/9b075696-9c1d-4209-b6b9-d991c19737bc">

6.Choose the sample-file.txt file name. The sample-file.txt overview page opens.​

​
<img width="960" alt="Screenshot 2024-03-23 220305" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/1211aa36-5444-4139-b951-62fb451f97be">

7. Under the Object overview section, locate and copy the Object URL link.​

In a new browser tab, paste the link into the address field, and then press Enter.​
Once again, Access Denied will be displayed. You need to configure a bucket policy to grant access to all objects in the bucket without having to specify permissions on each object individually.​

Keep this browser tab open, but return to the tab with the S3 Management Console.​

​
<img width="960" alt="Screenshot 2024-03-23 220346" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/fcf801cd-293c-4bf0-b288-7f6608ad5ca4">

8.Go to Services  > IAM > Roles​

​<img width="960" alt="Screenshot 2024-03-23 220659" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/51a91711-1a5d-4da4-beef-4b3655b4381c">

9.In the Search field type ​

EC2InstanceProfileRole​

This is the Role that the EC2 instance uses to connect to S3.​

<img width="960" alt="Screenshot 2024-03-23 221004" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/adda6ab6-8a91-4839-bdc1-2fe0d7f8542f">

10.Select EC2InstanceProfileRole. On the Summary page, copy the Role ARN to a text file to be used in a later step.​

It should look similar to this: arn:aws:iam::596123517671:role/EC2InstanceProfileRole​

​<img width="960" alt="Screenshot 2024-03-23 221211" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/411d8e86-74a1-441a-8c49-23cb99cca3b3">

11.Choose Services , S3 and return to the S3 Management Console.​

Choose the reportbucket.​

​<img width="960" alt="Screenshot 2024-03-23 221452" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/4917d173-2daa-4c98-be9e-733d80c6548c">

12.In the Permissions tab, scroll to the Bucket Policy section, choose Edit​

A blank Bucket policy editor is displayed. Bucket policies can be created manually, or they can be created with the assistance of the AWS Policy generator.​

 Amazon Resource Names (ARN)s uniquely identify AWS resources across all of AWS. Each section of the ARN is separated by a “:” and represents a specific piece of the path to the specified resource. The sections can vary slightly depending on the service being referenced, but generally follows this format:​

arn:partition:service:region:account-id:resource​

Amazon S3 does not require region or account-id parameters in ARNs, so those sections are left blank. However, the “:” to separate the sections is still used, so it looks similar to arn:aws:s3:::reportbucket987987​

Refer to the Amazon Resource Names (ARNs) and AWS Service Namespaces documentation link in the Additional Resources section at the end of the lab for more information.​
Copy the Bucket ARN to a text file to be used in a later step.​

It is displayed below the Policy examples and Policy generator buttons.​

It looks like this:​

​<img width="960" alt="Screenshot 2024-03-23 222226" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/d33e7da1-467b-496a-b6fb-983d71cd9fcb">

13.Choose Add Statement. The details of the statement you configured are added to a table below the button. You can add multiple statements to a policy.​

<img width="960" alt="Screenshot 2024-03-23 223701" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/dfb56639-214c-4406-9603-8637089a66e9">

14.Choose Generate Policy.​

<img width="960" alt="Screenshot 2024-03-23 223731" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/b5ccc1f0-6f69-4399-ab41-8ac9638bd199">

15.A new window is displayed showing the generated policy in JSON format. It should look similar to:​
Confirm that ​

/*​

 appears after your bucket name as shown in the Resource line in the sample above.​

Copy the policy you created to your clipboard.​

Close the web browser tab and return to the tab with the Bucket policy editor.​

​<img width="960" alt="Screenshot 2024-03-23 223920" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/28b58b36-a2d9-47a8-9c5e-2c9ac7cd225b">


16.Paste the bucket policy you created into the Bucket policy editor.​

Choose Save changes​


<img width="960" alt="Screenshot 2024-03-23 230538" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/22da37f8-18da-4800-b9ca-15e3f15f359a">


17.Return to the AWS Systems Manager (SSM) window. If your session has timed out, reconnect to the SSM using the steps from earlier in the lab.​

Type the following to verify you are in the /home/ssm-user/reports directory.​

pwd​

 The output should be:​

/home/ssm-user/reports​

 Enter the following command to list all objects in your reportbucket. Replace NUMBER with the number you used to create your bucket.​

aws s3 ls s3://reportbucket(NUMBER)​

The command should look similar to this: aws s3 ls s3://reportbucket987987​

 The output should look similar to this:​

sh-4.2$ aws s3 ls s3://reportbucket987987​
2020-11-02 23:20:27      86065 new-report.png​
2020-11-02 23:57:03         90 sample-file.txt​

Type the following to list the contents of the reports directory.​

ls​

 The output returns a list of files.​

Type the following to try coping the report-test1.txt file to the s3 bucket.​

aws s3 cp report-test1.txt s3://reportbucket(NUMBER)​

The command should look like this: aws s3 cp report-test1.txt s3://reportbucket987987​

 The output returns the following:​

upload: ./report-test1.txt to s3://reportbucket987987/report-test1.txt​

Type the following to see if the file successfully uploaded to S3.​

aws s3 ls s3://reportbucket(NUMBER)​

 The output should look similar to this:​

2020-11-11 18:20:23      86065 new-report.png​
2020-11-11 18:32:18         31 report-test1.txt​
2020-11-11 18:20:22         90 sample-file.txt​

You have successfully uploaded (PutObject) a file from the EC2 instance to your S3 bucket.​

Now type the following command to retrieve (GetObject) a file from S3 to the EC2 Instance.​

aws s3 cp s3://reportbucket(NUMBER)/sample-file.txt sample-file.txt​

 The output should look similar to this:​

download: s3://reportbucket987987/sample-file.txt to ./sample-file.txt​

Type the following to see if the file is now in the /reports directory.​

ls​

 The output should look similar to this:​

dolphins.jpg  files.zip  report-test1.txt  report-test2.txt  report-test3.txt  sample-file.txt​

You now see the sample-file.txt in your file list. Congratulations! You have succesfully uploaded and retrieved a file from EC2 to the S3 bucket.​

<img width="960" alt="Screenshot 2024-03-23 233232" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/d439a32d-768c-4d37-a1c4-e7aaadc75213">



18.Return to the browser tab that displayed the Access Denied for the sample-file.txt and refresh  the page.​

The page still displays an error message because the Bucket Policy only gave rights to the principal called EC2InstanceProfileRole.​

<img width="960" alt="Screenshot 2024-03-23 233612" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/66d5f904-e04b-4e3d-ae1e-23a557118eb0">

19.Next, on your own, go back to the policy generator and add another statement to the bucket policy allowing EVERYONE (*), Read access (GetObject). Take a moment to generate this policy which allows both the EC2InstanceProfileRole to have access to the bucket while giving EVERYONE access to read the objects via the browser.​

​<img width="960" alt="Screenshot 2024-03-24 021351" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/2de11fac-9842-47a3-9037-fd10516bcfa0">

20.To test if your policy works, go to your browser with the Access Denied error and refresh it. If you can read the text, then congratulations! Your policy was successful.​

 If not, look at the policy below for help. The modified policy should look like the policy listed below. Notice that there are TWO statements, one with the EC2InstanceProfileRole and one where the Principal is “*” for everyone.​

If you had trouble generating the policy on your own, you can copy the policy below and paste it into the BucketPolicy Editor. Remember to replace the existing EC2InstanceProfileRole ARN in the policy below with the EC2InstanceProfileRole ARN you copied in an earlier step. Ensure that the /* appears at the end of the Bucket ARN. See the last line of the file as an example.​

​Leave the tab open with the sample-file.txt displayed. You will return to this tab in the next task.​

In this task you created a bucket policy to allow specific access rights to your bucket. In the next section you explore how to keep copies of files to prevent against accidental deletion.​

<img width="960" alt="Screenshot 2024-03-24 021647" src="https://github.com/vikasgokavi/S3-Object-Storage-and-Governance/assets/105034318/639e2ff4-ab8a-4e90-83dc-6ced814e78d1">



​

​


​
​


​









​


​


​

​




​






​


​


​


​

​

​






​

​

​
​

​










​


​

​

​



​

​

​


​

​​

​

# script-aws-automatic-Snapshots

![Screen Shot 2023-04-29 at 8 25 29 PM](https://user-images.githubusercontent.com/123271041/235368345-9d5388f9-65da-4c19-adb3-c10de001ca10.png)

Create an EC2 Instance: First, you need to create an EC2 instance that you want to backup regularly. This instance can be of any type and can have any operating system installed. Once you have created the EC2 instance, you need to make sure that you have the necessary permissions to create snapshots of this instance, it will not be authorized by default.
![Screen Shot 2023-04-29 at 8 10 20 PM](https://user-images.githubusercontent.com/123271041/235368206-00907cf1-5171-4874-88d2-e44624e82d76.png)


Create a Tag: To make the EC2 instance identifiable as one of the instances that needs to have a programmed backup, you need to create a tag and assign it to the instance. This tag can be used to identify the instance during the snapshot creation process.

![Screen Shot 2023-04-29 at 8 08 02 PM](https://user-images.githubusercontent.com/123271041/235368217-380b3d57-86cb-4487-830e-b85581dab1c0.png)

Create a Lambda Function: Next, you need to create a Lambda function that will run the code to create EC2 snapshots. You can use any programming language to write the code for the Lambda function, but in this case, you will be using Python. The Lambda function should have the basic permissions to create snapshots.

![Screen Shot 2023-04-29 at 8 15 38 PM](https://user-images.githubusercontent.com/123271041/235368369-48c5b543-b11c-4f66-b466-f34f67707fc8.png)

Change IAM Permissions: In order for the Lambda function to be able to create snapshots, you need to change the IAM permissions on the JSON code and allow snapshot creation. You can do this by adding the necessary permissions to the IAM role associated with the Lambda function.

![Screen Shot 2023-04-29 at 8 12 07 PM](https://user-images.githubusercontent.com/123271041/235368260-b05cdaba-a7ca-4361-8c7e-4637d3af6b1b.png)

To create a CloudWatch trigger for running an EC2 snapshot backup every 24 hours, go to the CloudWatch console and create a new rule with a scheduled expression for the desired time interval. Then, select the EC2 instance and configure the action to create the snapshot. 

![Screen Shot 2023-04-29 at 8 19 34 PM](https://user-images.githubusercontent.com/123271041/235368278-757f7a6d-fdc3-4f02-9f09-b0726a8062c6.png)
Finally, save the rule and wait for it to trigger at the specified time.

![Screen Shot 2023-04-29 at 8 18 09 PM](https://user-images.githubusercontent.com/123271041/235368334-f2c3b9e2-b188-4ced-9863-b3ee814382bb.png)


cloudwatch finalized
Run the Code: Finally, you can let the cloudwatch trigger run the script will invoke the Lambda function that you created in step 3, which will then create snapshots of the EC2 instances that have been tagged in step 2. The script can be scheduled to run at regular intervals to ensure that the EC2 instances are backed up regularly.

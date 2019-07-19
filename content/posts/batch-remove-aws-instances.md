---
title: "How to Batch Remove AWS Instances with Termination Protection Turned On"
date: 2019-06-21T09:42:40-07:00
draft: true
---

I recently got a request to terminate several hundred stopped instances on AWS. My first reaction was this is easy, just go into the GUI console, select all the instances and terminate. This could have been a solution if you have a few instances but selecting hundreds of instances intermingled between those needing termination and those that need to stay around is not exactly trivial. To add to the complexity, most of the instances that are targeted for termination had the termination protection flag turned on.

## Query for all instances to remove
To solve our problem we need to first be able to query for all the instances we plan to remove. In my case I was targeting all the instances in a “stopped” state. Here is the query I ran, which produces a list of instance ID’s.

```bash
$ aws ec2 describe-instances --region us-east-1 --filters \ 
Name=instance-state-name,Values=stopped |  \
jq '.Reservations[] .Instances[] .InstanceId'
```

In the above example you will need aws–cli configured to work with your account and jq. jq is a json processor that makes quick work of retrieving the key-value pairs from the output of aws-cli. The filter I used was to find all instances with instance-state-name=stopped. AWS publishes a myriad of filters to allow you to select exactly what you want. See https://docs.aws.amazon.com/cli/latest/reference/ec2/describe-instances.html for more information about ec2 describe-instances and a list of filters that can be used.

## Remove termination protection
Now that you have a list of instance id’s that are targeted, you will need to remove protection from those instances. To do that we will pipe the first command into a modify-instance-attributes and disable api termination. Here is the full command.

```bash
$ aws ec2 describe-instances --region us-east-1 --filters \ 
Name=instance-state-name,Values=stopped | jq -r  \
'.Reservations[] .Instances[] .InstanceId' | \ 
xargs -t -n1 aws ec2 modify-instance-attribute \ 
--no-disable-api-termination --region us-east-1 \ 
--instance-I
```

## Batch terminate instances
The final step is to terminate all the instances of the original query.

```bash
$ aws ec2 describe-instances --region us-east-1 --filters \ 
Name=instance-state-name,Values=stopped | jq -r \ 
'.Reservations[] .Instances[] .InstanceId' | \ 
xargs -t -n1 aws ec2 terminate-instances --region us-east-1 \ 
--instance-ids
```
If you take a look at the console while you run this the instances will change to a terminating state and you have accomplished removing, in batch, a group of aws instances.

## Conclusion
Removing in batch is fairly straight forward if you have the right tools and knowledge. With the power of aws-cli you can easily query, set attributes, and terminate instances in batch. This solution works on MAC and Linux. If you have windows I would recommend installing cygwin or converting the syntax to PowerShell. 
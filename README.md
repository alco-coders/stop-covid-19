# stop-covid-19
> Running Folding@home and Rosetta@home on your AWS EC2 Spot instance to fight with COVID-19.

This repository contain templates that create an AWS spot instance in an autoscaling group for running either [Folding@Home](https://foldingathome.org/) or [Rosetta@Home](https://boinc.bakerlab.org/) client.

Folding@home is a computing platform to assist disease research, for instance to find a cure for the COVID-19 virus.

Rosetta@home is a distributed computing project for protein structure prediction on the Berkeley Open Infrastructure for Network Computing (BOINC) platform.

# [Folding@Home](/folding.yml)
<details>
<summary>Click to expand!</summary>

The template uses G4-type instances with NVIDIA TESLA T4 GPUs.

The template installs the following software:

 - AWS Deep Learning AMI (Amazon Linux 2)
 - Folding@home client v7.5 latest

Folding@home client is started automatically after instance initialization is complete.
Client runs until the template is removed, auto scaling group tries to keep running a singlr spot instance all the time.
The template bids 100% of on-demand price and instances are unlikely to be reclaimed.
Spot instance pricing varies: expect approximately 60-70% discount for G4 instance type.

## Usage

### Launch from AWS Console

Create stack using the template S3 URL: `https://folding-at-home.s3.amazonaws.com/folding.yml`

| Parameter            | Description |
|----------------------|-------------------------------------------------------------------------------------------------------------|
| `FoldingTeam`        | Folding@home team number (default 2164 for Ukraine)                                                            |
| `FoldingUser`        | Folding@home username                                     |
| `InstanceType`        | EC2 instance type to launch (default is g4dn.xlarge    |

Cost of spot instances may vary by availability zone. Use subnets across different availability zones to give lower cost.

| Region         | Create Stack              |
|----------------|---------------------------|
| Asia Pacific (Mumbai) `ap-south-1` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://ap-south-1.console.aws.amazon.com/cloudformation/home?region=ap-south-1#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| Asia Pacific (Singapore) `ap-southeast-1` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| Asia Pacific (Sydney) `ap-southeast-2` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://ap-southeast-2.console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| Asia Pacific (Tokyo) `ap-northeast-1` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| Asia Pacific (Seoul) `ap-northeast-2`| [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://ap-northeast-2.console.aws.amazon.com/cloudformation/home?region=ap-northeast-2#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| Canada (Central) `ca-central-1` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://ca-central-1.console.aws.amazon.com/cloudformation/home?region=ca-central-1#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| Europe (Frankfurt) `eu-central-1` |[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://eu-central-1.console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| Europe (Ireland) `eu-west-1` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://eu-west-1.console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| Europe (London) `eu-west-2` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://eu-west-2.console.aws.amazon.com/cloudformation/home?region=eu-west-2#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| Europe (Paris) `eu-west-3` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://eu-west-3.console.aws.amazon.com/cloudformation/home?region=eu-west-3#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| South America (São Paulo) `sa-east-1` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://sa-east-1.console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| US East (N. Virginia) `us-east-1` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| US East (Ohio) `us-east-2` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://us-east-2.console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| US West (N. California) `us-west-1`| [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://us-west-1.console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |
| US West (Oregon) `us-west-2` | [![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/review?templateURL=https://folding-at-home.s3.amazonaws.com/folding.yml&stackName=FoldingAtHome) |

### Launch from CLI

Replace `FoldingTeam`, `FoldingUser` and `InstanceType` values:

```sh
aws cloudformation create-stack \
  --stack-name FoldingAtHome \
  --template-url https://folding-at-home.s3.amazonaws.com/folding.yml \
  --parameters \
    ParameterKey="FoldingTeam",ParameterValue="0" \
    ParameterKey="FoldingUser",ParameterValue="Anonymous" \
    ParameterKey="InstanceType",ParameterValue="g4dn.xlarge" \
--capabilities CAPABILITY_IAM
```

### Access Web UI
 * [Using AWS SSM Session Manager](https://aws.amazon.com/blogs/aws/new-port-forwarding-using-aws-system-manager-sessions-manager/)
```sh
# find the instance ID based on Tag Name
INSTANCE_ID=$(aws ec2 describe-instances \
               --filter "Name=tag:Name,Values=FoldingAtHome" \
               --query "Reservations[].Instances[?State.Name == 'running'].InstanceId[]" \
               --output text)
# create the port forwarding tunnel
aws ssm start-session --target $INSTANCE_ID \
                       --document-name AWS-StartPortForwardingSession \
                       --parameters '{"portNumber":["7396"],"localPortNumber":["7396"]}'

Starting session with SessionId: sst-00xxx63
Port 7396 opened for sessionId sst-00xxx63
Connection accepted for session sst-00xxx63.
```

### Installation paths

Folding@home configuration is output to`/etc/fahclient/config.xml` .
Folding progress log output is written to `/var/lib/fahclient/log.txt`.
Show status of the service with `systemctl status FAHClient` .

</details>

## Release History

* 20.4.13
    * Initial version

## Resources

 - [Folding@home COVID-19 efforts](https://github.com/FoldingAtHome/coronavirus)
 - [Manual installation for Folding@home](https://foldingathome.org/support/faq/installation-guides/linux/manual-installation-advanced/)
 - [AWS Deep Learning AMI](https://docs.aws.amazon.com/dlami/latest/devguide/appendix-ami-release-notes.html)
 - [Optimize GPU Settings](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/optimize_gpu.html)

# Credits

 - Inspired by: [Julien Simon Medium post](https://medium.com/@julsimon/running-folding-home-on-amazon-ec2-instances-ce6bb8f84218)
 - Markdown template: [Janne Kataja](https://github.com/jkataja/cfn-foldingathome/blob/master/README.md)

# Meta

This software is provided "as is", without warranty of any kind.

Distributed under the MIT license. See ``LICENSE`` for more information.

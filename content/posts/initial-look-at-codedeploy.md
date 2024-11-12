+++
title = 'Initial Look at CodeDeploy'
date = 2024-11-12T18:47:27+02:00
categories = ['Blog']
series = ["I Guess I'm Doing Cloud Now"]
images = ["https://i.imgur.com/szx3RH1.png"]
+++

I'm slowly but surely collecting individual pieces that eventually will help me
deploy my [portfolio builder app](https://github.com/waseem-medhat/skillstackr)
with a CD pipeline (while following best practices as much as I can). So, I
took a stab at AWS CodeDeploy. As the name implies, it is the service that
deploys code to EC2 or other resources.

In this article, I briefly go over what I learned about CodeDeploy from [this
tutorial in the official
documentation](https://docs.aws.amazon.com/codedeploy/latest/userguide/tutorials-github.html),
which shows how to deploy code from GitHub to an EC2 instance.

## Architecture Overview

There isn't much architecture per se going on here. However, it wasn't
intuitively apparent at first how CodeDeploy works. So, I'll try to summarize
what I found out about the individual pieces work together, which together make
up this diagram:

![CodeDeploy architecture](https://i.imgur.com/k5HniOH.png)

- **Application & deployment group**: these are created via the CodeDeploy
console or the CLI and configured to identify the type of service (e.g., EC2)
and the particular instance(s) on which code will be deployed.

- **Deployments**: within a deployment group, we can create one or more
deployments, and there we specify either an S3 object or a GitHub repo and a
commit ID. What deployments end up doing is defined by an application
specification (AppSpec) file.

- **Revisions**: these are versions of the code to be deployed, which can be
either a particular S3 object or a Git commit ID.

- **AppSpec**: this YAML file is added to the revision and specifies the files
(in the revision) to be deployed, where to deploy them on the target instance,
and any additional hooks (scripts) to run at different stages of the deployment
process.

- **CodeDeploy agent**: that is installed on the target EC2 instance and is
needed to execute deployments.

- **EC2 instance profile**: as with any AWS resource, the necessary IAM
permissions need to be set so that the EC2 instance can access S3 buckets,
install or update the CodeDeploy agent, etc. In this case, it is done through
an IAM role that is attached to the instance.

## Thoughts and Future Implementations

Following this tutorial gave me a good general overview of CodeDeploy. However,
I'd say there are multiple things that need to be considered for a production
app.

### Compilation and CD

The process of deploying code via the console or the CLI is manual. So, some
work is needed to be able to trigger deployments on code push. Moreover, the
deployed code in this tutorial was an HTML file and a bunch of Bash code, but
many languages and frameworks need a compilation step. In that case, a build
step would have to be configured (especially as part of a CD pipeline), and
what would be deployed now is *compiled artifacts*, not source code.

I think most (if not all) of the issues in that regard could be addressed by
GitHub Actions, which can be used to build a CD pipeline that compiles the
code, sends the artifact to an S3 bucket, and possibly trigger a CodeDeploy
deployment which pulls the new revision on S3 into the EC2 instance.

### Infrastructure as Code

Nothing to say here except that further automation, and better documentation,
of this process would be to create the CodeDeploy resources via IaC, e.g.,
CloudFormation or Terraform. I've grown to realize the value of IaC after my
[last hands-on encounter with AWS](/posts/first-end-to-end-aws-project/), and
this is yet another example.

### Least Privilege Permissions

This has been (and surely will continue to be) a consistent theme with AWS. In
this case, the policies used in the tutorial may be a bit too permissive. For
example, the part related to S3 access in the EC2 instance role was included
this policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
      {
          "Action": [
              "s3:Get*",
              "s3:List*"
          ],
          "Effect": "Allow",
          "Resource": "*"
      }
  ]
}
```

The tutorial documentation did, however, recommend in a note that this policy
should be modified so that it can only access the bucket that contains the
revision and the buckets that contain the CodeDeploy agent.

## Final Notes

This has been a summary of my understanding of how CodeDeploy works as well as
some ideas on how to better use it in a production setting. It is probably a
relatively high-level or rudimentary knowledge compared to what the service can
offer, but I think that in my current learning stage, it might make more sense
to learn a little bit about many things and see how they connect together
before going deep. Not to mention that deeper knowledge will come naturally
with practice when the time comes.

Thanks for reading!

* * *

CodeDeploy icon used in the cover photo was obtained from [AWS architecture
icons](https://aws.amazon.com/architecture/icons/)

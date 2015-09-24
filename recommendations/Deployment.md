# Deployment

## Adopt

  - [CloudFormation](http://aws.amazon.com/cloudformation/)
    Useful for initial creation of the software stack and pushing occasional subsequent changes.
    A few examples of resources that can be created with CloudFormation: ELBs,
    ASGs, instance profiles, IAM profiles, S3 buckets, dynamo db tables.
    Think of it as creating a network structure into which your code can be deployed.


  - [CodeDeploy](http://aws.amazon.com/codedeploy/)
    Useful for deploying application code and any accompanying artifacts, agents, scripts, etc
    into an existing software stack, perhaps created with CloudFormation.
    This deals with concepts such as deployment groups, application versions, rollout strategies.


  - [Docker](https://www.docker.com/)

    Docker is largely in use as a replacement for RPMs, to wrap a program in some easily deployable format.
    We believe the ability to specify runtime requirements at development time, and not having to worry about the runtime capabilities of the server is extremely valuable.

  - [Docker Registry](https://docs.docker.com/registry/)

    The registry is the place where Docker images are uploaded at build time, and where they are downloaded from at deployment time. For open-source projects, we use [DockerHub](https://hub.docker.com). For private projects, we use one private registry for each AWS sub-account.

## Assess

  - [CodePipeline ](http://aws.amazon.com/codepipeline/)
  - [EC2 Container Service](http://aws.amazon.com/ecs/)
  - [sbt-codedeploy](https://github.com/gilt/sbt-codedeploy)
  - [AWS Lambda](http://aws.amazon.com/lambda/)

    A nice alternative to deploying/managing service clusters.
    Consider using in places where functionality is very simple, especially if the traffic is low and it's hard to justify the cost of running EC2 nodes all the time.

## Hold
  - [Ionroller](https://github.com/gilt/ionroller/)

    Ionroller is an exploration into 'immutable deploys'. It trades off speed of initial deploy (which involves new machines/elbs/etc being created) with the ability to:
      - test independently in production
      - quickly roll over to a different stack, enabling [Blue Green Deploys](http://martinfowler.com/bliki/BlueGreenDeployment.html)

    As of September 2015, we have open-sourced ION-roller, and are no longer actively working on it (the team behind ION-roller is now working on personalisation) Many teams are moving to adopt mst and CodeDeploy as an alternative. Additionally, we've worked with AWS Code-* product team to get the blue-green deployment concepts into CodeDeploy. As a result, we are recommending a HOLD on ION-Roller.


  - Ioncannon (Closed Source)

    The initial premise of Ioncannon, to deploy to a staging environment, run a bunch of functional tests, and promote to production automatically has had some difficulties.
    Particularly, maintaining said stage environment has proven challenging and not particularly efficient. Other methodologies are being explored in tooling above.

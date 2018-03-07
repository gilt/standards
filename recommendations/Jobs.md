# Jobs

## Adopt

 - We do not have a recommendation for Adoption right now; the existing job system is operational but we've moved it to HOLD (see below). We recommend that teams that need new jobs investigate alternative approaches listed in the Assess section. The decision of what job system should be assessed and pursued should be made at a department level.

## Trial

  - [Sundial](https://github.com/gilt/sundial)
    Scheduled workflow engine leveraging ECS and/or AWS Batch to run jobs in docker containers with dependency graph management.

  - [AWS Batch](https://aws.amazon.com/batch/)
    AWS Service for managing running Docker jobs on ECS

  - [Airflow](https://github.com/apache/incubator-airflow)
  - Apache incubator project from AirB&B, Expandable DAG based job system 

## Assess

  - Amazon Simple Work Flow

  - Time-triggered AWS Lambda Functions

  - Akka (Cluster)
    Supports cluster singletons without zookeeper, supports cluster sharding.
    Can be a good fit where you already have Akka cluster running for other reasons.

## Hold

  - Job System (Internal System)
    Legacy job system that can run ruby commands/java jars. Handles scheduling, error notification. This system still handles the bulk of Gilt's offline processing for backoffice; however, it is aging and beginning to reveal cracks in terms of out-of-memory errors and jobs not running. We ask engineers to assess other scheduling tools.

  - Curling a service on a schedule from cron to trigger tasks
  - Leader elected scheduled tasks on service nodes
    A few problems with these. For curling, we have the issue of concurrency control, unless you are also handling some global lock amongst your service nodes.
    For both, this means you are also adding load to your service at arbitrary points in time. This can degrade response times for regular traffic unexpectedly.


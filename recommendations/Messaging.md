# Messaging

## Adopt

  - [Amazon SQS](http://aws.amazon.com/sqs/)

    For worker queues, SQS has proven to be an effective technology and is in use in several projects at Gilt.

  - [Amazon Kinesis](http://aws.amazon.com/kinesis/)

    Replacement for Kafka. There are a number of limits currently in Kinesis, but teams have worked successfully with these in numerous use cases.


## Trial

  - [Amazon SNS](http://aws.amazon.com/sns/)

    Potential replacement for rabbit, where messages to SNS can be hooked up to multiple SQS topics for consumption.

## Hold

  - [Kafka](http://kafka.apache.org)
  - [RabbitMQ](https://www.rabbitmq.com)

    We've opted to pause on maintaining our own messaging infrastructure in favor of already managed solutions.

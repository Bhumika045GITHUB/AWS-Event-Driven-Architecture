# AWS-Event-Driven-Architecture
This Architecture uses implementation of dependable AWS Events to decouple an application’s components.

Sample usecase involving components:

~ Event producer: AWS S3 bucket
~ Event ingestion: AWS SNS
~ Event stream: AWS SQS
~ Event consumer: AWS lambda

This repo contains SNS access policy, SQS access policy, SNS subscription filter policy and IAM lambda policies used in this implementation.

# AWS-Event-Driven-Architecture
This Architecture uses implementation of dependable AWS Events to decouple an application’s components.

Sample usecase involving components:

~ Event producer (it causes change in state / update within application  —--> s3): AWS S3 bucket
~ Event ingestion (event router filter / pushes event to next component/ service —---> SNS): AWS SNS
~ Event stream (for huge no of events —---> SQS): AWS SQS
~ Event consumer (take action on event some workflow /  —-> LAMBDA): AWS lambda

This repo contains SNS access policy, SQS access policy, SNS subscription filter policy and IAM lambda policies used in this implementation.
-----------------------------------------------------------------------------------------------------------------------------------------------
Step wise Explanation ~

1. Added created s3 bucket 
2. Created sns - in that - standard / random msg coming not fifo , in advance json (s3 publisher —----> sqs subscriber 2 permisiions) sns-access-policy.json
3. Created 2 sqs  - in that - standard / random msg coming not fifo , multiple ques 2  3 made , ( 2 policies in json  -  1 for lambda func to send , receive msg , 2nd for  sns to send msg  )   sqs-access-policy.json
4. Creating 2 lambda func → craete iam to access, sqs, loudwatch for logs )lambda-policy.json created policy -> which takes role—-------- 4 components / service s raedy not connecting all—---
Connect s3 to sns destination—-----> with s3 event notification , object creation / file comes it triggere –
Connect sns topicss to sqs  queue 1—-----> create / subscribe to sns  -> sqs protocol -> topic -> select 1st queue —-> filter specific event subscription-filter-policy.json —-----> here only put object will come in msg body

5. Repeat - Connect sns topicss to sqs  queue 2—-----> create / subscribe to sns  -> sqs protocol -> topic -> select 2st queue —-> filter specific event subscription-filter-policy.json —-----> here only put object will come

6. Connect sqs queue to lambda —-----> here in sqs queue console we have lambda trigger option go ther —---> queue 1 to lambda1
Repeat - Connect sqs queue to lambda —-----> here in sqs queue console we have lambda trigger option go ther —---> queue 2 to lambda12 

7. Lambda just print event coming 

8. NOW UPLOAD FILE → GO IN LAMbda1, lam2 check cloudwatch logs to print logs.

9. Finish



# serverless-pubsub
Use Localstack to develop a serverless publisher-subscriber service

 *[Installation](#installation)  
 *[Architecture](#architecture)

## Installation

> NOTE: You must have docker running. See [documentation](https://docs.docker.com/).

1. git clone the repository (default `serverless-pubsub`)
2. cd serverless-pubsub
3. run `docker-compose up`

Step #3 will install all dependencies

## Architecture

```shell script
API - http://localhost:8080
 |-- SNS: internal subscriptions
      |-- SQS: internal queue for distribution
           |-- Lambda
                 |-- SNS: public subscriptions to topics
                      |-- SQS
                      |-- HTTP(S)
                      
      |-- SQS: internal queue for backup
           |-- Lambda
                |-- Firehose
                      |-- S3: raw storage
                           |-- Lambda
                                  |-- S3: YYYY/MM/DD/Topic 
```

# Deployment-Of-Serverless-Application

Lambda Function

import json

import boto3

from time import gmtime, strftime

dynamodb = boto3.resource('dynamodb')

table = dynamodb.Table('HelloWorldDatabase')

now = strftime("%a, %d %b %b %y %H:%M:&S +0000", gmtime())

def lambda handler(event, context):
    
    name = event['firstName'] +' '+ event['lastName']
    
    response = table.put item(
        item=(
            'ID' : name
            'LatestGreetingTime' :now
            })
        
    return {
        'statusCode' : 200,
        'body' : jason.dumps('Hello From Lambda,' + name)
    } 



Create Policy Inline

{
"Version": "2012-10-17",
"Statement": [
	{
		"Sid": "VisualEditor0",
		"Effect": "Allow",
		"Action": [
			"dynamodb:PutItem" ,
			"dynamodb:DeleteItem" ,
			"dynamodb:GetItem" ,
			"dynamodb:Scan" ,
			"dynamodb:Query" ,
			"dynamodb:UpdateItem"
		],
		"Resource" : "Your-Table-ARN"
	}
	]
}

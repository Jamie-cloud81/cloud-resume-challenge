# Cloud Resume Challenge – Jamie Jackson

Live site: https://d1q5qpdzxgxe1z.cloudfront.net  
API endpoint: https://hmrm8uhill.execute-api.us-east-2.amazonaws.com/count

## Overview
This project is my implementation of the Cloud Resume Challenge. It hosts my resume as a static website and includes a serverless visitor counter.

The site is deployed to Amazon S3 and delivered globally via Amazon CloudFront. A visitor counter is implemented using API Gateway + AWS Lambda + DynamoDB. A GitHub Actions workflow automatically deploys site changes to S3 and invalidates the CloudFront cache.

## Architecture
### High-level flow
1. User visits the CloudFront URL
2. CloudFront serves `index.html` from a private S3 bucket
3. The page runs JavaScript that calls the API Gateway endpoint (`/count`)
4. API Gateway invokes a Lambda function
5. Lambda updates the visit count in DynamoDB and returns the new count
6. The page displays the updated visitor count

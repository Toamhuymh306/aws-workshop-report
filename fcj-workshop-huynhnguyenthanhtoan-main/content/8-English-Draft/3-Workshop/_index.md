---
title: "Workshop"
date: 2026-07-09
weight: 3
chapter: false
pre: " <b> 8.3. </b> "
---

# Workshop: Serverless AI Inference Platform

## 3.1 Overview

The platform allows users to authenticate, request a secure upload URL, upload leaf images to S3, and trigger an AI inference pipeline through SQS and Lambda.

## 3.2 Prerequisites

- AWS account (Region: `ap-southeast-1`)
- AWS CLI, Docker, and Postman installed
- AI model file (`.pt` or `.onnx`)

## 3.3 Architecture and Service Rationale

- **Amazon Cognito:** secure user authentication with JWT.
- **API Gateway + Presign Lambda:** issue secure pre-signed URL for upload.
- **Amazon S3:** store raw and processed images.
- **Amazon SQS:** queue-based decoupling and burst control.
- **AWS Lambda + ECR:** run AI inference in container-based Lambda.
- **Amazon DynamoDB:** persist diagnosis results with low-latency reads/writes.

## 3.4 Step-by-Step Implementation

### Step 1: Initialize Storage and Database

- Create `s3-raw-images` bucket.
- Configure S3 lifecycle to transition older objects to Glacier Archive after 30 days.
- Create DynamoDB table `AI_Diagnosis_Results` with `ImageID` as partition key.

### Step 2: Package and Deploy AI Model

- Create an ECR repository.
- Build and push Docker image containing model + inference runtime.
- Create `inference-lambda` from container image (5-minute timeout, 3008 MB memory).
- Attach IAM role with SQS read + DynamoDB write permissions.

### Step 3: Secure Upload Flow

- Create `presign-lambda` using Boto3 `generate_presigned_url` (`put_object`).
- Expose endpoint via API Gateway and protect it with Cognito Authorizer.

### Step 4: Event-Driven Integration

- Create standard SQS queue.
- Configure S3 event notification for `s3:ObjectCreated:*` to SQS.
- Set SQS as trigger for `inference-lambda`.

### Step 5: Test and Validation

- Use Postman to get pre-signed URL.
- Upload sample image via HTTP PUT.
- Check CloudWatch logs and validate result records in DynamoDB.

### Step 6: Clean-up

- Empty and delete S3 buckets.
- Delete SQS queue, API Gateway resources, DynamoDB table, ECR images/repos, and Lambda functions.

## 3.5 Personal Reflection

- **Challenge:** HTTP 413 error when uploading large payloads through API Gateway; Lambda timeout during AI model cold start.
- **Solution:** switched to pre-signed URL upload and container-based Lambda via ECR.
- **Future Direction:** add WebSocket push from backend so users receive real-time results without manual refresh.

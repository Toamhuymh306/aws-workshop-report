---
title: "Proposal"
date: 2026-07-09
weight: 2
chapter: false
pre: " <b> 8.2. </b> "
---

# Proposal: Serverless AI Inference Platform

## 1. Project Overview

Build a serverless system that automatically detects and diagnoses plant leaf diseases from images uploaded by end users.

## 2. Problem Statement

In agriculture, disease misclassification is common. For example, red spider mite damage on cacao leaves can be confused with fungal diseases such as VSD or anthracnose. The system needs a stable cloud platform so users can upload images and receive AI-based diagnosis quickly without running servers 24/7.

## 3. Solution Architecture

- Amazon API Gateway
- AWS Lambda (Presign Lambda + Inference Lambda)
- Amazon S3
- Amazon SQS
- Amazon ECR
- Amazon DynamoDB

## 4. Why These Services

- **Cognito + API Gateway:** secure JWT-based API access.
- **Presign Lambda + S3:** direct upload via pre-signed URL, avoiding API Gateway payload limits.
- **SQS:** decouples upload events from AI processing and smooths traffic spikes.
- **Lambda + ECR:** supports large AI models with container images.
- **DynamoDB:** fast NoSQL storage for inference results.

## 5. Key Risk and Mitigation

- **Risk:** AI model size can exceed regular Lambda package limits.
- **Mitigation:** package model and dependencies as a container image and deploy through ECR.

## 6. Expected Outcomes

- Secure and scalable image upload flow.
- Event-driven AI inference pipeline.
- Consistent and queryable diagnosis results in DynamoDB.

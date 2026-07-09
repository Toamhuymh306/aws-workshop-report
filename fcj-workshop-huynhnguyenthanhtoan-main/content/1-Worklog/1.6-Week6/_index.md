---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

- Deploy the containerized AI model to AWS Lambda.
- Configure Lambda resources for heavy compute tasks.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Create new Lambda function using "Container Image" option from ECR | 05/25/2026 | 05/25/2026 | https://000026.awsstudygroup.com/ |
| 3 | - Configure Lambda: increase Timeout (5 mins) and Memory (3008 MB) | 05/26/2026 | 05/26/2026 | https://000027.awsstudygroup.com/ |
| 4 | - Grant IAM permissions for Lambda to read S3 Raw and write S3 Processed | 05/27/2026 | 05/27/2026 | https://000028.awsstudygroup.com/ |
| 5 | - Update Lambda code to download S3 object, run inference, and upload processed result | 05/28/2026 | 05/28/2026 | https://000029.awsstudygroup.com/ |
| 6 | - Perform manual testing of Inference Lambda via AWS Console | 05/29/2026 | 05/29/2026 | https://000030.awsstudygroup.com/ |

### Week 6 Achievements:

- Successfully ran a PyTorch AI model entirely in a serverless environment.
- Overcame Lambda cold start and memory limitation issues.

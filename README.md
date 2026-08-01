# Sales Data Projection

<img width="1092" height="738" alt="image" src="https://github.com/user-attachments/assets/a684c711-3366-4e2f-b919-9c0eb411a6cf" />

<img width="949" height="1177" alt="image" src="https://github.com/user-attachments/assets/2ca1004a-3e73-4882-af92-915d61a72d32" />

---

# 🏗️ AWS CDC Data Pipeline for Sales Analytics

```mermaid
flowchart LR

    A[🐍 Python Mock Data Generator]
    B[(Amazon DynamoDB<br/>Orders Table)]
    C[Amazon DynamoDB Streams<br/>CDC]
    D[Amazon EventBridge Pipes]
    E[Amazon Kinesis Data Streams]
    F[Amazon Kinesis Data Firehose]
    G[AWS Lambda<br/>Transform & Validate]
    H[(Amazon S3 Data Lake)]
    I[AWS Glue Crawler]
    J[AWS Glue Data Catalog]
    K[Amazon Athena]
    L[Amazon QuickSight Dashboard]

    A -->|Insert Orders| B
    B -->|INSERT / UPDATE / DELETE| C
    C -->|CDC Events| D
    D -->|Filtered Events| E
    E -->|Batch Records| F

    F -->|Invoke| G
    G -->|Processed Data| H

    F -->|Backup (Optional)| H

    H --> I
    I --> J
    J --> K
    K --> L

    classDef aws fill:#FF9900,color:#000,stroke:#232F3E,stroke-width:2px;
    classDef storage fill:#3F8624,color:#fff,stroke:#232F3E;
    classDef compute fill:#146EB4,color:#fff,stroke:#232F3E;

    class C,D,E,F,I,J,K,L aws;
    class B,H storage;
    class G compute;
```

---

                  AWS Cloud
┌──────────────────────────────────────────────────────────────────────┐

      Python App
          │
          ▼
 ┌─────────────────┐
 │ Amazon DynamoDB │
 │   Orders Table  │
 └────────┬────────┘
          │
          ▼
 ┌────────────────────────┐
 │ DynamoDB Streams (CDC) │
 └────────┬───────────────┘
          │
          ▼
 ┌────────────────────────┐
 │ EventBridge Pipes      │
 └────────┬───────────────┘
          │
          ▼
 ┌────────────────────────┐
 │ Kinesis Data Streams   │
 └────────┬───────────────┘
          │
          ▼
 ┌────────────────────────┐
 │ Kinesis Firehose       │
 └───────┬────────────────┘
         │
         ▼
 ┌────────────────────────┐
 │ Lambda Transformation  │
 └───────┬────────────────┘
         │
         ▼
 ┌────────────────────────┐
 │ Amazon S3 Data Lake    │
 └───────┬────────────────┘
         │
         ▼
 ┌────────────────────────┐
 │ AWS Glue Crawler       │
 └───────┬────────────────┘
         ▼
 ┌────────────────────────┐
 │ Glue Data Catalog      │
 └───────┬────────────────┘
         ▼
 ┌────────────────────────┐
 │ Amazon Athena          │
 └───────┬────────────────┘
         ▼
 ┌────────────────────────┐
 │ Amazon QuickSight      │
 │ Sales Dashboard        │
 └────────────────────────┘

---


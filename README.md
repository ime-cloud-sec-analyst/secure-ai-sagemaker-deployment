# secure-ai-sagemaker-deployment
Secure deployment of AI model using Amazon SageMaker, S3, IAM roles, and Jupyter notebooks with full code and security best practices.
Project 12: Secure AI Model Deployment on Amazon SageMaker
This project simulates the secure deployment of an AI/ML model using Amazon SageMaker, S3, IAM Roles, and boto3 automation. It demonstrates best practices for cloud-native AI workflows — from model packaging, configuration management, and secure storage, to deployment and execution in SageMaker with least privilege IAM roles and audit logging.
Project Scope

- Simulate a dummy AI model and configuration.
- Package model artifacts using tar.gz.
- Securely upload to Amazon S3 with IAM role.
- Use SageMaker Studio to initialize session and inspect default resources.
- Trigger model deployment using Python & SageMaker SDK.
- Confirm secure interaction (no plaintext credentials).
- Capture infrastructure & flow via screenshots.

Folder Structure

.
├── model/
│   ├── dummy_model.txt
│   └── config.json
├── model.tar.gz
├── Untitled.ipynb
├── screenshots/      <-- Upload your 51 PNG files here
├── README.md

Tools & Services Used
Tool	Purpose
Amazon SageMaker	Managed ML development & model deployment
Amazon S3	Secure artifact storage
IAM Role	Fine-grained permissioning
boto3 & sagemaker SDK	Python-based infrastructure automation
JupyterLab (Studio)	Step-by-step notebook execution
Security Highlights

- Used get_execution_role() — no hardcoded AWS credentials.
- Secure model upload to private S3 bucket using role-based access.
- Model config isolated and inspected before transmission.
- AWS-managed encryption and logging via SageMaker & CloudTrail.

Execution Steps (Notebook Highlights)
1. Load and View Model Artifacts
model/dummy_model.txt
model/config.json
Outputs:
- Model text content (for simulation)
- Pretty-printed JSON configuration
2. Initialize Secure SageMaker Session
from sagemaker import get_execution_role
session = sagemaker.Session()
role = get_execution_role()
3. Package Model Folder
tar -czf model.tar.gz model/
4. Upload to Amazon S3 (boto3)
for root, dirs, files in os.walk("model"):
    s3.upload_file(full_path, bucket, s3_key)
Lessons Learned

- Leveraged IAM role chaining instead of static credentials.
- Applied encryption-by-default via S3 bucket.
- Hands-on with SageMaker Studio interface and CLI packaging.
- Broke model deployment pipeline into secure, auditable steps.

Screenshots & Evidence
Full process documented with 51 step-by-step screenshots
📂 See the screenshots/ folder
References

- SageMaker Documentation: https://docs.aws.amazon.com/sagemaker/
- boto3 S3 Reference: https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html
- AWS Secure Deployment Guide: https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-dg.pdf

Author

Ime Ben
AWS Cloud Security Engineer
GitHub: https://github.com/ime-cloud-sec-analyst


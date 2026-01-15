### What is DevOps?

- **Definition**: DevOps is a set of practices that combines software development (Dev) and IT operations (Ops) to shorten the development lifecycle and deliver high-quality software continuously.
- **Key Principles**:
  - Continuous Integration (CI)
  - Continuous Delivery/Deployment (CD)
  - Infrastructure as Code (IaC)
  - Monitoring and Logging
- **Tools**: Jenkins, Docker, Kubernetes, Ansible, Terraform
- **Business Focus**: Primarily focuses on improving software delivery speed, reliability, and collaboration between development and operations teams.

### What is MLOps?

- **Definition**: MLOps (Machine Learning Operations) is a set of practices that combines machine learning (ML) and IT operations to streamline the deployment, monitoring, and management of machine learning models in production.
- **Purpose**: To ensure that ML models are reliable, scalable, and maintainable throughout their lifecycle.
- **Key Principles**:
  - Model Versioning
  - Data Management
  - Automated Testing for ML Models
  - Continuous Integration and Continuous Deployment for ML (CI/CD for ML)
  - Monitoring Model Performance
- **Tools**: MLflow, TensorFlow Extended (TFX), Kubeflow, Seldon, DataRobot
- **Business Focus**: Aims to bridge the gap between data science and operations teams, ensuring that ML models can be deployed and maintained effectively in production environments.

### Why MLOps Emerged

- **Data Dependency**: ML models rely heavily on data, which can change over time, necessitating continuous monitoring and updating.
- **Experiment Tracking**: Data scientists often run numerous experiments, requiring robust versioning and tracking systems.
- **Model Versions**: Unlike traditional software, ML models need to be versioned not just by code but also by data and hyperparameters.
- **Collaboration**: MLOps fosters collaboration between data scientists, ML engineers, and operations teams to streamline the deployment and maintenance of ML models.

### Key Differences Between DevOps and MLOps

- **Focus Area**:
  - DevOps: Software development and IT operations.
  - MLOps: Machine learning model lifecycle management.
- **Artifacts**:
  - DevOps: Code, binaries, and infrastructure configurations.
  - MLOps: ML models, datasets, and experiment metadata.
- **Testing**:
  - DevOps: Unit tests, integration tests, and system tests.
  - MLOps: Model validation, data validation, and performance testing.
- **Monitoring**:
  - DevOps: Application performance and infrastructure health.
  - MLOps: Model performance, data drift, and prediction accuracy.

### MLOps Maturity Levels

- **Level 0: Manual Processes**
    - Manual data processing, model training, and deployment with no automation or reproducibility.
    - Ad-hoc and manual processes for deploying and managing ML models ("Ad-hoc": done without planning)
- **Level 1: ML Pieline Automation**:
    - Automated training pipeline with continuous training using new data. Versioning of models and datasets.
    - Deployment still manual.
- **Level 2: Continuous Integration and Deployment (CI/CD) for ML**:
    - Fully automated CI/CD pipelines for ML models, including automated testing and validation.
    - Automated deployment to production environments.
- **Level 3: Monitoring and Governance**:
    - Continuous monitoring of model performance and data drift.
    - Governance practices for compliance, auditing, and reproducibility.

### Tools Comparison

- **DevOps Tools**:
    - Version Control: Git, SVN
        - SVN: Apache Subversion, a centralized version control system.
    - CI/CD: Jenkins, GitLab CI, CircleCI
    - Containerization: Docker
    - Orchestration: Kubernetes
    - Infrastructure as Code: Terraform, Ansible, CloudFormation

- **MLOps Tools**:
    - Data Versioning: DVC, Pachyderm
    - Experiment Tracking: MLflow, Weights & Biases
    - Training: GitHub Actions, Jenkins (CI Tools) + DAGs (e.g., Metaflow, Airflow, Kubeflow, Argo Workflows)
    - Model Registry: MLflow Model Registry, Neptune
    - Feature Store: Feast, Tecton
    - Model Serving: Seldon, TensorFlow Serving, TorchServe
    

### MLOps to DevOps Roadmap

1. **Build Foundations on AI/ML**: Understand the basics of machine learning, data science, and AI concepts.
2. **MLOps Foundations**: Learn MLOps principles, practices, and tools.
3. **MLOps with Kubernetes**: Gain expertise in deploying and managing ML models using Kubernetes.
4. **MLOps on Cloud Platforms**: Learn to implement MLOps on cloud platforms like AWS, GCP, or Azure.
5. **LLMops and Generative AI**: Explore MLOps practices specific to large language models (LLMs) and generative AI applications.
6. **Agentic AI Ops**: Delve into advanced MLOps concepts involving autonomous AI systems and their operational challenges.
7. **Data Engineering Foundations**: Build a strong foundation in data engineering to support MLOps workflows.
8. **DevSecOps for MLOps**: Integrate security practices into MLOps workflows to ensure data and model security.


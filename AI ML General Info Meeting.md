# Project Info
## Steps
- Planning: Define Problem, Data
- Execution: Algorithm, Related Work, Execution Plan
- Requirements: Functional and Non-Functional
## Example: Credit Card Fraud Detection
- problem: fraudulent transactions often go unnoticed
- why: traditional systems can't keep up with fraud patterns
- Affected: Banks, merchants, customers
- Impact: Financial loss, reduced trust in digital payments
- Feasability: Anomaly detection with ML models can be implemented as a prototype within one semester
- Data
## Execution: Algorithm, Related work, Execution Plan
- Algorithm/Methodology
- Related Work
- Execution Plan
	- Collect and preprocess data (Week 1-2)
	- Train baseline models (Week 3-4)
	- Implement advanced ML/DL models (Week 5-6)
	- Compare performance (AUC, Precision-Recall) (Week 7)
	- Deploy prototype with API or dashboard (Week 8
## Requirements
- Functional Requirements
	- System must detect fraudulent transactions in real-time
	- Must process incoming transaction streams from a database or API
	- Provide alerts/flags for suspicious transactions
	- Store results in a cloud database (AWS S3/ DynamoDB/ SQL)
	- Dashboard for monitoring model predictions and fraud statistics
- Non-functional requirements
	- Scalability: Should handle millions of transactions daily. (The system should still work if many people use it at once. Solution: Cloud autoscaling (AWS EC2, GCP)
	- Performance: Fraud detection latency < 1 second per transaction. (Detect Fraud quickly so that banks detect on time. Solution: Caching)
	- Reliability: System uptime >= 99% ( Should work most of the time without 
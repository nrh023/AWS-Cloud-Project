# AWS-cloud-project

# Amazon ECS Intrusion Prevention System

## Team Members: Mark Masenda, Lily Williams, Karma McCoy, Erik Garcia, Ned Hammatt 

## Project Overview:
An automated security pipeline deployed on Amazon ECS. It benchmarks AWS GuardDuty against a custom Machine Learning model (SageMaker Random Forest) to detect threats. When an attack is detected, a Lambda function automatically quarantines the compromised container at the network layer, preserving it for forensics without terminating the task.

## Tech Stack
Environment: Amazon ECS
Attack Simulation: Python
Detection: AWS GuardDuty & Scikit-learn Random Forest
Telemetry: CloudTrail, VPC Flow Logs, CloudWatch
Remediation: Amazon EventBridge & Python/Boto3 (isolation Lambda)

## Structure
├── attack-lambda-function/     Python source code for the simulated attacker and json file list for the commands to run
├── isolation-lambda-function/  Python source code for the automated quarantine
├── test-docker/                Docker environment files
├── test-ecr/                   Elastic Container Registry setup
├── Dockerfile                  Vulnerable target application image
├── .gitignore                   Git configuration
└── README.md                   Project documentation

## Quick Start


## Evaluation Metrics
The pipeline's performance is measured using timestamps extracted from CloudWatch:

Time to Detect (TTD): T(detect) −T(attack_start)
​Time to Isolate (TTI): T(quarantine)​ −T(detect)
Total Exposure Time (MTTR): TTD + TTI

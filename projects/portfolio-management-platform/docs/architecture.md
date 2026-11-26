# Portfolio Management Platform

## Business Context

This project simulates an Asset Management Platform similar to what is used in investment banking and portfolio management organizations.

## Components

### Frontend

- Investor Portal
- Reporting Dashboard

### Backend Services

- Trade Service
- Portfolio Service
- Client Service
- Risk Calculation Engine

### Data Sources

- Bloomberg Market Data
- Market Data Provider

### Database

- Oracle RDS

### Infrastructure

- AWS
- Kubernetes
- Terraform
- Jenkins

## High Level Flow

```text
Investor
   ↓
Load Balancer
   ↓
React UI
   ↓
API Gateway
   ↓
Trade Service
Portfolio Service
Client Service
   ↓
Risk Engine
   ↓
Oracle RDS
```

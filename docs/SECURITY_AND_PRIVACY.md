# Security and Privacy — Smart Building Energy

---

## Scope

This document covers the **security and privacy principles** of the Smart Building Energy platform. It applies to:

- The live demo environment
- Any future production deployment
- Data handling and privacy obligations

---

## Demo Environment Security

### Credentials

The demo environment uses fixed demo credentials:

| Field | Value |
|---|---|
| Username | `demo` |
| Password | `A1234` |

These credentials are **intentionally public** and are published in this repository. They provide access only to the demo environment with synthetic data. They do not provide access to any production system, real data, or administrative functions.

**Do not use these credentials on any other system.**

### Demo Data

All operational energy data in the demo environment is **synthetic**. It does not contain:

- Real personal data
- Real meter readings
- Real BMS data
- Real building operations data
- Personal information of any kind

The public building inventory data used (Rostock CC0) contains no personal data.

### Demo Environment Isolation

The demo environment is completely isolated from any production systems. It has:

- No connection to real metering infrastructure
- No connection to real BMS systems
- No write access to real city or building data

---

## Production Deployment Principles

Any production deployment of Smart Building Energy must implement:

### Authentication

- Multi-factor authentication for all users
- Role-based access control (energy manager / reviewer / administrator / read-only)
- Session timeout and re-authentication for sensitive operations
- Audit log of all authentication events

### Data Access Control

- Building data is accessible only to users with explicit authorization for that building
- Cross-building data access requires portfolio-level authorization
- All data access events are logged

### Credentials and Secrets Management

- No credentials, API keys, database connection strings, or tokens are stored in code repositories
- All secrets are managed through environment variables or a secrets management service
- Database credentials are rotated periodically
- API keys are scoped to minimum required permissions

### Network Security

- All API endpoints are served over HTTPS only
- Database connections are encrypted in transit
- BMS/meter integration endpoints require mutual TLS or equivalent

### Audit Logging

- All decisions in the governance chain are recorded in an immutable audit log
- Audit log access is restricted to authorized administrators
- Audit logs are retained for a minimum period consistent with applicable regulations

---

## Data Privacy

### GDPR Applicability

A production deployment handling personal data (including data that can be linked to individuals through building access records or occupancy patterns) is subject to GDPR and applicable national data protection law.

The platform is designed to minimize personal data collection:

- Building energy data is treated at the building level, not the individual level
- Occupancy data is aggregated; individual tracking is not implemented
- No personal performance or behavior data is collected

### Data Minimization

The platform collects only the data necessary for its stated purpose. It does not:

- Track individual occupant behavior
- Collect personal location data
- Store personal communication data

### Data Retention

In a production deployment:

- Energy data is retained for the duration required for M&V and persistence tracking
- Audit records are retained for the period required by applicable regulations
- Personal data, where it arises, is subject to data minimization and retention policies

---

## Responsible Disclosure

If you discover a security vulnerability in the demo environment or in this repository, please report it to:

**ILHAN CEKIC, PhD**  
[LinkedIn](https://www.linkedin.com/in/ilhan-cekic-212b4a4a/)

Please do not publicly disclose security issues before they have been addressed. See [SECURITY.md](../SECURITY.md) for the full responsible disclosure policy.

---

## What This Repository Does NOT Contain

This public showcase repository contains **documentation only**. It does not contain:

- Application source code
- Database schemas or credentials
- API keys or tokens
- Private datasets
- Personal data
- Internal algorithms or IP
- Production configuration files

The demo login credentials (`demo` / `A1234`) are the only credentials in this repository, and they are intentionally public demo credentials with no production access.

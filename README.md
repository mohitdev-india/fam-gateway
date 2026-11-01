<div align="center">
  <h1>FAM Gateway</h1>
  <p><strong>A smarter way to integrate UPI payments.</strong></p>
  <p>An independent payment-integration platform for developers and digital businesses.</p>
  <p>
    <a href="https://fam.hostaura.in"><strong>Live Platform</strong></a>
    &nbsp;·&nbsp;
    <a href="https://fam.hostaura.in/docs.php"><strong>API Documentation</strong></a>
  </p>
  <p>
    <a href="https://fam.hostaura.in"><img src="https://img.shields.io/badge/Platform-Live-16a34a?style=for-the-badge" alt="Platform live"></a>
    <img src="https://img.shields.io/badge/Version-2.4-2563eb?style=for-the-badge" alt="Version 2.4">
    <img src="https://img.shields.io/badge/Project-Proprietary-374151?style=for-the-badge" alt="Proprietary project">
  </p>
</div>

---

## Contents

- [Overview](#overview)
- [Platform Screenshots](#platform-screenshots)
- [Features](#features)
- [Developer API](#developer-api)
- [Webhook Events](#webhook-events)
- [How Payment Verification Works](#how-payment-verification-works)
- [Technology Stack](#technology-stack)
- [Security Notes](#security-notes)
- [Project Information](#project-information)
- [Official Links](#official-links)

## Overview

**FAM Gateway** is an independent payment-integration platform designed to help developers and digital businesses create UPI payment requests, track transactions and automate payment-confirmation workflows.

The platform brings together payment links, a merchant dashboard, API access, transaction records and webhook notifications. Payment confirmation automation can be configured through a connected Gmail account and the merchant's UPI details.

> FAM Gateway is an independent platform. Do not interpret this project as an official bank, payment-network or third-party payment-provider product. Merchants should review the platform's operating model and applicable requirements before using it for real transactions.

## Platform Screenshots

### Landing Page

<p align="center">
  <img src="screenshots/landing-page.jpg" width="100%" alt="FAM Gateway landing page">
</p>

### Merchant Dashboard

<p align="center">
  <img src="screenshots/dashboard.jpg" width="100%" alt="FAM Gateway merchant dashboard">
</p>

### Transactions

<p align="center">
  <img src="screenshots/transactions.jpg" width="100%" alt="FAM Gateway transaction management">
</p>

### API Documentation

<p align="center">
  <img src="screenshots/api-docs.jpg" width="100%" alt="FAM Gateway API documentation">
</p>

### Webhook Configuration

<p align="center">
  <img src="screenshots/webhooks.jpg" width="100%" alt="FAM Gateway webhook settings">
</p>

### Integrations

<p align="center">
  <img src="screenshots/integrations.jpg" width="100%" alt="FAM Gateway integration settings">
</p>

## Features

| Feature | Description |
| --- | --- |
| Payment links | Create payment requests that can be shared with customers. |
| UPI payment workflow | Support the platform's configured UPI payment collection workflow. |
| Automated verification | Check payment confirmations using the connected Gmail integration. |
| REST API | Integrate payment creation and status checks into external applications. |
| Webhooks | Send payment event notifications to configured endpoints. |
| Transaction history | Review payment records and their current statuses. |
| Merchant dashboard | View payment activity and available account analytics. |
| API key management | Manage the API credential used by developer integrations. |

## Developer API

FAM Gateway exposes API endpoints for creating payment requests and checking their status.

| Action | Method | Endpoint |
| --- | --- | --- |
| Create a payment | `POST` | `/api/create.php` |
| Check payment status | `GET` | `/api/status.php` |

### Authentication

Requests are authenticated using an API key. The documentation describes the supported authentication format, including the `X-API-KEY` header.

Example request structure (replace the placeholder with your own key and use the current parameter names from the live documentation):

```bash
curl -X POST "https://fam.hostaura.in/api/create.php" \
  -H "Content-Type: application/json" \
  -H "X-API-KEY: YOUR_API_KEY" \
  -d '{
    "amount": 100,
    "order_id": "ORDER-1001",
    "remark": "Test payment"
  }'
```

For exact request fields, response formats, status values and integration guidance, refer to the [official API documentation](https://fam.hostaura.in/docs.php).

## Webhook Events

FAM Gateway supports configurable webhook URLs for payment event notifications. The platform documentation describes HMAC-SHA256 signature verification and webhook delivery history.

When implementing a webhook receiver:

- Verify the signature on your server before trusting the payload.
- Handle duplicate deliveries safely; webhook consumers should be idempotent.
- Return an appropriate HTTP response promptly.
- Do not expose signing secrets in browser-side code or public repositories.

See the [API documentation](https://fam.hostaura.in/docs.php) for the current payload and signature format.

## How Payment Verification Works

The merchant configures the supported Gmail connection and UPI details in the platform. FAM Gateway uses the configured integration to check payment-confirmation messages and update transaction records. Configured webhook endpoints can then receive relevant payment notifications.

The reliability of this workflow depends on correct account configuration, message availability and the connected email provider. Merchants should reconcile important transactions against their own payment records.

## Technology Stack

The project is described as using:

- PHP
- MySQL
- JavaScript
- HTML5 and CSS3
- REST API
- HMAC-SHA256 for webhook signatures

## Security Notes

- Never commit a real API key, Gmail app password, webhook signing secret or customer data to GitHub.
- Use placeholders such as `YOUR_API_KEY` in examples and screenshots.
- If a credential is exposed, revoke or regenerate it immediately and update every integration that uses it.
- Keep private credentials on the server; do not embed them in public frontend JavaScript.
- Review webhook signatures and validate payment status on the server before fulfilling an order.
- Redact personal information and live transaction details from screenshots and issue reports.

## Project Information

| Detail | Information |
| --- | --- |
| Project | FAM Gateway |
| Developer | Mohit Kumar |
| Platform | Web application |
| Current documented release | 2.4 |
| Project status | Live platform |
| Ownership | Proprietary |

## Official Links

- **Website:** https://fam.hostaura.in
- **API Documentation:** https://fam.hostaura.in/docs.php
- **GitHub Repository:** https://github.com/mohitdev-india/fam-gateway

---

<div align="center">
  <strong>Built with purpose. Designed for simplicity.</strong>
  <br>
  © Mohit Kumar · FAM Gateway
  <br>
  <sub>All rights reserved. This repository does not grant permission to use, modify, redistribute or commercially exploit the platform without the owner's authorization.</sub>
</div>

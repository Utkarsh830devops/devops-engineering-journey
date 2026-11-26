# Trade Service

## Overview

Trade Service manages investor buy and sell transactions.

## Responsibilities

- Buy Asset
- Sell Asset
- Trade Validation
- Trade Settlement

## API Endpoints

### Buy Asset

```http
POST /api/v1/trades/buy
```

### Sell Asset

```http
POST /api/v1/trades/sell
```

### Get Trade History

```http
GET /api/v1/trades/{clientId}
```

## Dependencies

- Portfolio Service
- Client Service
- Market Data Provider

## Database

- Oracle RDS

## Status

Development

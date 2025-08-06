# BaseApp-Fees

A high-performance subgraph for tracking ERC-4337 Account Abstraction ecosystem data on Base chain.

## Overview

This subgraph monitors the complete BaseApp ecosystem including user operations, paymaster fees, account creation, and bundler activity.

## Features

- **User Operations**: Track all account abstraction transactions
- **Paymaster Analytics**: Monitor gas and token-based fee flows  
- **Account Management**: Smart contract account creation and usage
- **Bundler Performance**: Transaction bundling metrics
- **Real-time Data**: Live ecosystem monitoring

## Performance Optimizations

- **Timeseries entities** for efficient data storage
- **Automatic aggregations** for hourly/daily statistics
- **Immutable entities** for faster indexing
- **Pruning enabled** for optimal query performance
- **@derivedFrom relationships** for efficient data structures

## Contracts Tracked

- **EntryPoint**: `0x5ff137d4b0fdcd49dca30c7cf57e578a026d2789`
- **VerifyingSingletonPaymaster**: `0x00000f79b7faf42eebadba19acc07cd08af44789`
- **BiconomyTokenPaymaster**: `0x00000f7365ca6c59a2c93719ad53d567ed49c14c`
- **VerifyingSingletonPaymaster2**: `0x000000f6faeda8f7bfa1a8589b4b6e2d71c37592`
- **AccountFactory**: `0x0000000000a84d1a9b0063a910315c7ffa9cd248`

## Quick Start

```bash
# Install dependencies
npm install

# Generate types and build
graph codegen && graph build

# Deploy to Graph Studio
graph deploy base-app-fees
```

## Query Endpoint

```
https://api.studio.thegraph.com/query/111767/base-app-fees/0.0.8
```

## Example Queries

### Daily User Operations
```graphql
{
  userOperationStats(interval: "day", first: 7) {
    timestamp
    totalOperations
    totalGasUsed
    totalGasCost
  }
}
```

### Top Paymasters
```graphql
{
  paymasters(orderBy: totalOperations, orderDirection: desc, first: 10) {
    address
    totalOperations
    totalGasCost
    successRate
  }
}
```

## License

MIT 
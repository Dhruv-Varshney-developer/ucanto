# @ucanto/interface

`@ucanto/interface` provides shared TypeScript type definitions and contracts used across the `ucanto` ecosystem. It ensures type-safe and consistent interactions between all ucanto modules without containing any runtime code.

## What It Provides
- **Core UCAN Types**: Definitions for capabilities, invocations, delegations, and receipts
- **Transport Interfaces**: Types for encoding, decoding, and HTTP communication  
- **Service Contracts**: Types for client-server interaction and service method definitions
- **Validation Types**: Interfaces for capability parsing, matching, and authorization

## How It Fits with Other Modules
- `@ucanto/client`: Uses connection and invocation types for service communication
- `@ucanto/server`: Uses service method and validation types for request handling
- `@ucanto/transport`: Uses encoder/decoder interfaces for message serialization
- `@ucanto/core`: Uses core UCAN types for capability and delegation logic
- `@ucanto/principal`: Uses identity and signature types for cryptographic operations

## Installation
```sh
npm install @ucanto/interface
```

## TypeScript Integration
This package ensures type safety across ucanto packages. When you use other ucanto packages with TypeScript, you automatically get these type definitions:

```ts
// When using @ucanto/client, you automatically get these types:
import * as Client from '@ucanto/client'

// The connection, invocation, and receipt objects all use types from @ucanto/interface
const connection = Client.connect(/* ... */) // ConnectionView<T> type
const invocation = Client.invoke(/* ... */)  // IssuedInvocation<C> type  
const receipt = await connection.execute(invocation) // Receipt<T> type
```

**Note**: You typically don't import from @ucanto/interface directly. These types are used internally by other ucanto packages to ensure everything works together correctly.
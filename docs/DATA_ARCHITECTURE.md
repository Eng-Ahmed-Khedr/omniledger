# OmniLedger: Data Architecture & State Design

## Overview
OmniLedger simulates a high-velocity financial data stream. The core architecture relies on a strictly typed data pipeline that pushes new state snapshots at defined intervals without causing UI blocking or infinite rendering loops.

## The Data Interface Map
The global state relies on a single snapshot object representing the business at a specific second in time. 

### 1. Timestamp (String/Date)
- **Behavior:** Chronological anchor.
- **Purpose:** Maps the X-axis for all time-series visualizations.

### 2. Transaction Volume (Integer)
- **Behavior:** Highly volatile (e.g., 0, 4, 1, 0, 5).
- **Purpose:** Represents unpredictable, spontaneous server events or checkout completions during the current tick.

### 3. Active Checkout Sessions (Integer)
- **Behavior:** Organic fluctuation (e.g., 120 -> 123 -> 121).
- **Purpose:** Represents active, persistent WebSocket connections or users currently sitting in the purchasing funnel. 

### 4. Real-Time Revenue (Float/Integer)
- **Behavior:** Strictly cumulative and compounding.
- **Purpose:** An aggregated total calculated by multiplying the transaction volume by an assumed average order value. This metric only scales upward.

## State Management Rules
- The mock data engine generates these snapshots completely independent of the UI layer.
- The global state manager (Redux Toolkit) maintains an array buffer of these snapshots.
- To prevent memory leaks, the state buffer strictly enforces a maximum array length (e.g., 30 ticks), automatically shifting out the oldest data point when a new one is pushed.
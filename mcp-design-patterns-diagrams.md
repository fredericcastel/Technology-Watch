# MCP Design Patterns - Visual Diagrams

## 1. Direct API Wrapper Pattern

```mermaid
graph LR
    A[AI Agent] -->|Tool Call| B[MCP Server]
    B -->|Direct Mapping| C[API Endpoint]
    C -->|Response| B
    B -->|Tool Result| A
    
    style A fill:#e1f5ff
    style B fill:#fff3e0
    style C fill:#f3e5f5
```

**Description:** Simple 1:1 mapping between MCP tools and existing APIs.

---

## 2. Composite Service Pattern

```mermaid
graph TD
    A[AI Agent] -->|Request| B[MCP Composite Service]
    B -->|Call API 1| C1[Backend API 1]
    B -->|Call API 2| C2[Backend API 2]
    B -->|Call API 3| C3[Backend API 3]
    C1 -->|Response| B
    C2 -->|Response| B
    C3 -->|Response| B
    B -->|Aggregated Result| A
    
    style A fill:#e1f5ff
    style B fill:#fff3e0
    style C1 fill:#f3e5f5
    style C2 fill:#f3e5f5
    style C3 fill:#f3e5f5
```

**Description:** Combines and orchestrates multiple APIs into a single, higher-level service.

---

## 3. MCP-to-Agent Pattern

```mermaid
graph TD
    A[AI Agent - Main] -->|Delegate Task| B[MCP Server]
    B -->|Call Sub-Agent| C[Specialized AI Agent 1]
    B -->|Call Sub-Agent| D[Specialized AI Agent 2]
    B -->|Call Sub-Agent| E[Specialized AI Agent 3]
    C -->|Result| B
    D -->|Result| B
    E -->|Result| B
    B -->|Aggregated Result| A
    
    style A fill:#e1f5ff
    style B fill:#fff3e0
    style C fill:#c8e6c9
    style D fill:#c8e6c9
    style E fill:#c8e6c9
```

**Description:** MCP tools call other AI agents for specialized reasoning or domain expertise.

---

## 4. Event-Driven Integration Pattern

```mermaid
graph TB
    A[AI Agent] -->|Triggers Event| B[Event Emitter]
    B -->|Publishes| C[Event Queue/Broker]
    C -->|Event| D[Service 1]
    C -->|Event| E[Service 2]
    C -->|Event| F[Service 3]
    D -->|Process| G[Background Job 1]
    E -->|Process| H[Background Job 2]
    F -->|Process| I[Background Job 3]
    
    style A fill:#e1f5ff
    style B fill:#fff3e0
    style C fill:#ffe0b2
    style D fill:#f3e5f5
    style E fill:#f3e5f5
    style F fill:#f3e5f5
    style G fill:#dcedc8
    style H fill:#dcedc8
    style I fill:#dcedc8
```

**Description:** MCP tools emit events to trigger asynchronous or background processing.

---

## 5. Hierarchical MCP Pattern

```mermaid
graph TD
    A[AI Agent] -->|Request| B[Top-Level Router MCP]
    B -->|Route to Domain A| C[Domain A MCP]
    B -->|Route to Domain B| D[Domain B MCP]
    B -->|Route to Domain C| E[Domain C MCP]
    
    C -->|Calls| F[Service A1]
    C -->|Calls| G[Service A2]
    
    D -->|Calls| H[Service B1]
    D -->|Calls| I[Service B2]
    
    E -->|Calls| J[Service C1]
    E -->|Calls| K[Service C2]
    
    F -->|Returns| C
    G -->|Returns| C
    H -->|Returns| D
    I -->|Returns| D
    J -->|Returns| E
    K -->|Returns| E
    
    C -->|Result| B
    D -->|Result| B
    E -->|Result| B
    B -->|Unified Response| A
    
    style A fill:#e1f5ff
    style B fill:#fff3e0
    style C fill:#ffccbc
    style D fill:#ffccbc
    style E fill:#ffccbc
```

**Description:** Organizes MCP servers in layered domains with top-level routers handling coordination.

---

## 6. Local Resource Access Pattern

```mermaid
graph LR
    A[AI Agent] -->|File Request| B[MCP Local Access Server]
    B -->|Validate| C{Permission Check}
    C -->|Allowed| D[Local File System]
    C -->|Denied| E[Access Denied]
    D -->|File Data| B
    B -->|Processed Data| A
    
    style A fill:#e1f5ff
    style B fill:#fff3e0
    style C fill:#f3e5f5
    style D fill:#e8f5e9
    style E fill:#ffcdd2
```

**Description:** Gives secure access to local file systems for fast document or data processing.

---

## Pattern Comparison Matrix

| Pattern | Complexity | Scalability | Best For | Key Advantage |
|---------|-----------|-------------|----------|---------------|
| Direct API Wrapper | Low | Medium | Simple APIs | Speed & simplicity |
| Composite Service | Medium | Medium | Multi-API workflows | Orchestration |
| MCP-to-Agent | High | High | Complex reasoning | Modularity & expertise |
| Event-Driven | High | Very High | Real-time systems | Scalability & decoupling |
| Hierarchical | Very High | Very High | Enterprise systems | Manageability at scale |
| Local Resource | Low | Medium | High-performance tasks | Performance & security |

---

## When to Use Each Pattern

### Direct API Wrapper
- ✅ Third-party APIs are stable and well-documented
- ✅ Minimal engineering overhead needed
- ❌ Not suitable for complex multi-step workflows

### Composite Service
- ✅ Need to orchestrate multiple services
- ✅ Want to abstract complexity from the agent
- ❌ Avoid if APIs are frequently changing

### MCP-to-Agent
- ✅ Multiple AI agents with specialized roles
- ✅ Complex reasoning requiring domain expertise
- ❌ Can increase latency with too many hops

### Event-Driven
- ✅ Real-time, high-throughput systems
- ✅ Asynchronous processing required
- ❌ Needs careful event schema management

### Hierarchical
- ✅ Large enterprise deployments
- ✅ Multiple business domains
- ❌ More complex to maintain and monitor

### Local Resource Access
- ✅ High-performance file processing needed
- ✅ Offline or secure environments
- ❌ Limited to local resources only
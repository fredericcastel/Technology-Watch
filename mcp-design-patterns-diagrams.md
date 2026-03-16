# MCP Design Patterns Diagrams

## 1. Model-View-Presenter (MVP)
```mermaid
graph LR
A[User] -->|Interacts| B[View]
B -->|Notifies| C[Presenter]
C -->|Updates| B
C -->|Fetches| D[Model]
D -->|Returns Data| C
```

## 2. Model-View-Controller (MVC)
```mermaid
graph TD
A[User] -->|Input| B[Controller]
B -->|Fetches Model| C[Model]
C -->|Updates| B
B -->|Updates View| D[View]
D -->|Displays| A
```

## 3. Model-View-ViewModel (MVVM)
```mermaid
graph TD
A[User] -->|Interacts| B[View]
B -->|Binds| C[ViewModel]
C -->|Updates| B
C -->|Fetches| D[Model]
D -->|Returns Data| C
```

## 4. Flux
```mermaid
graph TD
A[View] -->|Dispatch| B[Action]
B -->|Notifies| C[Store]
C -->|Updates| A
C -->|Emits| D[View]
```

## 5. Command Pattern
```mermaid
graph TD
A[Client] -->|Sends Command| B[Invoker]
B -->|Calls| C[Command]
C -->|Executes| D[Receiver]
```

## 6. Observer Pattern
```mermaid
graph TD
A[Subject] -->|Notifies| B[Observer]
B -->|Updates| C[ConcreteObserver]
```

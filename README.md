# Top 60 Microservices Interview Questions

<div>
<p align="center">
<a href="https://devinterview.io/questions/software-architecture-and-system-design/">
<img src="https://firebasestorage.googleapis.com/v0/b/dev-stack-app.appspot.com/o/github-blog-img%2Fsoftware-architecture-and-system-design-github-img.jpg?alt=media&token=521fd2a9-0d56-49c0-a723-9bd6ca081893" alt="software-architecture-and-system-design" width="100%">
</a>
</p>

#### You can also find all 60 answers here 👉 [Devinterview.io - Microservices](https://devinterview.io/questions/software-architecture-and-system-design/microservices-interview-questions)

<br>

## 1. What is a _microservice_ and how does it differ from a _monolithic architecture_?

**Microservices** and **monolithic architecture** are two distinct software design paradigms, each with its unique traits.

A monolithic architecture consolidates all software components into a single program, whereas a microservices architecture divides the application into **separate, self-contained services**.

Microservices offer several advantages but also have their own challenges, requiring careful consideration in the software design process.

### Key Differences

- **Decomposition**: Monolithic applications are not easily separable, housing all functionality in a single codebase. Microservices are **modular**, each responsible for a specific set of tasks.

- **Deployment Unit**: The entire monolithic application is **packaged and deployed** as a single unit. In contrast, microservices are deployed **individually**.

- **Communication**: In a monolith, modules communicate through **in-process calls**. Microservices use standard communication protocols like **HTTP/REST** or message brokers.

- **Data Management**: A monolith typically has a **single database**, whereas microservices may use **multiple databases**.

- **Scaling**: Monoliths scale by replicating the entire application. Microservices enable **fine-grained scaling**, allowing specific parts to scale independently.

- **Technology Stack**: While a monolithic app often uses a single technology stack, microservices can employ a **diverse set of technologies**.

- **Development Team**: Monoliths can be developed by a **single team**, whereas microservices are often the domain of **distributed teams**.

### When to Use Microservices

Microservices are advantageous for certain types of projects:

- **Complex Systems**: They are beneficial when developing complex, business-critical applications where modularity is crucial.

- **Scalability**: If you anticipate varying scaling needs across different functions or services, microservices might be the best pick.

- **Technology Diversification**: When specific functions are better suited to certain technologies or when you want to use the best tools for unique tasks.

- **Autonomous Teams**: For bigger organizations with multiple teams that need to work independently.
<br>

## 2. Can you describe the principles behind the _microservices architecture_?

**Microservices** is an architectural style that structures an application as a collection of small, loosely coupled services. Each service is self-contained, focused on a specific business goal, and can be developed, deployed, and maintained independently.

### Core Principles of Microservices

#### Codebase & Infrastructure as a Service

Each microservice manages its own codebase and data storage. It uses its own independent infrastructure, ranging from the number of virtual machines to persistence layers, messaging systems, or even data models.

#### Antifragility

**Microservices**, instead of resisting failure, respond to it favorably. They self-adapt and become more resilient in the face of breakdowns.

#### Ownership

Development teams are responsible for the entire lifecycle of their respective microservices - from development and testing to deployment, updates, and scaling.

#### Design for Failure

Microservices are built to anticipate and handle failures at various levels, ensuring the graceful degradation of the system.

#### Decentralization

Services are autonomous, making their own decisions without requiring overarching governance. This agility permits independent deployments and ensures that changes in one service do not disrupt others.

#### Built Around Business Capability

Each service is crafted to provide specific and well-defined business capabilities. This focus increases development speed and makes it easier to comprehend and maintain the system.

#### Service Coupling

Services are related through well-defined contracts, mainly acting as providers of specific functionalities. This reduces dependencies and integration challenges.

#### Directed Transparency

Each service exposes a well-defined API, sharing only the necessary information. Teams can independently choose the best technology stack, avoiding the need for a one-size-fits-all solution.

#### Infrastructure Automation

Deployments, scaling, and configuration undergo automation, preserving development velocity and freeing teams from manual, error-prone tasks.

#### Organizational Alignment

Teams are structured around services, aligning with Conway's Law to support the **Microservices** architecture and promote efficiency.

#### Continuous Small Revisions

Services are frequently and iteratively improved, aiming for continual enhancement over major, infrequent overhauls.

#### Discoverability

Services make their features, capabilities, and interfaces discoverable via well-documented APIs, fostering an environment of interoperability.

### The "DevOps" Connection

The **DevOps** method for software development merges software development (Dev) with software operation (Ops). It focuses on shortening the system's software development life cycle and providing consistent delivery. The "you build it, you run it" approach, where developers are also responsible for operating their software in production, is often associated with both **Microservices** and **DevOps**.

### Code Example: Loan Approval Microservice

Here is the sample Java code:

```java
@RestController
@RequestMapping("/loan")
public class LoanService {
    @Autowired
    private CreditCheckService creditCheckService;

    @PostMapping("/apply")
    public ResponseEntity<String> applyForLoan(@RequestBody Customer customer) {
        if(creditCheckService.isEligible(customer))
            return ResponseEntity.ok("Congratulations! Your loan is approved.");
        else
            return ResponseEntity.status(HttpStatus.FORBIDDEN).body("We regret to inform you that your credit rating did not meet our criteria.");
    }
}
```
<br>

## 3. What are the main benefits of using _microservices_?

Let's look at the main advantages of using microservices:

### Key Benefits

#### 1. Scalability

Each microservice can be **scaled independently**, which is particularly valuable in dynamic, going-viral, or resource-intensive scenarios.

#### 2. Flexibility

**Decoupling** services means one service's issues or updates generally won't affect others, promoting agility.

#### 3. Technology Diversity

Different services can be built using varied languages or frameworks. While this adds some complexity, it allows for **best-tool-for-the-job** selection.

#### 4. Improved Fault Tolerance

If a microservice fails, it ideally doesn't bring down the entire system, making the system more **resilient**.

#### 5. Agile Development

Microservices mesh well with Agile, enabling teams to **iterate independently**, ship updates faster, and adapt to changing requirements more swiftly.

#### 6. Easier Maintenance

No more unwieldy, monolithic codebases to navigate. With microservices, teams can focus on smaller, specific codebases, thereby enabling more targeted maintenance.

#### 7. Tailored Security Measures

Security policies and mechanisms can be tailored to individual services, potentially reducing the overall attack surface.

#### 8. Improved Team Dynamics

Thanks to reduced **codebase ownership** and the interoperability of services, smaller, focused teams can thrive and communicate more efficiently.
<br>

## 4. What are some of the challenges you might face when designing a _microservices architecture_?

When **designing a microservices architecture**, you are likely to encounter the following challenges:

### Data Management

- **Database Per Microservice**: Ensuring that each microservice has its own database can be logistically complex. Data relationships and consistency might be hard to maintain.
  
- **Eventual Consistency**: Different microservices could be using data that might not be instantly synchronized. Dealing with eventual consistency can raise complications in some scenarios.

### Service Communication

- **Service Synchronization**: Maintaining a synchronous communication between numerous services can result in a more tightly coupled and less scalable architecture.
  
- **Service Discovery**: As the number of services grows, discovering and properly routing requests to the appropriate service becomes more challenging.

### Security and Access Control

- **Decentralized Security**: Implementing consistent security measures, such as access control and authentication, across all microservices can be intricate.
  
- **Externalized Authorization**: When security-related decisions are taken outside the service, coherent and efficient integration is crucial.

### Infrastructure Management

- **Server Deployment**: Managing numerous server deployments entails additional overhead and might increase the risk of discrepancies among them.

- **Monitoring Complexity**: With each microservice operating independently, gauging the collective functionality of the system necessitates more extensive monitoring capabilities.

### Business Logic Distribution

- **Domain and Data Coupling**: Microservices, especially those representing different business domains, may find it challenging to process complex business transactions that require data and logic from several services.

- **Cross-Cutting Concerns Duplication**: Ensuring a uniform application of cross-cutting concerns like logging or caching across microservices is non-trivial.

### Scalability

- **Fine-Grained Scalability**: While microservices allow selective scale-up, guaranteeing uniform performance across varying scales might be troublesome.

- **Service Bottlenecks**: Certain services might be hit more frequently, potentially becoming bottlenecks.

### Development and Testing

- **Integration Testing**: Interactions between numerous microservices in real-world scenarios might be challenging to replicate in testing environments.

### Consistency and Atomicity 

- **System-Wide Transactions**: Ensuring atomic operations across multiple microservices is complex and might conflict with certain microservice principles. 

- **Data Integrity**: Without a centralized database, governing data integrity could be more intricate, especially for related sets of data that multiple microservices handle.

### Challenges in Updating and Versioning

- **Deployment Orchestration**: Coordinated updates or rollbacks, particularly in hybrid environments, can present difficulties.

- **Version Compatibility**: Assuring that multiple, potentially differently-versioned microservices can still work together smoothly.

### Team Structure and Organizational Alignment

- **Siloed Teams**: Without a unified architectural vision or seamless communication, different teams developing diverse microservices might make decisions that are not entirely compatible with the overall system.

- **Documentation and Onboarding**: With an extensive number of microservices, their functionalities, interfaces, and usage need to be well-documented for efficient onboarding and upkeep.
<br>

## 5. How do _microservices communicate_ with each other?

**Microservices** often work together, and they need efficient **communication mechanisms**...

### Communication Patterns

- **Synchronous**: Web services and RESTful APIs synchronize requests and responses. They are simpler to implement but can lead to **tighter coupling** between services. For dynamic traffic or workflow-specific requests, this is a suitable choice.

- **Asynchronous**: Even with service unavailability or high loads, queues lead to the delivery of messages. The services do not communicate or interact beyond their immediate responsibilities and workloads. For unpredictable or lengthy processes, use asynchronous communication.

- **Data Streaming**: For continuous data needs or applications that work with **high-frequency data**, such as stock prices or real-time analytics, this method is highly effective. Kafka or AWS Kinesis are examples of this pattern.

### Inter-Service Communication Methods

1. **RESTful APIs**: Simple and clean, they utilize HTTP's request-response mechanism. Ideal for stateless, cacheable, and stateless resource interactions.

2. **Messaging**: Deploys a message broker whereby services use HTTP or a messaging protocol (like AMQP or MQTT). This approach offers decoupling, and the broker ensures message delivery. Common tools include RabbitMQ, Apache Kafka, or AWS SQS.

3. **Service Mesh and Sidecars**: A sidecar proxy, typically running in a container, works alongside each service. They assist in monitoring, load balancing, and authorization.

4. **Remote Procedure Call (RPC)**: It involves a client and server where the client sends requests to the server with a defined set of parameters. They're efficient but not perfectly decoupled.

5. **Event-Based Communication**: Here, services interact by producing and consuming events. A service can publish events into a shared event bus, and other services can subscribe to these events and act accordingly. This pattern supports decoupling and scalability. Common tools include Apache Kafka, AWS SNS, and GCP Pub/Sub.

6. **Database per Service**: It involves each microservice owning and managing its database. If a service A needs data from service B, it uses B's API to retrieve or manipulate data.

7. **API Gateway**: Acts as a single entry point for services and consumers. Netscaler, HAProxy, and Kong are popular API Gateway tools.

### Code Example: REST API

Here is the Python code:

```python
import requests

# Make a GET request to receive a list of users.
response = requests.get('https://my-api/users')
users = response.json()
```

### Code Example: gRPC

Here is the Python code:

```python
# Import the generated server and client classes.
import users_pb2
import users_pb2_grpc

# Create a gRPC channel and a stub.
channel = grpc.insecure_channel('localhost:50051')
stub = users_pb2_grpc.UserStub(channel)

# Call the remote procedure.
response = stub.GetUsers(users_pb2.UserRequest())
```

### What is the best way to Implement Microservices?

- **Ease of Development**: If you need to onboard a large number of developers or have strict timelines, RESTful APIs are often easier to work with.

- **Performance**: gRPC and other RPC approaches are superior to RESTful APIs in terms of speed, making them ideal when performance is paramount.

- **Type Safety**: gRPC, due to its use of Protocol Buffers, ensures better type safety at the cost of being slightly less human-readable when compared to RESTful JSON payloads.

- **Portability**: RESTful APIs, being HTTP-based, are more portable across platforms and languages. On the other hand, gRPC is tailored more towards microservices built with Protobufs.
<br>

## 6. What is _Domain-Driven Design (DDD)_ and how is it related to _microservices_?

**Domain-Driven Design** (DDD) provides a model for designing and structuring microservices around specific business domains. It helps teams reduce complexity and align better with domain experts.

### Context Boundaries

In DDD, a **Bounded Context** establishes clear boundaries for a domain model, focusing on a specific domain of knowledge. These boundaries help microservice teams to operate autonomously, evolving their services within a set context.

### Ubiquitous Language

**Ubiquitous Language** is a shared vocabulary that unites developers and domain experts. Microservices within a Bounded Context are built around this common language, facilitating clear communication and a deeper domain understanding.

### Strong Consistency and Relational Databases

Within a Bounded Context, microservices share a consistent data model, often dealing with strong consistency and using relational databases. This cohesion simplifies integrity checks and data relationships.

### Code Example

1. `PaymentService` Microservice:

    ```java
    @Entity
    public class Payment {
        @Id
        private String paymentId;
        private String orderId;
        // ... other fields and methods
    }
    ```

2. `OrderService` Microservice:

    ```java
    @Entity
    public class Order {
        @Id
        private String orderId;
        // ... other fields and methods
    }

    public void updateOrderWithPayment(String orderId, String paymentId) {
        // Update the order
    }
    ```

3. `OrderDetailsService` Microservice:

    ```java
    @Entity
    public class OrderDetail {
        @EmbeddedId
        private OrderDetailId orderDetailId;
        private String orderId;
        private String itemId;
        private int quantity;
        // ... other fields and methods
    }
    ```
<br>

## 7. How would you decompose a _monolithic application_ into _microservices_?

**Decomposing** a **monolithic application** into **microservices** involves breaking down a larger piece of software into smaller, interconnected services. This process allows for greater development agility, flexibility, and often better scalability.

### Key Considerations

1. **Domain-Driven Design (DDD)**: Microservices should be independently deployable and manageable pieces of the application, typically built around distinct business areas or domains.
  
2. **Database Strategy**: Each microservice should have its own data storage, but for ease of data access and management, it's beneficial for microservices to share a database when practical.

3. **Communication**: The microservices should interact with each other in a well-coordinated manner. Two common models are Direct communication via HTTP APIs or using events for asynchronous communication.

### Steps to Decompose

1. **Identify Domains**: Break down the application into major business areas or domains.
2. **Data Segregation**: Determine the entities and relationships within each microservice. Use techniques like **database-per-service** or **shared-database**.
3. **Service Boundary**: Define the boundaries of each microservice - what data and functionality does it control?
4. **Define Contracts**: Intelligently design the APIs or events used for communication between microservices.
5. **Decouple Services**: The services should be loosely coupled, to the maximum extent possible. This is especially important in scenarios where you have independent development teams working on the various microservices.

### Code Example: Decomposition with DDD

Here is the Java code:

```java
@Entity
@Table(name = "product")
public class Product {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private double price;
    //...
}

@Entity
@Table(name = "order_item")
public class OrderItem {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private Long productId;
    private Integer quantity;
    private double price;
    //...
}

public interface OrderService {
    Order createOrder(String customerId, List<OrderItem> items);
    List<Order> getOrdersForCustomer(String customerId);
    //...
}

@RestController
@RequestMapping("/orders")
public class OrderController {
    //...
    @PostMapping("/")
    public ResponseEntity<?> createOrder(@RequestBody Map<String, Object> order) {
        //...
    }
    //...
}
```

In this example, a `Product` microservice could manage products and expose its services through RESTful endpoints, and an `Order` microservice could manage orders. The two microservices would communicate indirectly through APIs, following DDD principles. Each would have its own database schema and set of tables.
<br>

## 8. What strategies can be employed to manage transactions across multiple _microservices_?

Managing transactions across multiple **microservices** presents certain challenges, primarily due to the principles of independence and isolation that microservices are designed around. However, there are both traditional and modern strategies to handle multi-service transactions, each with its own benefits and trade-offs.

### Traditional Approaches

#### Two-Phase Commit (2PC)

Two-Phase Commit is a transaction management protocol in which a global coordinator communicates with all participating services to ensure that the transaction can either be committed globally or rolled back across all involved services.

While it offers **transactional integrity**, 2PC has seen reduced popularity due to its potential for **blocking scenarios**, performance overhead, and the difficulties associated with its management in distributed ecosystems.

#### Three-Phase Commit (3PC)

A direct evolution of the 2PC model, 3PC provides a more **robust** alternative. By incorporating an extra phase, it tries to overcome some of the drawbacks of 2PC, such as the potential for indefinite blocking.

While 3PC is an improvement over 2PC in this regard, it's not without its complexities and can still introduce **performance penalties** and **maintenance overhead**.

#### Transactional Outbox

The Transactional Outbox pattern involves using **messaging systems** as a mechanism to coordinate transactions across multiple microservices. In this approach:
1. The primary DB records changes in the outbox.
2. An event message is added to a message broker.
3. Subscribers read the message and execute the corresponding local transaction.

**Transactional outbox offers high decoupling** but does not provide the same level of **strong consistency** as the previous pattern.

#### SAGA Pattern

Derived from the Greek word for a "long, epic poem," a saga is a sequence of **local transactions**, each initiated within a microservice. In a distributed setting, a saga is a **coordination mechanism** between these local transactions, aiming for **eventual consistency**.

With SAGA, you trade **immediate consistency** for long-term consistency. If something goes wrong during the saga, you need to define a strategy for **compensation actions** to bring the overall system back to a consistent state, hence the "epic journey" metaphor.
  
### Modern Approaches

#### Acknowledged Unreliability

The philosophy here is one of embracing a **partially reliable** set of distributed systems. Instead of trying to guarantee strong consistency across services, the focus is on managing and mitigating **inconsistencies** and **failures** through robust service designs and effective monitoring.

#### DDD and Bounded Contexts

When microservices are designed using **Domain-Driven Design (DDD)**, each microservice focuses on a specific business domain, or "Bounded Context." By doing so, services tend to be **more independent**, leading to fewer cross-service transactions in the first place.

This approach promotes a strong focus on **clear service boundaries** and effective **communication** and **collaboration** between the stakeholders who understand those boundaries and the associated service behavior.

#### CQRS and Event Sourcing

The **Command Query Responsibility Segregation (CQRS)** pattern involves separating read and write operations. This clear **separation of concerns** reduces the need for cross-service transactions.

With **Event Sourcing**, each state change is **represented as an event**, providing a reliable mechanism to propagate changes to multiple services in an **asynchronous** and **non-blocking** manner.

What is crucial here is that the **proliferation** of these patterns and concepts in modern software and system design is a direct result of the **unique needs and opportunities** presented by new paradigms such as microservices. Instead of retrofitting old ways of thinking into a new environment, the focus is on adapting notions of consistency and reliability to the realities of modern, decentralized, and highly dynamic systems.
<br>

## 9. Explain the concept of '_Bounded Context_' in the _microservices architecture_.

In the context of **microservices architecture**, the principle of "_Bounded Context_" emphasizes the need to segment a complex business domain into distinct and manageable sections.

It suggests a partitioning based on business context and **clearly defined responsibilities** to enable individual teams to develop and manage independent microservices.

### Core Concepts

#### Ubiquitous Language

- Each microservice and its **bounded context** must have a clearly defined "domain language" that is comprehensible to all the members of the team and aligns with the business context.

#### Context Boundaries

- A bounded context delineates the scope within which a particular model or concept is operating, ensuring that the model is consistent and meaningful within that context.

- It establishes clear boundaries, acting as a bridge between **domain models**, so that inside the context a specific language or model is used.

- For instance: in the context of a customer, it might use a notion of "sales leads" to represent potential customers, while in the context of sales, it would define leads as initial contact or interest in a product.

#### Data Consistency

- The data consistency and integrity is local to the bounded context. Each context's data is safeguarded using transactions, and data is only propagated carefully to other contexts to which it has a relationship.
 
- It ensures that the understanding of data by each service or bounded context is relevant and up-to-date.

  **Example**: In an e-commerce system, the product catalog context is responsible for maintaining product data consistency.

#### Teams & Autonomy

Each bounded context is maintained and evolved by a specific team responsible for understanding the business logic, making it self-governing and allowing teams to work independently without needing to understand the logic of other contexts.

#### Relationship with Source Code

- The concept of a bounded context is implemented and realized within the source code using Domain-Driven Design (DDD) principles. Each bounded context typically has its own codebase.

#### Code Example: Bounded Context and Ubiquitous Language

Here is the Tic Tac Toe game Model:

```java
// Very specific to the context of the game
public enum PlayerSymbol {
    NOUGHT, CROSS
}

// Specific to the game context
public class TicTacToeBoard {
    private PlayerSymbol[][] board;
    // Methods to manipulate board
}

// This event is purely for the game context to indicate the game has a winner.
public class GameWonEvent {
    private PlayerSymbol winner;
    // getter for winner
}
```
<br>

## 10. How do you handle _failure_ in a _microservice_?

In a **microservices architecture**, multiple smaller components, or **microservices**, work together to deliver an application. Consequently, a failure in one of the services can have downstream effects, potentially leading to system-wide failure. To address this, several **best practices** and **resilience mechanisms** are implemented.

### Best Practices for Handling Failure

#### Fault Isolation

- **Circuit Breaker Pattern**: Implement a circuit breaker that isolates the failing service from the rest of the system. This way, the failure doesn't propagate and affect other services.

- **Bulkhead Pattern**: Use resource pools and set limits on the resources each service can consume. This limits the impact of failure, ensuring that it doesn't exhaust the whole system's resources.

#### Error Recovery

- **Retry Strategy**: Implement a **retry mechanism** that enables services to recover from transient errors. However, it's important to determine the **maximum limit** and **backoff policies** during retries to prevent overload.

- **Failsafe Services**: Set up **backup systems** so that essential functionalities are not lost. For example, while one service is down, you can temporarily switch to a reduced-functionality mode or data backup to avoid complete system failure.

### Resilience Mechanisms

#### Auto-scaling

- **Resource Reallocation**: Implement auto-scaling to dynamically adjust resources based on **load** and **performance metrics**, ensuring the system is capable of handling the current demand.

#### Data Integrity

- **Eventual Consistency**: In asynchronous communication between services, strive for **eventual consistency** of data to keep services decoupled. This ensures data integrity is maintained even when a service is temporarily unavailable.

- **Transaction Management**: Use a two-phase commit mechanism to ensure **atomicity** of transactions across multiple microservices. However, this approach can introduce performance bottlenecks.

### Data Management

- **Data Redundancy**: Introduce redundancy (data duplication) in services that need access to the same data, ensuring data availability if one of the services fails.

- **Caching**: Implement data caching to reduce the frequency of data requests, thereby lessening the impact of failure in the data source.

- **Data Sharding**: Distribute data across multiple databases or data stores in a partitioned manner. This reduces the risk of data loss due to a single point of failure, such as a database server outage.

#### Communication

- **Versioning**: Maintain backward compatibility using **API versioning**. This ensures that services can communicate with older versions if the newer one is experiencing issues.

- **Message Queues**: Decouple services using a message queuing system, which can help with load leveling and buffering of traffic to handle temporary fluctuations in demand.

- **Health Checks**: Regularly monitor the health of microservices to identify and isolate services that are malfunctioning or underperforming.

#### Best Practices for Handling Failure

- **Self-Healing Components**: Develop microservices capable of self-diagnosing and recovering from transient faults, decreasing reliance on external mechanisms for recovery.

- **Graceful Degradation**: When a service fails or becomes overloaded, gracefully degrade the quality of service provided to users.

- **Continuous Monitoring**: Regularly monitor all microservices and alert teams in real-time when there is a deviation from the expected behavior.

- **Failure Isolation**: Localize and contain the impact of failures, and provide backup operations and data whenever possible to provide ongoing service.
<br>

## 11. What design patterns are commonly used in _microservices architectures_?

Several design patterns lend themselves well to **microservices architectures**, offering best practices in their design and implementation.

### Common Design Patterns

- **API Gateway**: A single entry point for clients, responsible for routing requests to the appropriate microservice.
  
- **Circuit Breaker**: A fault-tolerance pattern that automatically switches from a failing service to a fallback to prevent service cascading failures.

- **Service Registry**: Microservices register their network location, making it possible to discover and interact with them dynamically. This is essential in a dynamic environment where services frequently start and stop or migrate to new hosts.

- **Service Discovery**: The ability for a microservice to locate and invoke another through its endpoint, typically facilitated by a service registry or through an intermediary like a load balancer.

- **Bulkhead**: The concept of isolating different parts of a system from each other to prevent the failure of one from affecting the others.

- **Event Sourcing**: Instead of persisting the current state of an entity, the system persists a sequence of events that describe changes to that entity, allowing users to reconstruct any state of the system.

- **Database per Service**: Each microservice has a dedicated database, ensuring autonomy and loose coupling.

- **Saga Pattern**: Orchestrates multiple microservices to execute a series of transactions in a way that maintains data consistency across the services.

- **Strangler Fig**: A deployment pattern that gradually replaces $monolithic\ or \( conventional$ systems with a modern architecture, such as microservices.

- **Blue-Green Deployment**: This strategy reduces downtime and risk by running two identical production environments. Only one of them serves live traffic at any point. Once the new version is tested and ready, it switches.

- **A/B Testing**: A/B testing refers to the practice of making two different versions of something and then seeing which version performs better.

- **Cache-Aside**: A pattern where an application is responsible for loading data into the cache from the storage system.

- **Chained Transactions**: Instead of each service managing its transactions, the orchestration service controls the transactions between multiple microservices.

### Code Example: Circuit Breaker using Hystrix Library

Here is the Java code:

```java
@CircuitBreaker(name = "backendA", fallbackMethod = "fallback")
public String doSomething() {
  // Call the service
}

public String fallback(Throwable t) {
  // Fallback logic
}
```

The term "Circuit Breaker" is from Martin Fowler's original description. It's a well-known hardware pattern used in electrical engineering. When the current is too high, the circuit "breaks" or stops working until it is manually reset. The software equivalent, in a microservices architecture, is designed to stop sending requests to a failing service, giving it time to recover.
<br>

## 12. Can you describe the _API Gateway_ pattern and its benefits?

The **API Gateway** acts as a single entry point for a client to access various capabilities of **microservices**.

### Gateway Responsibilities

- **Request Aggregation**: Merges multiple service requests into a unified call to optimize client-server interaction.
- **Response Aggregation**: Collects and combines responses before returning them, benefiting clients by reducing network traffic.
- **Caching**: Stores frequently accessed data to speed up query responses.
- **Authentication and Authorization**: Enforces security policies, often using **JWT** or **OAuth 2.0**.
- **Rate Limiting**: Controls the quantity of requests to safeguard services from being overwhelmed.
- **Load Balancing**: Distributes incoming requests evenly across backend servers to ensure performance and high availability.
- **Service Discovery**: Provides a mechanism to identify the location and status of available services.

### Key Benefits

- **Reduced Latency**: By optimizing network traffic, it minimizes latency for both requests and responses.
- **Improved Fault-Tolerance**: Service failures are isolated, preventing cascading issues. It also helps in providing **fallback** functionality.
- **Enhanced Security**: Offers a centralized layer for various security measures, such as end-to-end encryption.
- **Simplified Client Interface**: Clients interact with just one gateway, irrespective of the underlying complicated network of services.
- **Protocol Normalization**: Allows backend services to use different protocols (like REST and SOAP) while offering a consistent interface to clients.
- **Data Shape Management**: Can transform and normalize data to match what clients expect, hiding backend variations.
- **Operational Insights**: Monitors and logs activities across services, aiding in debugging and analytics.

### Contextual Use

The gateway pattern is particularly useful:

- In systems built on **SOA**, where it is used to adapt to modern web-friendly protocols.
- For modern applications built with **microservices**, especially when multiple services need to be accessed for a single user action.
- When integrating with **third-party services**, helping in managing and securing the integration.

### Code Example: Setting Up an API Gateway

Here is the Python code:

```python
from flask import Flask, request
import requests

app = Flask(__name__)

@app.route('/')
def api_gateway():
    # Example: Aggregating and forwarding requests
    response1 = requests.get('http://service1.com')
    response2 = requests.get('http://service2.com')

    # Further processing of responses

    return 'Aggregated response'
```
<br>

## 13. Explain the '_Circuit Breaker_' pattern. Why is it important in a _microservices ecosystem_?

The **Circuit Breaker** pattern is a key mechanism in microservices architecture that aims to enhance **fault tolerance** and **resilience**.

### Core Mechanism

- **State Management**: The circuit breaker can be in one of three states: Closed (normal operation), Open (indicating a failure to communicate with the service), and Half-Open (an intermittent state to test if the service is again available).
- **State Transition**: The circuit breaker can transition between states based on predefined triggers like the number of consecutive failures or timeouts.

### Benefits

1. **Failure Isolation**: Preventing cascading failures ensures that malfunctioning services do not drag down the entire application.
2. **Latency Control**: The pattern can quickly detect slow responses, preventing unnecessary resource consumption and improving overall system performance.
3. **Graceful Degradation**: It promotes a better user experience by continuing to operate, though possibly with reduced functionality, even when services are partially or completely unavailable.
4. **Fast Recovery**: After the system or service recovers from a failure, the circuit breaker transitions to its closed or half-open state, restoring normal operations promptly.

### Practical Application

In a microservices environment, the circuit breaker pattern is often employed with libraries like Netflix's Hystrix or `Resilience4J` and languages like **Java** or **.NET**.

#### Hystrix Example

Here is the Java code:

```java
HystrixCommand<?> command = new HystrixCommand<>(HystrixCommand.Setter
  .withGroupKey(HystrixCommandGroupKey.Factory.asKey("ExampleGroup"))
  .andCommandPropertiesDefaults(HystrixCommandProperties.Setter()
     .withCircuitBreakerErrorThresholdPercentage(50)));
```

#### Resilience4J Example

Here is the Java code:

```java
CircuitBreakerConfig config = CircuitBreakerConfig.custom()
  .failureRateThreshold(20)
  .ringBufferSizeInClosedState(5)
  .build();

CircuitBreaker circuitBreaker = CircuitBreakerRegistry.of(config).circuitBreaker("example");
```

#### .NET's Polly Example

Here is the C# code:

```csharp
var circuitBreakerPolicy = Policy
  .Handle<SomeExceptionType>()
  .CircuitBreaker(3, TimeSpan.FromSeconds(60));
```

#### Asynchronous Use Cases

For asynchronous activities, such as making API calls in a microservices context, the strategy can adapt to handle these as well. Libraries like Polly and Resilience4j are designed to cater to asynchronous workflows.
<br>

## 14. What is a '_Service Mesh_'? How does it aid in managing _microservices_?

A **Service Mesh** is a dedicated infrastructure layer that simplifies network requirements for **microservices**, making communication more reliable, secure, and efficient. It is designed to reduce the operational burden of communication between microservices.

### Why Service Mesh?

- **Zero Trust**: Service Meshes ensure secure communication, without relying on individual services to implement security measures consistently.

- **Service Health Monitoring**: Service Meshes automate health checks, reducing the risk of misconfigurations.

- **Traffic Management**: They provide tools for controlling traffic, such as load balancing, as well as for A/B testing and canary deployments.

- **Adaptive Routing**: In response to dynamic changes in service availability and performance, Service Meshes can redirect traffic to healthier services.

### Elements of Service Mesh

The Service Mesh architecture comprises two primary components:

- **Data Plane**: Controls the actual service-to-service traffic. It's made up of proxy servers, such as Envoy or Linkerd, which sit alongside running services to manage traffic.

- **Control Plane**: Manages the configuration and policies that the Data Plane enforces. It includes systems like Istio and Consul.

### Key Capabilities

- **Load Balancing**: Service Meshes provide intelligent load balancing, distributing requests based on various criteria, like latency or round-robin.

- **Security Features**: They offer a suite of security capabilities, including encryption, authentication, and authorization.

- **Traffic Control**: Service Meshes enable fine-grained traffic control, allowing you to manage traffic routing, failover, and versioning.

- **Metrics and Tracing**: They collect and provide key operational telemetry, making it easier to monitor the health and performance of your microservices.

### Code Example: Service Mesh Components in Kubernetes

Here is the `YAML` configuration:

For the **Control Plane**:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: control-plane-pod
  labels:
    component: control-plane
spec:
  containers:
  - name: controller
    image: control-plane-image
    ports:
    - containerPort: 8080
---
apiVersion: v1
kind: Service
metadata:
  name: control-plane-service
spec:
  selector:
    component: control-plane
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
```

For the **Data Plane**:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: service-1-pod
  labels:
    app: service-1
spec:
  containers:
  - name: service-1-container
    image: service-1-image
    ports:
    - containerPort: 8080
  - name: proxy
    image: envoyproxy/envoy-alpine
  containers:
  - name: service-2-container
    image: service-2-image
    ports:
    - containerPort: 8080
  - name: proxy
    image: envoyproxy/envoy-alpine
```

In this example, Envoy serves as the sidecar proxy (Data Plane) injected alongside `service-1` and `service-2`, and the `control-plane-pod` and `control-plane-service` represent the control plane.
<br>

## 15. How do you ensure _data consistency_ across _microservices_?

**Data consistency** in a microservices architecture is crucial for ensuring that business-critical operations are executed accurately.

### Approaches to Data Consistency in Microservices 

1. **Synchronous Communication**:  Via REST or gRPC, which ensures immediate consistency but can lead to performance issues and tight coupling.
2. **Asynchronous Communication**: Using message queues which ensure eventual consistency but are more resilient and performant.
3. **Eventual Consistency with Compensating Actions**: Involves completing a series of potentially inconsistent operations within a microservice and compensating for any errors, often orchestrated through a dedicated event handler.

### Code Example: Synchronous Communication

Here is the Python code:

```python
# Synchronous Communication with RESTful APIs
import requests

def place_order(order):
    response = requests.post('http://order-service/api/v1/orders', json=order)
    if response.status_code == 201:
        return "Order placed successfully"
    else:
        return "Order placement failed"

# Potential downside: If the order service is down, the basket service cannot commit the transaction.
```

### Code Example: Asynchronous Communication with Event Bus

Here is the RabbitMQ code:

**Producer:**

```python
import pika

def send_order(order):
    connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
    channel = connection.channel()
    channel.queue_declare(queue='order_queue')
    channel.basic_publish(exchange='', routing_key='order_queue', body=order)
    connection.close()

# No blocking operation or transactional context ensures high performance.
```

**Consumer:**

```python
# Consumes the 'order_queue'
# Processes the order asynchronously
```

### Eventual Consistency with Compensating Actions

#### CAP Theorem
The CAP theorem states that it's impossible for a distributed data store to simultaneously provide more than **two** of the following three guarantees: Consistency, Availability, and Partition Tolerance.

#### BASE (Basically Available, Soft state, Eventually consistent)

BASE is an acronym that describes the properties of many NoSQL databases. It includes:

1. **Basically Available**: The system remains operational most of the time.
2. **Soft state**: The state of the system may change over time, even without input.
3. **Eventually Consistent**: The system will become consistent over time, given that the applications do not input any new data.

### Transactional Outbox Pattern

This pattern, used in conjunction with an **event store or message broker**, ensures **atomic operations** across services. The microservice first writes an event to an "outbox" table within its own database before committing the transaction. A specialized, outbox-reading process then dispatches these events to the message broker.

#### Advantages

- Ensures **atomicity**, preventing events from being disclosed due to a partially committed transaction.
- Mitigates the risk of **message loss** that might occur if an external event publishing action happens after the transaction is committed.

#### Code Example: Transactional Outbox Pattern

Here is the Java code:

```java
// Using Java's Spring Data JPA and RabbitMQ
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Modifying;
import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.query.Param;

public interface OutboxEventRepository extends JpaRepository<OutboxEvent, Long> {

    @Modifying
    @Query(value = "INSERT INTO outbox_event (id, eventType, payload) VALUES (:id, :eventType, :payload)", nativeQuery = true)
    void create(@Param("id") long id, @Param("eventType") String eventType, @Param("payload") String payload);
}

public class OrderService {
    private final OutboxEventRepository outboxEventRepository;
    
    public void placeOrder(Order order) {
        // ... Perform order placement
        
        outboxEventRepository.create(order.getId(), "OrderPlacedEvent", toJson(order));
        
        // ... Commit transaction
    }
}
```
<br>



#### Explore all 60 answers here 👉 [Devinterview.io - Microservices](https://devinterview.io/questions/software-architecture-and-system-design/microservices-interview-questions)

<br>

<a href="https://devinterview.io/questions/software-architecture-and-system-design/">
<img src="https://firebasestorage.googleapis.com/v0/b/dev-stack-app.appspot.com/o/github-blog-img%2Fsoftware-architecture-and-system-design-github-img.jpg?alt=media&token=521fd2a9-0d56-49c0-a723-9bd6ca081893" alt="software-architecture-and-system-design" width="100%">
</a>
</p>


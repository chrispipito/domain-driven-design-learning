# Core Concepts of Domain-Driven Design

## Ubiquitous Language
- **Definition**: Ubiquitous Language is a shared language that is developed collaboratively by domain and technical experts. It is used consistently throughout the creation and modification of a software product in conversations, documentation, and code.
- **Importance**: Ubiquitous Language helps bridge the communication gap between domain experts and techical experts. It ensures that everyone has a clear and consistent understanding of the domain concepts, reducing misunderstandings and ambiguity.
- **Collaboration**: Creating a Ubiquitous Language involves close collaboration between domain and technical experts. It requires iterative refinement and continuous feedback to make sure that the language accurately represents the domain. The first occurrence of this collaboration is often in the form of an EventStorming session. (See EventStorming below)

## Bounded Contexts
- **Definition**: A specific area of the domain that has its own Ubiquitous Language and a clear boundary. It represents a logical boundary within which a particular model is defined and applicable.
- **Understanding the problem domain**: To identify Bounded Contexts, it's essential to understand the problem domain and the subdomains within it. Each subdomain may have its own set of concepts, rules, and relationships.

## Context Mapping
- **Definition**: Context Mapping is a process for identifying and defining relationships and interactions between Bounded Contexts within a domain. Helping to understand how the contexts relate to each other, how they communicate, and how they fulfill the overall business goals.
- **Importance**: Complex domains will have multiple Bounded Contexts that need to interact and exchange information. Context Mapping establishes a clear understanding of these relationships, enabling effective communication and integration between the contexts.

- **Relationship Patterns**: Context Mapping defines several patterns that represent the relationships between Bounded Contexts.
These patterns include:
  - **Partnership**: Bounded Contexts that have a cooperative relationship and collaborate to fulfill a goal. A subset of their domain models are shared and align their development efforts.
  - **Shared Kernel**: Bounded Contexts that share a small common domain model that is essential for their interaction. The shared kernel is kept stable and must evolve slowly with the agreement of all bounded contexts involved.
- **Rules**:
    1. Keep the kernel small
    2. Have an explicit boundary
    3. Have a clear integration process within the shared kernel
 
  - **Customer-Supplier**: One Bounded Context (the supplier) provides services and/or information to another Bounded Context (the customer). The customer's needs drive the development of the supplier's services.
  - **Conformist**: One Bounded Context conforms to the domain model of another Bounded Context. The conformist context uses the same language and concepts as the upstream bounded context to avoid translation and maintain compatibility.
  - **Anticorruption Layer**: A Bounded Context uses an Anticorruption Layer to protect its own domain model from the influence of other contexts. The layer translates and adapts the external models and services to fit the internal domain model.
  - **Open Host Service**: A Bounded Context that provides a set of open interfaces(services) that other bounded contexts can consume. The services are designed to be generic and reusable. This allows multiple bounded contexts to integrate with them.
  - **Published Language**: A Bounded Context that defines a published language like a domain-specific language (DSL) or set of APIs that other bounded contexts can use to communicate with it. The published language encapsulates the bounded context's domain model and provides a stable interface for integration.

- **Upstream and Downstream Relationships**:
  - **Importance**: Identifying upstream and downstream relationships during Context Mapping lets us understand the flow of information, dependencies and the impact of changes. The relationships guide the design and evolution of the system by highlighting which bounded contexts have greater influence and which bounded contexts must to adapt to changes within their dependencies. It is important to consider the direction of influence and coupling when defining the relationships between bounded contexts. Upstream contexts strive for stability and backward compatibility seeking to minimize the impact on downstream bounded contexts. Downstream bounded contexts are designed to handle changes in the upstream with mechanisms in place to adapt to evolving interfaces and contracts.
  - **Upstream Context**: Influences and/or provides services to another bounded context. It is the source of dependencies and has control over the contracts and interfaces with the downstream contexts. Upstream contexts are typically more stable and have a higher level of autonomy.
  - **Downstream Context**: Depends on and/or consumes the services provided by an upstream context. It is influenced by the upstream bounded context and needs to adapt to the contracts and interfaces exposed by the upstream. Downstream bounded contexts are more susceptible to changes in the upstream and have little to no control over their dependencies.


- **Integration Strategies**: Context Mapping also helps define the integration strategies between bounded contexts. These strategies determine how the bounded contexts exchange data and invoke each other's services. Common integration strategies include:
  - **REST APIs**: Bounded Contexts expose their services through REST APIs, allowing other contexts to consume them over HTTP.
  - **Messaging**: Bounded Contexts communicate asynchronously through messaging systems, such as message queues or event-driven architectures.
  - **Shared Database**: Bounded Contexts share a common database, but each context owns and manages its own schema and data.
  - **Remote Procedure Invocation**: Bounded Contexts invoke each other's services using remote procedure calls (RPC) or gRPC.


- **Evolution and Governance**: Context Mapping is an ongoing process that evolves along with the domain and the system. As the understanding of the domain deepens and the business requirements change, the relationships between Bounded Contexts may need to be updated. Context Mapping should be part of the overall governance process, ensuring that the interactions between contexts remain aligned with the business goals and the domain model.

## Event Storming 
(Alberto Brandolini is the inventor and creator of EventStorming and the EventStorming Workshop. Paul Rayner is an expert and published author on EventStorming. You can find books, workshops and other resources provided by Alberto and Paul in the Resources section.)

- **Definition**: EventStorming is a lightweight, rapid learning collaborative workshop that brings together domain experts and technical experts to explore and model the domain. It focuses on identifying and visualizing the key domain events, entities, and processes.
- **Process**: During an EventStorming session, participants gather around a large wall or board and use sticky notes to represent domain events. They collaboratively identify the events that occur within the domain, the entities involved, and the processes that trigger or react to those events.
- **Benefits**: Event Storming helps in quickly gaining a shared understanding of the domain, uncovering hidden complexities, and identifying potential Bounded Contexts. It promotes collaboration and alignment towards a common vision of the domain.
- **Outcomes**: The outcomes of an EventStorming session include a visual representation of the domain, identification of key events, entities, and processes, and a better understanding of the relationships and interactions within the domain.
Relation to DDD: EventStorming is often used as a precursor to applying DDD principles. It helps in discovering and defining Bounded Contexts, identifying Aggregates, and understanding the flow of Domain Events. The insights gained from EventStorming sessions can inform the creation of a more refined and accurate domain model.

## Entities
- **Definition**: Entities are domain objects that have a unique identity they are defined by rather than their attributes. They represent the core concepts of the domain and are often long-lived and mutable.
- **Characteristics**: Entities have a lifecycle and can change their attributes over time while retaining their identity. They are responsible for encapsulating domain logic and behavior related to their identity.

## Value Objects
- **Definition**: Value Objects are immutable domain objects that do not have a unique identity. They are defined by their attributes and are often used to describe the properties or characteristics of Entities.
- **Characteristics**: Value Objects are immutable, meaning their state cannot be changed once they are created. They are typically small, simple objects that represent a concept or a value in the domain.

## Aggregates
- **Definition**: Aggregates are a cluster of domain objects (Entities and Value Objects) that are treated as a single unit for data changes and consistency. They define a consistency boundary within which invariants(conditions or rules that must always be in place for a system to be in a valid state, representing consistency and integrity constraints of the domain model.) are maintained.
- **Aggregate Root**: The Aggregate Root is the entry point and the only member of an Aggregate that can be directly accessed from outside the Aggregate. It is responsible for ensuring the integrity and consistency of the Aggregate.

## Domain Events
- **Definition**: Domain Events represent important occurrences or state changes in the domain that are significant to other parts of the system. They capture the memory of something that has happened in the domain.
- **Characteristics**: Domain Events are immutable and often triggered by the behavior of Aggregates. They can be used to communicate changes across Bounded Contexts and enable loose coupling between different parts of the system.

## Domain Services
- **Definition**: Domain Services are stateless operations that encapsulate domain logic that doesn't naturally fit within Entities or Value Objects. They provide a way to express complex domain behavior that spans multiple domain objects.
- **Characteristics**: Domain Services are stateless and operate on domain objects. They encapsulate domain logic that involves coordination, orchestration, or complex calculations.

These core concepts form the foundation of Domain-Driven Design and provide a common vocabulary for modeling and implementing complex business domains. Throughout the tutorials and examples, we'll explore how these concepts are applied in practice and how they contribute to building maintainable and expressive software systems.

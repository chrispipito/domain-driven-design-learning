# Core Concepts of Domain-Driven Design

## Ubiquitous Language
- **Definition**: Ubiquitous Language is a shared language that is developed collaboratively by the domain experts and technical experts. It is used consistently throughout the creation and modification of a software product, in conversations, documentation, and code.
- **Importance**: Ubiquitous Language helps bridge the communication gap between domain experts and techical experts. It ensures that everyone has a clear and consistent understanding of the domain concepts, reducing misunderstandings and ambiguity.
- **Collaboration**: Creating a Ubiquitous Language involves close collaboration between domain experts and technical experts. It requires iterative refinement and continuous feedback to ensure that the language accurately represents the domain. The first occurrence of this collaboration is often in the form of an EventStorming session.

## Bounded Contexts
- **Definition**: A Bounded Context is a specific area of the domain that has its own Ubiquitous Language and a clear boundary. It represents a logical boundary within which a particular model is defined and applicable.
- **Understanding the problem domain**: To identify Bounded Contexts, it's essential to understand the problem domain and the subdomains within it. Each subdomain may have its own set of concepts, rules, and relationships.

## Context Mapping
- **Definition**: Context Mapping is the process of identifying and defining the relationships and interactions between different Bounded Contexts within a domain. It helps in understanding how the contexts relate to each other, how they communicate, and how they collaborate to fulfill the overall business goals.
Importance: In a complex domain, there are often multiple Bounded Contexts that need to interact and exchange information. Context Mapping helps in establishing a clear understanding of these relationships, enabling effective communication and integration between the contexts.

### Relationship Patterns: Context Mapping defines several common patterns for representing the relationships between Bounded Contexts. These patterns include:
- **Partnership**: Two or more Bounded Contexts have a cooperative relationship and closely collaborate to fulfill a common goal. They share a subset of their domain models and align their development efforts.
- **Shared Kernel**: Two or more Bounded Contexts share a small, common domain model that is essential for their interaction. The shared kernel is kept stable and evolves slowly with the agreement of all the involved contexts.
- **Customer-Supplier**: One Bounded Context (the supplier) provides services or information to another Bounded Context (the customer). The customer's needs drive the development of the supplier's services.
- **Conformist**: One Bounded Context conforms to the domain model of another Bounded Context. The conformist context uses the same language and concepts as the upstream context to avoid translation and maintain compatibility.
- **Anticorruption Layer**: A Bounded Context uses an Anticorruption Layer to protect its own domain model from the influence of other contexts. The layer translates and adapts the external models and services to fit the internal domain model.
- **Open Host Service**: A Bounded Context provides a set of open interfaces or services that other contexts can consume. The services are designed to be generic and reusable, allowing multiple contexts to integrate with them.
- **Published Language**: A Bounded Context defines a published language, such as a domain-specific language (DSL) or a set of APIs, that other contexts can use to communicate with it. The published language encapsulates the context's domain model and provides a stable interface for integration.


### Integration Strategies: Context Mapping also involves defining the integration strategies between Bounded Contexts. These strategies determine how the contexts exchange data and invoke each other's services. Common integration strategies include:
- **REST APIs**: Bounded Contexts expose their services through REST APIs, allowing other contexts to consume them over HTTP.
- **Messaging**: Bounded Contexts communicate asynchronously through messaging systems, such as message queues or event-driven architectures.
- **Shared Database**: Bounded Contexts share a common database, but each context owns and manages its own schema and data.
- **Remote Procedure Invocation**: Bounded Contexts invoke each other's services using remote procedure calls (RPC) or gRPC.


# Evolution and Governance: Context Mapping is an ongoing process that evolves along with the domain and the system. As the understanding of the domain deepens and the business requirements change, the relationships between Bounded Contexts may need to be updated. Context Mapping should be part of the overall governance process, ensuring that the interactions between contexts remain aligned with the business goals and the domain model.

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

These core concepts form the foundation of Domain-Driven Design and provide a common vocabulary for modeling and implementing complex business domains. In the next sections, we'll explore how these concepts are applied in practice and how they contribute to building maintainable and expressive software systems.

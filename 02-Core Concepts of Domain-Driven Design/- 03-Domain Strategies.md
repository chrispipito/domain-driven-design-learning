# Domain Strategies

Distinguishing the different domain types in your system guides the selection of which strategies and patterns you will choose.  

## Core Domain:
- **Definition**: The unique and critical aspects of the business that differentiates it from competitors and provides a competitive advantage.
- **Importance**: Knowing the Core Domain helps in deciding where to place significant effort, focus, and investment. The development efforts are aligned with the organizatations goals and value proposition. This alignment and focus enables teams to invest in delivering software solutions that directly contribute to the succes and growth of the business.
- **Strategy**: Let's put our best people and focus here. We need business and technical expertise, great collaborative skills, design skills, and great at abstraction. These people will need to model and explore different ways of modeling the system. This is where a ubiquitious langauge will be formed within a bounded context that is explicit and optimized for this core domain. All of the tactical patterns of Domain-Driven Design live here.

## Supporting Domain:
- **Definition**: Essential to the systems functionality and success overall.
- **Importance**: Essential for enabling and enhancing the core domain allowing the system to operate effectively and effeciently. Supporting domains are still complex systems requireing domain expertise to be implemented correctly. Any neglect in these domains can lead to suboptimal performance, technical debt, and makes it more difficult in adapting to future changes.
- **Strategy**: Make sure competent and talented people are creating this software solution. Involve business experts.

## Generic Domain:
- **Definition**: Not specific or unique aspects of the business.
- **Importance**: These domains do not require any custom development, are not part of the unique value or critical aspects that differentiate the business or provide a competitive advantage.
- **Strategy**: Avoid opportunity costs and purchase off-the-shelf software. If this is not an option, make sure competent people are building this software, but know that it is not where the investment should be made.

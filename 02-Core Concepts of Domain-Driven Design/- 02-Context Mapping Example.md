# Context Mapping Example

### Example Context Map
Let's take a look at an example context map for a would be online retail system. In this system, we have the following Bounded Contexts:

- **Order Management**: Handles customer orders and coordinates with other contexts to fulfill orders.
- **Inventory Management**: Manages inventory levels, reserves stock, and provides availability of products.
- **Shipping**: Handles the end-to-end shipping process (packaging, labeling, tracking of orders).
- **Catalog**: Manages the product catalog (product information, categories, pricing).
- **Billing**: Handles the billing process (invoicing, payment processing, refunds).
- **Customer**: Manages customer information (profile data, addresses, preferences)

![image](https://github.com/chrispipito/domain-driven-design-learning/assets/90569206/fa0b4e2d-df88-4761-b7da-67527d326018)





**In the context map above, the arrows indicate the direction of influence as well as the flow of information between Bounded Contexts.** 
- Order Management is in a partnership relationship with Inventory Management.
- Shipping and Billing are downstream and are conformists to Order Management.
- Catalog has an open host service to Inventory Management.
- Customer is an upstream Bounded Context to Order Management, and has a shared kernel relationship.

**The interactions between the Bounded Contexts are as follows**:
- Order Management places orders and reserves stock with Inventory Management.
- Inventory Management provides product data to the Catalog.
- Shipping receives order information from Order Management to handle deliveries.
- Billing generates invoices and processes payments based on order information from Order Management.
- Customer provides customer data to Order Management.

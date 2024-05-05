# Work In Progress

### Example Context Map
Let's take a look at an example context map for a would be online retail system. In this system, we have the following Bounded Contexts:

- **Order Management**: Responsible for handling customer orders and coordinating with other contexts to fulfill the orders.
- **Inventory Management**: Manages the inventory levels, stock reservations, and availability of products.
- **Shipping**: Handles the shipping process, including packaging, labeling, and tracking of orders.
- **Catalog**: Manages the product catalog, including product information, categories, and pricing.
- **Billing**: Handles the billing process, including invoicing, payment processing, and refunds.
- **Customer**: Manages customer information, including profile data, addresses, and preferences.





**In this context map, the arrows indicate the direction of influence and the flow of information between the Bounded Contexts.** 
- Order Management has a partnership relationship with Inventory Management.
- Shipping and Billing are downstream conformists to Order Management.
- Catalog is an open host service to Inventory Management.
- Customer is an upstream Bounded Context to Order Management, with a shared kernel relationship.

**The interactions between the Bounded Contexts are as follows**:
- Order Management places orders and reserves stock with Inventory Management.
- Inventory Management provides product data to Catalog.
- Shipping receives order information from Order Management to handle the delivery.
- Billing generates invoices and processes payments based on order information from Order Management.
- Customer provides customer data to Order Management.

# agent-mall

## Project Overview

**agent-mall** is an agent-first e-commerce platform where both sellers and buyers are represented by AI bots. Unlike traditional models (e.g., Shopee) that require manual interaction, this system allows merchants to deploy "Seller Agents" to automatically list products, while customers use "Buyer Agents" to automatically search, compare, and shop.

## Objectives

Build a new e-commerce infrastructure where AI doesn't just assist but plays an active role in the buying and selling process, helping to:
- Optimize transaction efficiency
- Reduce manual operations
- Enhance user experience

## System Architecture

### API-First Architecture

The entire system is designed with an **API-first** architecture, where bots interact directly with the platform through a standard set of APIs:

- **Product API**: Product management (CRUD, inventory updates, pricing)
- **Search API**: Product search and filtering
- **Order API**: Order processing (create, cancel, track status)
- **Negotiation API**: Price and terms negotiation
- **Tracking API**: Shipping and delivery tracking

## Core Components

### 1. Seller Agent (Seller Bot)

**Functions:**
- Automatically list products with complete information:
  - Product images
  - Detailed descriptions
  - Pricing
  - Inventory
- Optimize product content (SEO, descriptions, keywords)
- Update information in real-time through API
- Manage orders and provide automatic responses

**Features:**
- Automatically create and update product listings
- Analyze and optimize pricing based on market conditions
- Intelligent inventory management
- Automatically respond to reviews and questions

### 2. Buyer Agent (Buyer Bot)

**Functions:**
- Automatically search for products based on user requirements
- Analyze and compare products based on criteria:
  - Purchase volume
  - Ratings and reviews
  - Pricing
  - Shop reputation
  - Product quality
- Recommend optimal choices
- Place orders when confirmed by the user

**Features:**
- Intelligent multi-criteria search
- Automatic price and quality comparison
- Price negotiation with Seller Agents
- Order tracking and status updates
- Similar product recommendations

## Users

### User Types

#### 1. Merchants (Sellers)
Merchants are business owners or retailers who want to sell products on the platform. They interact with the system through Seller Agents.

**Characteristics:**
- May have existing inventory management systems
- Need to manage multiple products simultaneously
- Require real-time updates on sales and inventory
- Want to optimize pricing and product visibility
- May operate multiple stores or product categories

**Use Cases:**
- Small business owners automating their online presence
- Retailers managing large product catalogs
- Dropshippers coordinating with suppliers
- Brands managing their product listings
- Marketplace sellers optimizing their listings

**Interaction Model:**
- Configure Seller Agent with product data sources
- Set business rules and pricing strategies
- Monitor agent performance through dashboards
- Override agent decisions when necessary
- Review and approve automated actions

#### 2. Customers (Buyers)
Customers are end-users who want to purchase products. They interact with the system through Buyer Agents.

**Characteristics:**
- Have specific needs or preferences
- May not know exactly what they want
- Value time and convenience
- Want the best deals and quality
- May shop for themselves or others

**Use Cases:**
- Busy professionals who want automated shopping
- Price-conscious shoppers looking for deals
- Gift buyers needing recommendations
- Bulk purchasers comparing options
- Tech-savvy users who prefer AI assistance

**Interaction Model:**
- Provide natural language requests to Buyer Agent
- Review and approve agent recommendations
- Set preferences and constraints (budget, quality, etc.)
- Monitor order status through agent updates
- Provide feedback to improve future recommendations

#### 3. Platform Administrators
Administrators manage the overall platform, ensuring system stability, security, and compliance.

**Responsibilities:**
- Monitor system health and performance
- Manage user accounts and permissions
- Oversee agent behavior and compliance
- Handle disputes and escalations
- Maintain API documentation and standards

### User Journey

#### Merchant Onboarding
1. **Registration**: Merchant creates account and provides business information
2. **Agent Setup**: Configure Seller Agent with product data sources (CSV, API, database)
3. **Business Rules**: Define pricing strategies, inventory thresholds, and automation rules
4. **Testing**: Test agent with sample products before going live
5. **Launch**: Activate agent to start listing and managing products
6. **Monitoring**: Track performance through analytics dashboard

#### Customer Onboarding
1. **Registration**: Customer creates account (optional for browsing)
2. **Preference Setup**: Configure shopping preferences, budget ranges, and priorities
3. **Agent Activation**: Enable Buyer Agent for personalized shopping assistance
4. **First Search**: Make initial product request to test agent capabilities
5. **Learning**: Agent learns from user feedback and purchase history
6. **Optimization**: Agent improves recommendations over time

## Core Flow

### Complete Transaction Flow

#### Phase 1: Product Discovery
```
Customer Request → Buyer Agent Analysis → Search API Query → Product Matching
```

**Detailed Steps:**
1. **Customer Input**: Customer provides natural language request (e.g., "I need a wireless mouse under $50")
2. **Intent Analysis**: Buyer Agent parses request to extract:
   - Product category/type
   - Price constraints
   - Quality requirements
   - Urgency level
   - Additional preferences
3. **Search Execution**: Agent queries Search API with structured parameters
4. **Result Collection**: Platform returns matching products with metadata
5. **Initial Filtering**: Agent applies customer preferences and constraints

#### Phase 2: Product Comparison
```
Product List → Multi-criteria Analysis → Ranking Algorithm → Top Recommendations
```

**Detailed Steps:**
1. **Data Enrichment**: Agent gathers additional data for each product:
   - Seller reputation scores
   - Historical sales data
   - Review sentiment analysis
   - Price history and trends
   - Shipping options and costs
2. **Scoring**: Each product is scored across multiple dimensions:
   - Price competitiveness (weighted by customer preference)
   - Quality indicators (reviews, ratings, seller reputation)
   - Value proposition (features vs. price)
   - Availability and shipping speed
   - Return policy and customer service
3. **Ranking**: Products ranked using weighted scoring algorithm
4. **Shortlisting**: Top 3-5 products selected for presentation
5. **Comparison Matrix**: Agent creates side-by-side comparison

#### Phase 3: Recommendation & Decision
```
Top Products → Customer Presentation → Customer Review → Selection/Refinement
```

**Detailed Steps:**
1. **Presentation**: Buyer Agent presents top recommendations with:
   - Key differentiators highlighted
   - Pros and cons for each option
   - Price breakdown including shipping
   - Estimated delivery times
2. **Customer Interaction**: Customer can:
   - Request more details on specific products
   - Ask for alternatives
   - Adjust constraints (e.g., increase budget)
   - Request price negotiations
3. **Refinement**: Agent refines search based on feedback
4. **Decision**: Customer selects product or requests negotiation

#### Phase 4: Negotiation (Optional)
```
Price Request → Seller Agent Evaluation → Counter-offer → Agreement/Rejection
```

**Detailed Steps:**
1. **Negotiation Initiation**: Buyer Agent sends negotiation request via Negotiation API
2. **Seller Agent Analysis**: Seller Agent evaluates:
   - Current profit margin
   - Inventory levels
   - Market conditions
   - Customer purchase history
   - Competitive pricing
3. **Response Generation**: Seller Agent responds with:
   - Accept offer
   - Counter-offer with justification
   - Reject with alternative (e.g., bundle deal)
4. **Iteration**: Multiple rounds of negotiation if needed
5. **Agreement**: Both agents agree on final price and terms
6. **Order Creation**: Proceed to order placement

#### Phase 5: Order Placement
```
Product Selection → Order Creation → Payment Processing → Order Confirmation
```

**Detailed Steps:**
1. **Order Assembly**: Buyer Agent creates order with:
   - Selected product(s)
   - Agreed price
   - Shipping address
   - Payment method
2. **Validation**: System validates:
   - Product availability
   - Inventory levels
   - Payment method validity
   - Shipping address
3. **Order Submission**: Order API creates order record
4. **Seller Notification**: Seller Agent receives order notification
5. **Inventory Update**: Seller Agent automatically updates inventory
6. **Confirmation**: Both parties receive order confirmation

#### Phase 6: Fulfillment & Tracking
```
Order Confirmation → Seller Processing → Shipping → Delivery → Completion
```

**Detailed Steps:**
1. **Order Processing**: Seller Agent:
   - Prepares order for shipment
   - Generates shipping label
   - Updates order status to "Processing"
2. **Shipping**: When shipped:
   - Tracking number generated
   - Order status updated to "Shipped"
   - Tracking API updated with shipping details
3. **In Transit**: Buyer Agent monitors:
   - Real-time tracking updates
   - Estimated delivery date
   - Delivery exceptions
4. **Delivery**: Upon delivery:
   - Order status updated to "Delivered"
   - Customer notified
   - Review prompt sent
5. **Completion**: After delivery confirmation:
   - Transaction marked complete
   - Funds released to seller
   - Feedback collected

### Agent-to-Agent Communication Flow

#### Direct Agent Interactions
```
Buyer Agent ←→ Platform APIs ←→ Seller Agent
```

**Communication Patterns:**
1. **Asynchronous Messaging**: Agents communicate through platform APIs, not directly
2. **Event-Driven Updates**: Agents subscribe to relevant events (new orders, price changes)
3. **State Synchronization**: Platform maintains single source of truth
4. **Conflict Resolution**: Platform handles concurrent modifications

#### Negotiation Flow Diagram
```
Buyer Agent                    Platform                    Seller Agent
     |                            |                            |
     |-- Negotiation Request ---->|                            |
     |                            |-- Forward Request -------->|
     |                            |                            |
     |                            |<-- Counter-offer ---------|
     |<-- Counter-offer ----------|                            |
     |                            |                            |
     |-- Accept/Reject ---------->|                            |
     |                            |-- Notify Result ---------->|
     |                            |                            |
```

### Error Handling & Edge Cases

#### Common Scenarios
1. **Product Out of Stock**: 
   - Buyer Agent notified immediately
   - Alternative products suggested
   - Back-in-stock notifications available

2. **Price Changes During Negotiation**:
   - Platform locks price during active negotiation
   - Timeout mechanism for stale negotiations
   - Automatic re-evaluation if negotiation expires

3. **Payment Failures**:
   - Buyer Agent notified of failure
   - Alternative payment methods suggested
   - Order held until payment resolved

4. **Shipping Delays**:
   - Tracking API updates with delays
   - Buyer Agent proactively notifies customer
   - Seller Agent can provide compensation offers

5. **Order Cancellations**:
   - Either party can request cancellation
   - Platform handles refund processing
   - Inventory automatically restored

## Workflow Processes

### Sales Workflow (Seller)

1. Merchant deploys Seller Agent
2. Agent automatically collects product information
3. Creates and uploads products to platform
4. Optimizes content and pricing
5. Updates information in real-time
6. Processes orders and transactions automatically

### Purchase Workflow (Buyer)

1. User requests product search
2. Buyer Agent analyzes request
3. Searches and compares products
4. Recommends optimal choices to user
5. User confirms selection
6. Agent places order
7. Tracks order and updates status

## Shopping Flow Comparison

### Traditional E-commerce Flow vs. Agent-Based Flow

| Aspect | Traditional E-commerce Flow | Agent-Based Flow (agent-mall) |
|--------|----------------------------|-------------------------------|
| **Product Discovery** | User manually searches using keywords, filters, and categories | User provides natural language request; Buyer Agent analyzes intent and searches automatically |
| **Search Process** | User must refine search multiple times, try different keywords | Agent understands context and intent, performs intelligent multi-criteria search |
| **Product Comparison** | User manually opens multiple tabs, compares products side-by-side | Agent automatically compares products across multiple dimensions (price, quality, reviews, shipping) |
| **Analysis Depth** | User relies on visible information only | Agent analyzes hidden factors: price history, seller reputation trends, review sentiment |
| **Time Investment** | 15-30 minutes per product search | 2-5 minutes (mostly review time) |
| **Decision Support** | User makes decision based on limited information | Agent provides ranked recommendations with detailed pros/cons and justifications |
| **Price Negotiation** | Fixed prices only; no negotiation possible | Automated negotiation between Buyer Agent and Seller Agent |
| **Price Optimization** | User must manually find best deals across platforms | Agent automatically finds best prices and negotiates discounts |
| **Order Placement** | User manually fills forms, selects options, confirms details | Agent assembles order, validates information, user only confirms final selection |
| **Order Tracking** | User must manually check tracking status | Agent proactively monitors and updates user on order status |
| **Error Handling** | User discovers issues (out of stock, delays) and must take action | Agent detects issues early, suggests alternatives, handles automatically when possible |
| **Personalization** | Generic recommendations based on browsing history | Deep personalization based on preferences, past purchases, and learned behavior |
| **Multi-tasking** | User must be actively engaged throughout process | User can set request and let agent work in background |
| **Learning** | Platform learns from user behavior but limited | Agent learns from each interaction, improves recommendations over time |
| **Scalability** | User can only handle one search at a time efficiently | Agent can handle multiple concurrent searches and comparisons |
| **Complex Queries** | Difficult to express complex requirements | Natural language support for complex, multi-criteria requests |
| **Seller Interaction** | Limited to reviews and Q&A sections | Direct agent-to-agent communication for negotiations and inquiries |
| **Inventory Management** | User discovers out-of-stock items during checkout | Agent checks availability in real-time, suggests alternatives immediately |
| **Shipping Optimization** | User must compare shipping options manually | Agent factors shipping costs and speed into recommendations |
| **Post-Purchase** | User must manually track and follow up | Agent monitors delivery, handles issues, requests feedback automatically |

### Key Advantages of Agent-Based Flow

1. **Time Savings**: Reduces shopping time by 70-80% through automation
2. **Better Decisions**: AI-powered analysis considers more factors than human comparison
3. **Price Optimization**: Automated negotiation and price comparison ensure best deals
4. **Proactive Management**: Agents handle issues before they become problems
5. **Personalization**: Deep learning from user behavior provides increasingly relevant recommendations
6. **Scalability**: Handle multiple shopping tasks simultaneously
7. **Accessibility**: Natural language interface makes shopping accessible to all users

## API Specification

### Product API
- `GET /api/products` - Get product list
- `GET /api/products/:id` - Get product details
- `POST /api/products` - Create new product
- `PUT /api/products/:id` - Update product
- `DELETE /api/products/:id` - Delete product
- `PUT /api/products/:id/inventory` - Update inventory
- `PUT /api/products/:id/price` - Update price

### Search API
- `GET /api/search` - Search products
- `GET /api/search/compare` - Compare products
- `GET /api/search/suggestions` - Search suggestions

### Order API
- `POST /api/orders` - Create order
- `GET /api/orders/:id` - Get order information
- `PUT /api/orders/:id/status` - Update order status
- `DELETE /api/orders/:id` - Cancel order

### Negotiation API
- `POST /api/negotiations` - Start negotiation
- `PUT /api/negotiations/:id/offer` - Submit offer
- `PUT /api/negotiations/:id/accept` - Accept offer
- `PUT /api/negotiations/:id/reject` - Reject offer

### Tracking API
- `GET /api/tracking/:orderId` - Track order
- `GET /api/tracking/:orderId/status` - Get shipping status

## Technology & Tools

- **Backend**: API-first architecture
- **AI/ML**: Machine learning for recommendation and optimization
- **Real-time**: WebSocket or Server-Sent Events for real-time updates
- **Database**: Support for complex queries and real-time updates

## Benefits

### For Sellers
- Reduce product management time
- Automatically optimize pricing and content
- Increase sales efficiency
- Quick response to customers

### For Buyers
- Automatic search and comparison
- Personalized product recommendations
- Save shopping time
- Intelligent shopping experience

## Future Development

- Multi-language support
- Integration with payment platforms
- Expansion to other commerce types
- Improved AI models for recommendation and negotiation
- Analytics dashboards for both sellers and buyers

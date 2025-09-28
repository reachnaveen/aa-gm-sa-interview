Here is the comprehensive C4 diagram set for the Hotel Voucher Notification System. 
### 1. Context Diagram
Shows the high-level system context with external actors and systems:

Gate Agents using Gate Applications
Passengers receiving notifications
External systems (Operations Hub, Notification Hub, Sabre Services)
![Context](diagrams/C4_Context.png)

#### 2. Container Diagram
Details the internal architecture of the notification system:

API Gateway: Azure API Management for security and rate limiting
Event Processor: Handles flight cancellation events from Operations Hub
Notification Orchestrator: Core workflow engine
Flight Analyzer: Checks flight availability and passenger eligibility
Supporting services: Service Bus, Cosmos DB, Key Vault, Application Insights
![Container](diagrams/Container_Diagram.png)

### 3. Component Diagram
Breaks down the Notification Orchestrator into specific components:

Message Handler, Eligibility Checker, Availability Validator
Passenger Service, Notification Service, Audit Service
Retry Handler for failed notifications
![Component](diagrams/3-component.png)

### 4. Deployment Diagram
Shows the Azure infrastructure with security and networking:

Network Security: WAF, Private endpoints, Network Security Groups
Compute: Functions in dedicated subnets
Data: Cosmos DB and Service Bus with private connectivity
Security: Key Vault, Azure AD, Security Center, Sentinel
Monitoring: Application Insights and Log Analytics
![Deployment](diagrams/Deployment_Architecture.png)

### 5. Sequence Diagram
Illustrates the complete workflow from flight cancellation to passenger notification, including:

Event processing and validation
Flight availability checking
Passenger retrieval and notification
Error handling and retry logic
![Context](diagrams/Sequence_Diagram.png)


### Key Design Principles Implemented:
#### Security:
Private endpoints for all data services
WAF protection for external traffic
Managed identities for service authentication
Network segmentation with NSGs

#### Reliability:
Event-driven architecture with Service Bus
Retry mechanisms for failed notifications
Comprehensive audit logging
Multi-zone deployment for high availability

#### Scalability:
Serverless Functions that auto-scale
Service Bus for reliable message processing
Cosmos DB for global distribution
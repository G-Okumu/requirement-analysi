# Requirement Analysis in Software Development.
Master the principles and methodologies of Requirement Analysis in the software development lifecycle (SDLC).

## What is Requirement Analysis?
Requirement Analysis is a critical phase in the Software Development Life Cycle (SDLC) that involves gathering, analyzing, validating, and documenting the requirements for a software project. It defines what the system should do, who will use it, and how it should perform, without detailing how to implement it technically.

## Detailed Explanation
Requirement Analysis is the process of understanding the exact needs and expectations of stakeholders (clients, users, and others involved) to build a system that solves their problems or fulfills their goals. It acts as a foundation for all subsequent phases of software development.

## Key Activities in Requirement Analysis
### Requirement Gathering:
Collecting requirements from stakeholders using techniques like interviews, questionnaires, observation, brainstorming, and document analysis.

### Requirement Elicitation:
Drawing out the true needs, including unstated or hidden requirements, through discussions and analysis.

### Requirement Specification:
Documenting requirements in a structured format, typically using an SRS (Software Requirements Specification) document.

### Requirement Validation:
Ensuring the requirements are correct, complete, unambiguous, and agreed upon by all stakeholders.

### Requirement Prioritization:
Ranking requirements based on business value, urgency, cost, or risk.

### Why is Requirement Analysis Important?
- Provides a clear roadmap for developers and designers to build the system.
- Clearly defined requirements prevent unnecessary features or changes later in the project.
- Ensures all stakeholders have a shared understanding of the project's goals.
- Early identification of incorrect or incomplete requirements saves time and money during later stages.


# Types of Requirements

## Functional Requirements

## Functional Requirements for Booking Management System

### 1. Booking Service

- **Initiate Bookings**:  
  Allows users to reserve rooms. Works in coordination with payment and availability systems.

- **Confirm/Cancel Bookings**:  
  Interfaces with the payment service; upon successful payment, booking is confirmed. Otherwise, it may cancel or roll back reservations.  
  *[Source: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7)*

---

### 2. Search & Availability

- **Search for Available Hotels/Rooms**:  
  Utilizes a search service backed by Elasticsearch to deliver results based on location, dates, and possibly filters like price or amenities.  
  *[Source: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7)*

---

### 3. Hotel Management

- **Manage Hotel Listings and Details**:  
  Hotel managers can add or update hotel information, manage room availability, prices, and descriptions via the Hotel Management Service.  
  *[Source: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7)*

---

### 4. View Booking Service

- **View Current and Past Bookings**:  
  Users (customers and hotel staff) can retrieve booking histories and details via the View Booking Service, which aggregates data from Redis (for recent bookings) and Cassandra (for archived data).  
  *[Source: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7)*

---

### 5. Notifications and Alerts

- **Send Booking Notifications**:  
  Notifies users or hotel managers about booking confirmations, modifications, or cancellations through notification services tied to messaging queues (Kafka).  
  *[Source: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7)*

---

### 6. Archival & Analytics

- **Store Completed or Canceled Bookings**:  
  Offload stale booking data to Cassandra for archive and use Kafka + Hadoop for analytics—supporting reporting, trends, and business insights.  
  *[Source: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7)*


## Non-Functional Requirements
These define performance, reliability, and quality aspects essential for booking management systems like this one:

## Non-Functional Requirements for Booking Management System

### 1. Low Latency

- **Fast Response Times**:  
  Search and booking operations should respond quickly, aided by caching (e.g., using Redis) and optimized data retrieval (e.g., Elasticsearch).  
  *[Sources: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7), [GeeksforGeeks](https://www.geeksforgeeks.org/system-design-of-airbnb-hotel-reservation-system/)*

---

### 2. High Availability & Reliability

- **Continuous Uptime**:  
  The system must remain available even under heavy traffic. Using load balancers, master–slave DB architectures, and microservice redundancy ensures high availability.  
  *[Sources: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7), [GeeksforGeeks](https://www.geeksforgeeks.org/system-design-of-airbnb-hotel-reservation-system/)*

---

### 3. Consistency

- **Accurate Availability and Booking Integrity**:  
  The system must prevent double-booking and ensure transactional consistency, especially during booking and payment flows.  
  *[Sources: GeeksforGeeks](https://www.geeksforgeeks.org/system-design-of-airbnb-hotel-reservation-system/), [Preparation Zone](https://www.preparationzone.com/design/pages/system_design_example/hotel_booking.html)*

---

### 4. Scalability

- **Handle Spikes in Demand**:  
  The system must scale horizontally—by adding nodes to services, databases, and caching layers—to support peak booking seasons or heavy user loads.  
  *[Sources: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7), [Preparation Zone](https://www.preparationzone.com/design/pages/system_design_example/hotel_booking.html)*

---

### 5. Fault Tolerance

- **Resilient Architecture**:  
  Use messaging queues and redundant services to isolate failures and continue operations when parts of the system fail.  
  *[Sources: Medium](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7), [Preparation Zone](https://www.preparationzone.com/design/pages/system_design_example/hotel_booking.html)*

---

### 6. Performance (Throughput)

- **Handle High Traffic**:  
  Services like search and booking must support high throughput and concurrent requests to maintain system performance under load.  
  *[Sources: Preparation Zone](https://www.preparationzone.com/design/pages/system_design_example/hotel_booking.html), [GeeksforGeeks](https://www.geeksforgeeks.org/system-design-of-airbnb-hotel-reservation-system/)*

# Acceptance Criteria.
### Importance of Acceptance Criteria in Requirement Analysis
<ul>
  <li>Clear Definition</li>
  <li>Enhances Communication</li>
  <li>Prvents Scope Creep</li>
</ul>

### Example: Acceptance Criteria for Checkout Feature in Booking Management System
- Successful Payment Processing:
The system must process payments using supported payment methods (credit card, PayPal, wallet).
- Booking Confirmation:
After successful payment, the user must receive a booking confirmation with a unique booking ID.
- Error Handling:
If payment fails, the system must notify the user with a clear error message and allow retry.

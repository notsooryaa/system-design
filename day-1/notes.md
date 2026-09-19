1. What is System Design?

 - What does the entire system need to look like so that it works reliably when thousands or millions of people use it?

for example:


                    ┌──────────────┐
                    │    Users     │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │ Load Balancer│
                    └──────┬───────┘
                           │
              ┌────────────┼────────────┐
              ▼            ▼            ▼
          API Server   API Server   API Server
              │            │            │
              └────────────┼────────────┘
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
           Cache                     Database


Then you start asking:

What happens if traffic increases 100x?
What happens if the database becomes slow?
What happens if one API server crashes?
How do we prevent double bookings?
Where should caching happen?
How do we handle millions of requests?
What happens if a payment succeeds but booking creation fails?
How do we monitor failures?
How do we deploy without downtime?

*That is system design.*

2. Functional vs Non-Functional Requirements

_Functional requirements_

These describe what the system does.

For your booking system:

Users can:

1. Register/login
2. Search salons
3. View available services
4. View available time slots
5. Create a booking
6. Cancel a booking
7. View booking history

These are functional requirements.

_Non-functional requirements_

These describe how the system should behave.

For example:

Availability: 99.9%

Response time: < 200ms for most requests

Users: 100,000

Salons: 1,500

System should handle traffic spikes

System should not create duplicate bookings

System should remain available if one server fails

These are often where system design becomes interesting.

3. Scalability

Imagine your application currently has:

1,000 users

Your architecture works perfectly.

Then your company grows:

10,000 users
100,000 users
1,000,000 users
10,000,000 users

Can your architecture continue handling the load?

That's scalability.

There are two major approaches.

Vertical scaling and Horizontal scaling

_Vertical scaling_

Make one machine stronger.

Before:

4 CPU
8 GB RAM

       ↓

After:

32 CPU
128 GB RAM

Simple, but there are physical and cost limits.

_Horizontal scaling_

Add more machines.

                Load Balancer
                     │
          ┌──────────┼──────────┐
          ▼          ▼          ▼
       Server 1   Server 2   Server 3

This is extremely important in modern system design.

4. Availability

Availability asks:

Is the system available when users need it?

99%
99.9%
99.99%
99.999%

These are called availability targets.

The interesting part is how small the difference sounds:

99%

versus

99.99%

But the downtime difference is significant.

5. Latency

Latency is:

How long does something take?

For example:

Client
  │
  │ request
  ▼
API
  │
  ▼
Database
  │
  ▼
API
  │
  ▼
Client

If the entire process takes:

50 ms

that's much different from:

2 seconds

System designers constantly think about reducing latency.


6. Throughput

Latency:

How long does ONE request take?

Throughput:

How many requests can the system handle?

Example:

10,000 requests / second

Your API might have:

100 ms latency

but still only handle:

500 requests/sec

before falling over.

So when designing systems, you'll constantly think about both:

Latency
+
Throughput


              Requirements
                   │
                   ▼
             Estimations
                   │
                   ▼
              API Design
                   │
                   ▼
             Data Modeling
                   │
                   ▼
          High-Level Architecture
                   │
                   ▼
             Scaling Strategy
                   │
                   ▼
        Reliability / Failure Cases
                   │
                   ▼
          Monitoring & Security
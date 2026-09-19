# Day 1 — System Design Fundamentals

## Problem

Design a salon booking system.

## Functional Requirements

- Users can view salons
- Users can view services
- Users can view available slots
- Users can create bookings
- Users can cancel bookings
- Users can view booking history

## Non-Functional Requirements

- High availability
- Low latency
- Scalable
- Reliable booking creation
- Prevent duplicate bookings

## Initial Architecture

Client
    ↓
NestJS API
    ↓
MySQL

## Future Scaling Considerations

- Load balancing
- Horizontal scaling
- Caching
- Database replication
- Async processing
- Monitoring

## Key Learnings

- Functional vs non-functional requirements
- Horizontal vs vertical scaling
- Availability
- Latency
- Throughput
- Basic system-design workflow
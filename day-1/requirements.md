Problem: Salon Booking System

You're designing a booking system with:

100,000 users
1,500 salons
10 million bookings

Users should be able to:

Search salons
View salon details
View services
View available slots
Create bookings
Cancel bookings
View booking history


# Requirements

## Functional Requirements

1. login/register
2. view salons and salon details
3. create/edit/cancel appointment
4. view all appointments
5. get slot and service details

## Non-Functional Requirements

1. should handle traffic while discount campaigns
2. retrive single user bookings and details in milisec
3. should not create dup bookings
4. should not accept diff booking in same slots
5. should have backup if incase the srever overloads
Question:

What would your high-level architecture look like?

        Client
           ↓
       Frontend
           ↓
      API/Backend 
   ↓             ↓
Databases.   Payment gateway


Question 3: Scaling.

Your system grows from 100,000 users to 10 million users.

What do you think will become a bottleneck in your current architecture, and what would you change to handle the increased traffic?

- have a single database can cause bottleneck in a huge amount of transaction at the same time, sacling horizontally here would be better, as we are using mySql we would prefer to scale vertically
- Also we should keep in mind with the load that the server takes in this particular scenario and be ready to scale our server too

Edit 

MySQL doesn't mean we should prefer vertical scaling.

Both approaches are possible:

Vertical Scaling
MySQL
2 CPU → 16 CPU
8GB → 64GB RAM

and eventually:

Horizontal / distributed scaling
          MySQL
        /       \
    Primary    Replica

Later, depending on the workload, we can consider things like:

Read replicas
Partitioning
Sharding
Caching
Better indexes
Query optimization



10M users
    ↓
Is API CPU high?
    ↓
Scale API

Is DB CPU high?
    ↓
Optimize / scale DB

Are DB reads overwhelming?
    ↓
Consider caching / read replicas

Are requests arriving in huge bursts?
    ↓
Consider load balancing / queues / rate limiting


Scenario:

Your API/Backend server suddenly crashes.

Questions:

What happens to users currently using the application?
- currently as the server went down every users rew would be cancelled and nothing is diplayed to there end

What happens to requests that were being processed?
- Those will not be queued anywhere as we dont have a queue worker right now

How would you design the system so that one backend server crashing doesn't bring down the entire application?

- we should have a load balacer with 3-4 servers up and ready so that when a server is down the req's are alotted to the next nearest servers right away
- also as we might deal with a huge transaction per sec even if before the load balancer alocattion some req might fail so have a queue worker and dequeue from there whould a right way of work here


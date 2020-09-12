1. Get the requirements done - what the service needs to do
2. Get the system interface definition - interface means how you will interact wit the system, like what all APIs do you need?
3. Back of the envelope estimation - meaning what will be the scale. Scale in terms of events, users, storage, network bandwidth(so as to determine load balancing), etc.
4. Defining data model - how data will flow among different components of the system. Purpose is to figure out the following:
    i. different entities in the system
    ii. interaction b/w entities
    iii. data managent - storage
    iv. data management-  transportation
    v. data management - encryption
What database to use? What kind of block storage to be used for storing media?
5. High-level design
5-6 core components to ensure the actual problem is solved from end-to-end
i. load-balancers in front of these components if needed
ii. differentiate b/w read and write - if huge difference then solve them differently
iii. distributed file system for media storage.
6. Detailed design
i. dig deeper into 2/3 components
ii. take interviewer's feedbacks
iii. present multiple approaches
iv. enlist pros and cons of multiple approaches
v. consider tradeoffs while keeping system constraints in mind
vi. data partitioning if massive amounts of data
vii. hot users v/s cold users
viii. what layers need caching to speed things up?
ix. what components need better load balancing?
7. Identifying and resolving bottlenecks
i. is there any single point of failure
ii. how to mitigate singpe P.o.F.
iii. db replicas so that we server our users if faced with failures
iv. are services replicated to avoid total system shutdown
v. how are we monitoring the performance of our service
vi. alerting for critical component failures and for performance degradation


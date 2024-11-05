# System design - Gaurav Sen


### [No. 1] For any scalable system points to look for

---
1. Optimise processes and increase throughput using the same resources (vertical scaling)
2. Prepare beforehand during non-peak hours (pre-processing and cron jobs)
3. Keep backup and avoid single point failure (Backups for resilience )
4. Hire more resources (Horizontal scaling)
5. Microservice architecture
6. Distributed system (partitioning, contributes to resilience, performance)
7. Load balancer (with some objective e.g. minimum order delivery time)
8. Decoupling (agnostic sub-system)
9. logging and metrics (for analytics, auditing, reporting, Machine learning)
10. Extensible (embracing decoupling in order to make an extensible system)

### [No. 2] System design basic

---

```
users       ---requests--->     | server (accepts/responds requests using APIs)
            <---response---     | server  
                                | server 
```
__Levels__
1. Example. you have a useful algo(code)
2. algo(code) is on your local server machine
3. algo(code) on some cloud(e.g. aws, so cloud provider will take case of resilience)
4. algo(code) is getting more traffic, so needs scaling
   - Solution 1. get bigger machine (vertical scaling)
   - Soutionl 2. get more machines (horizontal scaling)

**Horizontal scaling**
1. load balancing required
2. resilient*
3. Network calls (RPC)
4. data inconsistency (dirty write)
5. scales well as user increases*

**Vertical scaling**
1. load balancing not required as such
2. Single point failure
3. Inter-process communication*
4. consistent*
5. hardware limit

### [No. 3] LOAD BALANCING - Consistent Hashing

---
you have N server, and you have a traffic chunk(load), now you will distribute load
over all servers in an efficient way called `load balancing`.

Example:
- you have N servers 
- requests are coming with requestId (R0, R1, to Rm) 
- M1 = hashFunction(R1)
- (M1%N) is the server number(Sn) where a request will go
- hash function is random, so we will expect traffic will be evenly distributed.


> __Note:__ Now imagine you have added one more server, then Sn  = M1%(n+1)  
> With this, your Sn will change for older request ids also (e.g. for R1, Sn  = M1%(n+1)).  
> In real world R1 are not really random, and hashFunction will give the same result (M1) every time 
> so that request will go to the same server and some request information can be cached for efficiency  
> But this hashing approach each time with addition of a new server request allocation will be completely randomize and caching will be of no use.
> Here the problem is not the load balancing but the hashing algorithm.

### [No. 4] Consistent Hashing

---
https://www.geeksforgeeks.org/consistent-hashing/
https://www.youtube.com/watch?v=zaRkONvyGr8

- As part of this hashing, we define a hash function (h_func) which can give values from 0 to m-1.   
- we assume these values on a ring of number in ascending order (we can assume integer number line)
- Then we use a hash function (h_func) for calculating hashed value for server_id (e.g. h_func(S1), h_func(S2), h_func(S3), ...)  
and map it on the ring.
- Now whenever a request comes we use (h_func) for calculating hashed value for request_id and from the number line  
we will find immediate next mapped server and route the request to that server.
- This approach has a small flaw, imagine a case when multiple consecutive server crashed, in that case all the cascaded equivalent load  
will be routed to the immediate successor server, which is not good for a server.
- This flaw can fixed by virtualization of server on the ring, which basically means instead of mapping the one server at one point   
we can map the same server at multiple points on the ring using the same or different hash function.  
e.g.  for server S1, we can map it at `h_func(S1_a), h_func(S1_b), h_func(S1_c)`
or at `h_func2(S1), h_func2(S1), h_func2(S1)`
```java
// code example 
import java.util.*;

class ConsistentHashRing {
    private final TreeMap<Integer, String> ring = new TreeMap<>();
    private final int replicas;

    // Constructor to initialize replicas, default value is 3
    public ConsistentHashRing(int replicas) {
        this.replicas = replicas;
    }

    // Overloaded constructor to set default replicas as 3
    public ConsistentHashRing() {
        this(3);
    }

    // Function to calculate the hash of a value (using a simple string hash)
    private int getHash(String value) {
        return value.hashCode();
    }

    // Function to add a node in the ring with multiple replicas
    public void addNode(String node) {
        for (int i = 0; i < replicas; i++) {
            String replicaKey = node + "_" + i;
            int hash = getHash(replicaKey);
            ring.put(hash, node);
        }
    }

    // Function to remove a node from the ring
    public void removeNode(String node) {
        for (int i = 0; i < replicas; i++) {
            String replicaKey = node + "_" + i;
            int hash = getHash(replicaKey);
            ring.remove(hash);
        }
    }

    // Function to get the node for a given key
    public String getNode(String key) {
        if (ring.isEmpty()) {
            return null;
        }

        int hashValue = getHash(key);
        // Find the closest node in the ring using ceiling or wrap-around
        Map.Entry<Integer, String> entry = ring.ceilingEntry(hashValue);
        if (entry == null) {
            entry = ring.firstEntry();  // Wrap around to the beginning of the ring
        }
        return entry.getValue();
    }

    public static void main(String[] args) {
        ConsistentHashRing hashRing = new ConsistentHashRing();

        // Add nodes to the ring
        hashRing.addNode("Node_A");
        hashRing.addNode("Node_B");
        hashRing.addNode("Node_C");

        // Get the node for a key
        String key = "first_key";
        String node = hashRing.getNode(key);

        System.out.println("The key '" + key + "' is mapped to node: " + node);
    }
}
```
### [No. 5] What is a MESSAGE QUEUE and Where is it used?

---
https://www.youtube.com/watch?v=oUJbuFMyBDk

RabbitMQ, JMS, ZeroMQ

### [No. 6] What is a MICROSERVICE ARCHITECTURE and what are its advantages?

---
https://www.youtube.com/watch?v=qYhRvH9tJKw

MICROSERVICE is a single business unit.
Monolith has multiple business unit in the same service.

Monolith advantages: 
1. small and cohesive team
2. lesser moving parts deployments are easy 
3. less code duplicacy
4. faster, no network/rpc calls 

Monolith Disadvantages:
1. whole deployments required for every change
2. tough to understand the whole flow
3. tight-coupling

Microservice advantages:
1. easy to scale system
2. easy to start work from a microservice (a small business unit context needed)
3. parallel development easy, loose coupling is there that's y. 
4. lesser parts are hidden while deployment

Microservice Disadvantages:
1. tough to design and maintain all Microservice at once.
2. if two Microservices always talking to each other, its better to keep them in one.

### [No. 7] What is DATABASE SHARDING?

---










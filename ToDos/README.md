- POC on distributed databases consitency with RAFT
A distributed system needs to reach a consensus on what the actual state is. etcd uses the RAFT consensus
algorithm to achieve this, which ensures that at any given moment, each node’s state is
either what the majority of the nodes agrees is the current state or is one of the previously agreed upon states. 
Understand and design a distributed consensus POC with database 
https://www.allthingsdistributed.com/2008/12/eventually_consistent.html
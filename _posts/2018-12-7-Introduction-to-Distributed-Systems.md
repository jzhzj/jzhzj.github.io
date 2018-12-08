---
title: "Introduction to Distributed Systems"
date: 2018-12-7
tags: [Distributed Systems, Network]
header:
  teaser: "/images/Intro_to_distributed_systems/intro_header.jpg"
  image: "/images/Intro_to_distributed_systems/intro_header.jpg"
excerpt: "Distributed Systems, Networks"
---

When it comes to “distributed systems”, everyone’s first feeling is that it is something marvelous, something hard to learn. Looking at books or lectures about distributed systems, most of them are difficult to understand.  

### What is the Distributed System?  

Regarding the definition of distributed system, let’s first look at how it is defined in the book, Distributed Systems: Principles and Paradigms. “A distributed system is a collection of independent computers that appears to its users as a single coherent system.”  

With regard to this definition, our intuitive feeling is:  
-	First of all, this kind of system is relatively competitive, at least composed of several hosts. In the case of Google, Amazon and other service providers, their data centers are supported by tens of thousands of hosts.  
-	Secondly, although they are powerful, it’s not possible for cloud users to feel the existence of these hosts. In other words, we only see one system is working.  

From a process perspective, if two programs are running on two individual hosts, and they work together to provide a same service (or function), in theory, the system composed by these two programs can also be called “Distributed System”.  

Of course, the two programs can be different programs or the same program. If they are the same program, we can call it "cluster." The so-called cluster is the way to improve the service capability by continuously expanding the same program.  

The definitions of "distributed systems" and "clusters" are simple enough.  

![alt]({{ site.url }}{{ site.baseurl }}/images/Intro_to_distributed_systems/2network.jpg)  

### What are the advantage of distributed systems?  
So, why do we want to use a distributed system?  

Speaking of distributed systems, we have to talk about the ancestors of distributed systems - centralized systems. A centralized system is exactly the opposite of a distributed system. A centralized system is a way of distributing all the programs and functions to a single host to provide services.  

Centralized systems are easy to understand. For example, on our host PC or mobile phone, we installed all kinds of software on one machine. When you need some function, you will get it all from this machine. For example, like some projects we designed for course purpose, we deployed and installed web servers, databases, etc. on a single computer. The advantage is that it is easy to understand, easy to maintain, and you have deployed everything you want in a place where they are easy to find. On the other hand, the drawbacks are obvious. If the machine crashes, or the hard disk is broken, it will crash with the whole system, and if the backup is also on this hard disk, it would totally be a disaster.  

There is a famous saying about investment, that "Don't put all your eggs in one basket." The same is true for the system. The manufacturer's machine can't always guarantee that it will never fail. You can't guarantee that the hackers won't come to the base of your system. The most important thing is that you can't guarantee that there are no bugs in your programs. So, problems cannot be avoided and mistakes are inevitable. We can only disperse eggs into different baskets to alleviate the risk of one-point failure. This is why distributed systems are needed.  

Another reason to use a distributed system is scalability. After all, any host (even a minicomputer, supercomputer) will have performance limits. Distributed systems can scale horizontally by expanding the number of hosts. Everyone knows that Google's servers are mostly machines that do not have the best performance.  

### What challenges will the distributed system face?  

There is no doubt that distributed systems are more complex to implement than centralized systems are. Distributed systems will be harder to understand, design, build, and manage, which means that it is harder to discover hidden problems.  

When designing a distributed system, you often need to consider the following challenges:  
-	Heterogeneity: Distributed systems are based on different networks, operating systems, computer hardware, and programming languages. A common network communication protocol must be considered to mask the differences between heterogeneous systems. These differences are generally handled by middleware.  
-	Lack of global clocks: When programs need to collaborate, they coordinate their actions by exchanging messages. Close coordination often relies on a consensus on when the program actions occur, but in reality, the accuracy of the computer's synchronous clock on the network is greatly limited, that is, there is no global concept of correct time. This is a direct result of the fact that messages are sent over the network as the only means of communication.  
-	Consistency: Data is scattered or copied to different machines. How to ensure the consistency of data between hosts will become a difficult point.  
-	Fault tolerance: Any computer can be faulty and the faults are different. The timing of failures among them is also independent against each other. Generally distributed systems are designed to be allowed to partially fail without affecting the normal use of the entire system.  
-	Concurrency: The purpose of a distributed system is to share resources easily. Then each unit of resource in the system must be designed to be secure in a concurrent environment.  
-	Transparency: Failure of any component in a distributed system, or upgrade or migration of a host, is transparent to the user and is invisible.  
-	Openness: Distributed systems are written by different programmers. The components are ultimately integrated into a system. The interfaces published by the components must adhere to certain specifications and be understood by each other.  
-	Security: Encryption is used to provide proper protection for shared resources, and all sensitive information passed on the network needs to be encrypted. A denial of service attack is still a problem to be solved.  
-	Scalability: The system should be designed so that as the business volume increases, the corresponding system must also be able to expand to provide the corresponding services.  

### How to design distributed systems  

The essence of designing a distributed system is "how to reasonably split a system into multiple subsystems and deploy them to different machines." So, the primary consideration is how to properly split the system. Since the separated subsystems cannot exist in isolation, they must be connected through the network, so how to communicate between them becomes more important. Of course, in the communication process, system should be able to identify "enemy", to prevent information from being intercepted and tampered with in the process of transmission. This involves security issues. To adapt to the growing business needs of distributed systems, you need to consider its scalability as well. Distributed systems must also ensure reliability and data consistency.  

In summary, when designing a distributed system, the following issues should be considered:  

- How do you split the system into subsystems?  
- How do you manage communication between subsystems?  
- How do you ensure the security during communication?  
- How do you make the subsystem be extendable?  
- How do you guarantee the reliability of the subsystems?  
- How is the consistency of the data achieved?  

In fact, each of the above issues is not a simple question. Fortunately, we would like to thank open source for the technology of this era to be shared, and the cost of implementing complex systems is getting lower and lower. For example, when designing communication, we can use message-oriented middleware, such as Apache ActiveMQ, RabbitMQ, Apache RocketMQ, Apache Kafka, etc., and RPC frameworks such as Google Protocol Buffer and Thrift. When designing distributed computing, we can use MapReduce, Apache Hadoop, Apache Spark, etc. In terms of big data and distributed storage, we can choose Apache HBase, Apache Cassandra, Memcached, Redis, MongoDB and so on. In terms of distributed monitoring, commonly used technologies include Nagios, Zabbix, Consul, ZooKeeper, and so on.  

EJB Day4

Enterprise Java Beans related terms you need to be able to explain
what *ARE* they and what they *DO* / what is their *PURPOSE* (both).
* EJB
-> Enterprise Java Beans
=> Framework to ...
* J2EE 
-> Java 2 Enterprise Edition
=> A framework for Java handling HTTP protocol, reusable business components (beans), Data Persistence (JPA), security, reliability, load-balancing and other advanced technologies.
* JSP - Java Servlet Pages
-> Allows mixing Java code with HTML code using special tags.
* JSF - Java Servlet Faces
-> A framework separating UI from Data model
* JPA
-> Java Persistence API
=> Managing data between database and application using Entities and Entity Manager.
* DDD
-> Domain Driven Design
* JNDI 
-> Java Naming Directory Interface
=> Used by J2EE container to locate Beans that implement a specific interface required by client.
* Annotation
=> Modifies properties or add/modifes code of field, method, class. Applied at compilation time.
* Dependency Injection
=> Determine which necessary class to load at runtime (as opposed to compilation time, normally)
* What are the 4 tiers in EJB
=> Presentation, Business Logic, Persistance, Database
* Entity Manager / persistence provider
=> part of JPA, object that sychronizes Entities in database with Entities in memory (operations: persist, delete, merge, query)
* Bean
=> Business component
* Container
=> J2EE server e.g. Glassfish or JBoss or WebLogic
* Stateless Session Bean
=> Request-response, no session/continuity of interaction with a client
* Stateful Session Bean
=> Every client gets one bean for the entire duration of the session
* Message Driven Bean
=> Queue of requests, client will be called back when answer is available
* Signleton Bean
=> Only exactly one instance per container, may simultanously serve multiple clients, requires readers-writers locks to protect shared data
* Lifecycle of Stateless and Stateful session bean
=> draw the two lifecycles, including actions on each arrow edge
* Java RMI
-> Remote Method Invocation
=> Binary protocol used to call methods in objects existing on another machine.
* JPQL
-> Java Persistence Query Language
=> SQL-like language used by JPA to retrieve entities from database
* Clustering
-> Many computers acting as one server
* Load balancing
-> Ensuring that in a cluster of computers the load of each is more-less even.
* Failover
-> When a machine in cluster fails its tasks are taken over automatically by another machine.
* @Local
-> Bean is accessible within the same container/JVM only.
* @Remote
-> Bean is accessible from another JVM or even remote computer.
* @EJB
-> Annotation we put just before a reference to bean's interface.
It will open connection to server/container and instantiate proxy class to access the actual bean.
* @ConcurrencyManagement(CONTAINER)
-> Annotation to enable Readers/Writers locks.
* @Lock(WRITE)
-> Exclusive lock for writers - one writer at a time, no readers.
* @Lock(READ)
-> Shared lock for readers - many readers at a time, no writers.

Other questions:
* What does InitialContext ctx = new InitialContext(props); do?
-> Opens connection to server/container.

* What does ctx.lookup("beans.RestaurantRemote") call do?
- asks container whether it has a bean implementing "beans.RestaurantRemote" interface,
- defines and instantiates a proxy class to communicate with container and an instance of "beans.RestaurantRemote" bean inside of it

* Why do we need the "proxy class"?
- we can't access the bean directly, we must use RMI so the proxy class hides the complexity of actually making a remote call to bean's method.

* Draw lifecycles of stateful and stateless beans including state transitions and exact names of annotations in EJB3.

* Why do we need to passivate Stateful beans?
-> Stateful beans have to exist for the entire duration of client connection, meaning they are using resources (open files, databases, memory use) during their sometimes long inactivity periods. After certain inactivity period container may decide to free up memory of the Stateful bean by passivating it, meanig writing its state to persisten storage (hard drive). The bean will be revived only if and when the client sends another request.



A Data-Centric Approach
-----------------------

##### Preface

[The client/server architecture is a way to dispense a service from a central source.](http://composingprograms.com/pages/46-distributed-computing.html#client-server-architecture) Elos leverages this centralized system as the core stack is the primary locale for the elos service. The data processing and decision making which drive the elos experience occur at the server level.

When designing witht he client/server architecture there arise an issue of distributed data. This issue has been hidden in the past as manifestations of other problems - the need to refresh, the need to complete a full-formed request to a server before loading each page. The design of client applications across several platforms begins to realize this problem as one of distributed data. Elos does not shy from this clarification.

##### Solution

Elos takes a very centralized, data-driven approach. *There is no single source of truth in elos* The structure is still client/server - the near entirety of the computation resides on our servers and the clients server mostly has GUIs and human access points for the data processed and created by elos. They also server as a the location of human input.

Due to this masterless approach any client or the elos server can create data for a user, and the hub(link needed) system of the server will push that data to all clients. Clients should not perform any ad-hoc computation - rather they should simply display the data. This way, when things change they get updated and all clients will simply reflect that change. When autonmous agents analyze and make decisions based on the data available to them at the elos server main stack then they do so the same regardless of whether the entire distributed system is in equilibrium. We rely on _eventual consistency_. When more information is available to the elos agents they will make apt use of it.

The only communication between a nodes in the elos system is client -> server and server -> client. And this communication consists only of authentication protocols and data transfer.

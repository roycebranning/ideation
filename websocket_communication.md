WebSocket Communication
=======================

3 Prerequisites
---------------
Sockets provide a psuedo-synchronous form of communication with a server. There is no blocking on a request (or message) as with traditional HTTP.

Because the communication is bi-directional, the client store can remain up to date without polling the server.

This general and assumed consistency can lead to a guarantee that data is accurate, and allows assumptions to be made on data existence.

Problem
-------

How do you retrieve data that you have identifiers for, but no data for. How do you coordinate a server's response to a specific client request? Does this degrade the elos models of agent communication, wherein all agents connected with the same ids receive the updates of a single request?

Solution
--------

Acting as though the identifiers the client has been supplied thus far are guarantees for expected data returns, act aggressively on those promises.

When the need for data arrives, query the server, but move forward synchronously as though you have the data. Instantiate a record with the said id(s) in the store.

The subsequent server POST action with the data should fill in the null (loading) values of the records instantiated on query.

In practice this should prove very quick, as the UI renders along with the servers response over the socket.


Protocol
========

The general form is:

```json
{
  "action": "<action>", 
  "data": {
    "<kind>":{
      "some":"data"
    }
  }
}
```

There are three actions: GET, POST and DELETE. The server never uses GET.

GET is a query.
POST is create and update.
DELETE ditto.



GET
---

Client:

```json
{
  "action": "GET",
  "data": {
    "event": {
      "id": "alksdj1"
    }
  }
}
  ```

Server:

```json
{
  "action": "POST",
  "data": {
    "event": {
      "id": "alksdfj1",
      "name": "This is the event",
      "start_time": "2014-7-13-101200",
      "end_time": "2014-7-13-101200",
      "user_id": "asdfk1kl1"
    }
  }
}
```

Post
----

Client:

```json
{
  "action": "POST",
  "data": {
    "event": {
      "id": "lkajdsf12",
      "name": "This is my new event",
      "start_time": "2014-7-13-101200",
      "end_time": "2014-7-13-101200",
      "user_id": "asdfk1kl1"
    }
  }
}
```

Server:

```json
  {
    "action": "POST",
    "data": {
      "event": {
        "id": "lkajdsf12",
        "name": "This is my new event",
        "start_time": "2014-7-13-101200",
        "end_time": "2014-7-13-101200",
        "user_id": "asdfk1kl1"
    }
  }
}
```

Notice that the client populates the id, the server's response is confirmation.

Delete
------

Client:

```json
  {
    "action": "DELETE",
    "data": {
      "event": {
        "id": "kaljslfjk1"
    }
  }
}
```

Server:

Success:

```json
{
  "action": "DELETE",
  "data": {
    "event": {
      "id": "kaljslfjk1"
    }
  }
}
```

Failure:

```json
{
  "action": "POST",
  "data": {
    "event": {
      "id": "kaljslfjk1",
      "name": "This is my new event",
      "start_time": "2014-7-13-101200",
      "end_time": "2014-7-13-101200",
      "user_id": "asdfk1kl1"
    }
  }
}
```




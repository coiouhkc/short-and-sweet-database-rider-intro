---
marp: true
title: Short and sweet intro to Database Rider
description: Short and sweet intro to Database Rider
theme: uncover
paginate: true
_paginate: false
header: "**Alexei Bratuhin** Short and Sweet Intro to Database Rider"
footer: "![openvalue height:32px](./assets/openvalue-text-color.png)"
---

# Short and sweet

## Introduction to Database Rider

---

# Testing stateful microservices with Database Rider

---


# Alexei Bratuhin

alexei.bratuhin@googlemail.com
https://de.linkedin.com/in/alexei-bratuhin-21647811
https://www.xing.com/profile/Alexei_Bratuhin
https://github.com/coiouhkc

![bg right:30% height:256px](./assets/alexei-bratuhin.jpg)

---

# Intro, reason & background


<!--
Hello and welcome to yet another episode of short and sweet.

Today we're going to talk about testing stateful microservices using Database Rider.

What are microservices - most probably, you already know it, otherwise you wouldn't be here today. Same applies for the question "why we should test microservices".

For sake of simplicity, let's manifest following (very simplified) definition
-->

---

# Stage

<!--

Let's just define a stateful microservice as a kind of black box.

A black box, which has a state (database), some inputs (ingoing interfaces, e.g. requests, messages) and effects.

Those effects can be (either or both) outgoing interfaces (responses, messages) and changes to the database state.

So basically we can think of the stateful microservice as a state machine and that's exactly, what we want to test - given a database state and certain input, we assert expected database state and certain output.

 -->

 TODO: plantuml diagram of transition from one stage to another

---

# Objection, your honor!

<!--
Common objections you might hear trying to test the microservice as a black box might include references to the testing pyramid, hexagonal architecture, etc.

You might be told to use proper mocking techniques, etc

In this case you may ask, how one should otherwise sensibly test complex transactions, JPA listeners, database triggers, etc, and just move along.

Don't let the theory fool you! Don't let anyone prevent you from at least trying it yourself!

TODO: add "get that thing out of my face"?
-->

---

# Why Database Rider

<!--
I hope you have tests in your current project or at least you've seen projects having those tests.

You also might have heard of Arquillian Persistence Extension or have seen it in action.

If not, chances are high, that you've seen following code snippets in some form in your project.
-->


```
EntityManager#unwrap(Session.class)
```

```
TestUtil#createTestData(Connection)
```

```
@BeforeEach
void setUp() {
    datasource.getConnection()
    .execute("src/test/resources/some-test.sql");
}
```

---

# Here comes the shiny armor

```
@DBRider
```

```
@DataSet(value="dataset.yml", cleanBefore=cleanAfter=true)
```

```
@ExpectedDataSet(value="expected.yml")
```

---

# Cool fact

<!--
I am a fan of Quarkus and I like to point out cool features/integrations related to it
-->

Database Rider has Quarkus support!*

---

# Links

* https://github.com/database-rider/database-rider
* https://arquillian.org/arquillian-extension-persistence/

---

# Thanks!

TODO: QR code?
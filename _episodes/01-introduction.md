---
title: "Primer: Information exchange on the internet"
teaching: 20
exercises: 10
questions:
  - "What exactly is the internet?"
  - "How is information exchanged on the internet?"
  - "Working with APIs"
objectives:
  - "Understand the structure of APIs, including resources and query parameters"
keypoints:
  - "The internet is a network of computers (servers) that exchange information with each other."
  - "Various transport protocols, such as HTTP, dictate how information is transferred between servers."
  - "Data is returned in various formats by servers, including `json` and `xml`."
  - "APIs are exposed interfaces which allows us to programatically get data from the server."
---

# The internet revolution

The roots of the internet can be traced back to the 1960s, when the U.S. Department of Defense developed ARPANET to ensure reliable communication. In the 1980s and early 1990s, key innovations such as TCP/IP protocols, the World Wide Web, and the first web browsers transformed the internet from a research tool into a global public network.

Since then, it has expanded at an extraordinary pace. The rise of personal computers, mobile devices, and broadband made it accessible to billions. Social media, e‑commerce, and cloud computing further deepened its role in everyday life, making digital connectivity indispensable.

Its impact on society has been profound: it has revolutionized communication, democratized access to knowledge, reshaped economies, and enabled new forms of work and collaboration. Today, the internet touches nearly every aspect of modern life — from banking transactions and healthcare to air traffic control, power grids, and telecommunications. The internet has also created a hyper-connected world, where connecting and engaging with others happens instantaneously and at scale. Information (and disinformation) has also become more readily available. It is impossible for us to imagine a world without the internet today.

At the same time, it poses challenges, including issues of privacy, misinformation, and unequal access. Still, the internet remains one of humanity’s greatest innovations — a force that continues to redefine how we connect, live, and progress.

# The request life-cycle

Most of us associate the internet with a web browser like Chrome, Firefox, Safari — or even, God forbid, Internet Explorer. Yet what happens when you type `www.google.com` into the address bar is nothing short of an engineering marvel.

In reality, the internet does not understand human‑friendly names like `www.google.com`. Instead, every server on the internet is identified by an **IP address** — a unique series of numbers that acts like a digital street address. When you press `Enter`, your request first goes to the **Domain Name System (DNS)**, which translates the web address into the correct IP address. Your computer then uses that IP to locate Google’s servers, establishing a connection through a series of routers and networks in milliseconds.

This process, though invisible to us, happens billions of times every day and is the backbone of the hyper‑connected world we live in. From streaming videos to sending money across the globe, it all depends on this seamless orchestration of networking technologies working in the background.

# HTTP: The backbone of data transfer over the internet

# APIs: the new economy

# Resources and query parameters in API calls

{% include links.md %}

---
layout: post
title: KBOP 1.0.0 Release
tags:
  - release
  - archives
---

KBOP (Key Based Object Pool) version 1.0.0 was just released.  KBOP is a lightweight Keyed Object Pool which supports Single Key to Single Object Pooling or Single Key to Multiple Object Pooling. KBOP provides factory lifecycle's, metrics, borrowing, releasing and object invalidation.  Typical use cases are dealing with connections, sockets or caches that need to behave in a transactional fashion.  For example if authentication is expensive against a remote service you can use KBOP to store the authenticated client against a key.  Only one thread at a time (if in single mode) can have access to the client and must release it for the next thread to have access.  For more information visit <a href="http://www.kbop.org" target="_blank">http://www.kbop.org</a>
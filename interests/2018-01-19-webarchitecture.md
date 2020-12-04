---
layout: post
title: Scalable Web Architecture and Distributed Systems
tags:
  - Distributed System
description: 'by Kate Matsudaira (http://aosabook.org/en/distsys.html)'
---

# Scalable Web Architecture and Distributed Sysems

This article is focused on systems, but it is also applicable to other distributed systems

## Design of Large-scale web systems

* Make system **scalable**!
  * Distribute resource or accessing them across multiple servers
* Principle
  * Availability, Performance, Reliability, Scalability, Manageability, Cost
  * Consider trade-offs each other

## 새롭게 알게된 내용

* CDN\(Content Delivery Network\)

### Shared-nothing architecture

* Redundancy 부분에서 소개하고 있다.
* 웹 아키텍처에서 failure를 잘 처리하기 위해 대부분의 경우 redundancy 서비스, 데이터를 가지고 있다. 하나의 서버에 하나의 파일만 있는 경우 그 서버가 fail 되면 그 파일도 실패되기 때문에 이를 해결하기 위해 multiple redundant copy를 생성한다. 이는 데이터 뿐 아니라 서비스도 마찬가지이다.

  * 여기서 failover 개념이 나온다.

  Shared-nothing architecture를 만들게 되는 핵심은 중앙 관리하는 것을 두는 것이 아니라 각 노드가 독립적으로 동작할 수 있게 하는 것이다. 




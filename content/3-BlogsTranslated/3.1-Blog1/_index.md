---
title: "Blog 1"
date: 2026-04-03
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Building Event-Driven Applications with Amazon EventBridge

Event-Driven Architecture (EDA) is rapidly becoming the standard for building highly scalable and distributed microservices applications in the cloud. Instead of services calling each other directly (synchronous), they communicate by emitting and responding to "events" (changes in state). This helps components stay decoupled and makes the system more flexible.

This blog post will dive deep into using **Amazon EventBridge** – a serverless event bus that makes it easy to connect applications together using data from your own applications, integrated Software-as-a-Service (SaaS) applications, and AWS services.

---

## Why choose Event-Driven Architecture?

Migrating from a monolith or tightly coupled microservices architecture to an event-driven model brings many benefits:
- **Decoupling:** Services that emit events (Producers) do not need to know which services are consuming those events (Consumers).
- **Independent scaling:** You can easily add new consumers to process an event without needing to modify the producer.
- **Enhanced Resilience:** If a consumer fails, the event remains on the bus or queue and can be reprocessed once the system recovers.

---

## Core components of EventBridge

Event-driven architectural solutions with EventBridge consist of three main concepts you need to master:

> *Figure 1. Overall architecture; Events flow from the Source through the Bus to the Target.*

1. **Event Buses:** A pipeline that receives events. Your AWS account comes with a *default event bus* that receives events from AWS services. You can also create *custom event buses* for your internal applications.
2. **Rules:** Rules route events to a target based on an event pattern or on a schedule.
3. **Targets:** Where EventBridge sends the event after it matches a rule. Common targets include AWS Lambda, Amazon SNS, Amazon SQS, or AWS Step Functions.

---

## Comparing Message/Event services on AWS

When designing a system, choosing the right service is crucial:

| AWS Service | Communication Model | Best suited for |
| :--- | :--- | :--- |
| **Amazon SQS** | Point-to-point (Queue) | Decoupling heavy processing tasks, ensuring messages are not lost (Buffered). |
| **Amazon SNS** | Pub/Sub (Publish/Subscribe) | Sending the same message to multiple subscribers with ultra-low latency (Fanout). |
| **Amazon EventBridge** | Event Bus (Smart routing) | Complex event content filtering, integrating 3rd-party SaaS applications, multi-service routing. |

---

## Example: Event filtering with EventBridge Rule

One of the greatest strengths of EventBridge is the ability to filter the event payload before invoking a Target. 

For example, you only want to trigger an AWS Lambda function when an Order is successfully created with a value greater than $100:
```json
{
  "source": ["com.mycompany.orders"],
  "detail-type": ["OrderCreated"],
  "detail": {
    "status": ["SUCCESS"],
    "amount": [{ "numeric": [ ">", 100 ] }]
  }
}
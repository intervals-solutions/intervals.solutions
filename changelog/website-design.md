# Intervals - Website Design Document

## Overview
Website for Intervals - a high-performance, distributed notification scheduling system built with Kotlin, Micronaut, Kafka, and MongoDB.

---

## 1. Hero Section
**Headline**: "**Intervals** - Schedule Notifications at Scale"

**Subheadline**: "High-performance, distributed notification scheduling system for time-sensitive alerts, promotional campaigns, and workflow automation."

**CTA Buttons**:
- [Get Started] - links to Quick Start
- [View on GitHub] - links to repository
- [Documentation] - links to docs

**Visual**: Animated timeline showing message flow from input to scheduled execution

---

## 2. What is Intervals?

### Value Proposition
Intervals is a robust application designed to **schedule and trigger notifications at specified times in the future** with exceptional performance and reliability.

### Key Benefits
| Benefit | Description |
|---------|-------------|
| **High Performance** | Minimal latency delivery with optimized processing |
| **High Throughput** | Handles large volumes of concurrent notifications |
| **Scalable** | Horizontal scaling from small workloads to enterprise |
| **Reliable** | Built on Kafka + MongoDB with distributed locking |
| **Flexible Scheduling** | ISO 8601 support - single, duration, and periodic |

### Use Cases
- **Reminders & Alerts** - User notifications, deadline reminders
- **Promotional Campaigns** - Scheduled marketing messages
- **Workflow Automation** - Delayed triggers for business processes
- **Any time-sensitive system** - Where precise future notifications matter

---

## 3. How It Works

### Architecture Overview

Your Application (Producer) -> Intervals -> Kafka -> Your Application (Consumer)



### Data Flow
1. **Send** - Publish your message with schedule information
2. **Deliver** - Message appears for you at the right time

---

## 4. Schedules

Intervals uses **ISO 8601** based scheduling:

### Single Execution
```
2026-07-16T19:20:30.45Z
```
Execute once at the specified time.

### Periodic
```
R/2026-07-16T19:20:30.45Z/PT7H/2026-07-17T20:20:30.45Z
```
Execute every 7 hours from start to end date.

---

## 5. Quick Integration (Java)

### Step 1: Send a Scheduled Message

```kotlin
val producer = KafkaProducer<String, ByteArray>(properties)

val record = ProducerRecord<String, ByteArray>(
    "assignments.<your-tenant>",
    payload
)

record.headers().add("intervals-schedule", "2026-07-21T19:20:30.45Z")

producer.send(record)
```

### Step 2: Receive the Execution

```kotlin
consumer.subscribe("executions.t30600")

// When the scheduled time arrives,
// the message will be delivered here
// with all original headers preserved
```

---

## 6. Contact

email: intervals.application@gmail.com

---

## 7. Footer

**Resources**
- [Documentation](./documentation/)
- [API Reference](./documentation/)

---

## Design Guidelines

### Color Palette
- Navy: #0F172A
- White: #FFFFFF
- Accent Orange: #F59E0B

### Typography
- **Headings**: Inter, bold
- **Body**: Inter, regular
- **Code**: JetBrains Mono

### Tone
Professional, technical, developer-focused, reliable

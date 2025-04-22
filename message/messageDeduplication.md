# 📨 System Design: Message Deduplication System
In a distributed system, messages can sometimes be delivered more than once due to retries, network issues, or failures. But many systems require exactly-once processing — meaning we need to detect and ignore duplicates.

That’s where a Message Deduplication System comes in.

## ❓ Why Do Duplicates Happen?
- Network retries
- The producer sends the same message again
- Consumer crashes after processing but before acknowledging
- At-least-once delivery guarantees (common in Kafka, RabbitMQ, etc.)

## ✅ Goals of a Deduplication System
- Prevent processing the same message more than once
- Maintain data integrity
- Support idempotent behavior (safe to process the same message multiple times without side effects)
  
## 🧩 Key Components
### 1. Message ID or Unique Token
Each message should have a unique identifier (message_id, uuid, etc.). The deduplication system checks this ID.

### 2. Storage for Tracking IDs
We need a place to store processed message IDs for checking duplicates:
- In-memory (e.g. Redis)
- Persistent storage (e.g. database)
- Time-limited cache (TTL) to avoid growing forever

### 🧪3. Deduplication Logic
```
[ Producer ] 
     |
     v
[ Message Queue ] --> [ Deduplication Layer ]
                                 |
                        (Check if ID exists?)
                                 |
           Yes --> Drop Message      No --> Process Message
                                |
                      [ Store Message ID ]

```
### 🔍4. How to Check for Duplicates
A few strategies depend on what you have in your message.
#### ✅ Option 1: Check by message_id (Best Practice)
- Each message has a unique ID (UUID, Kafka offset, timestamp+user_id, etc.)
- Redis stores the message ID as a key, with a TTL (like 1 hour).
#### ✅ Option 2: Check by Hash of Message Content
- You hash the full message using something like SHA256.
- Use the hash as a Redis key.
#### ✅ Option 3: Composite Key (e.g., user_id:event_type)
- Useful when the same user can trigger a similar event multiple times (e.g., like_post).
- Redis key: dedup:<user_id>:<event_type>



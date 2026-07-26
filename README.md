# 🚀 Apache Kafka Interactive Simulators

A collection of lightweight, single-file HTML5/JS interactive visual simulators designed to build intuitive mental models of **Apache Kafka** core architecture, replication mechanics, partition routing, offset tracking, and consumer group rebalancing.

---

## 📸 What's Included

| Simulator File | Focus Area | Description |
| :--- | :--- | :--- |
| **`kafka_simulator.html`** | **3-Broker Basic Architecture** | Simulates event publishing, key hashing (`hash(key) % partitions`), leader/follower replication across 3 brokers, and offset commits to consumers. |
| **`kafka_6-broker_simulator.html`** | **6-Broker High Availability** | Demonstrates how 3 partitions with a Replication Factor of 3 (1 Leader + 2 Followers per partition) distribute load across a 6-broker cluster. |
| **`consumer_group_simulator.html`** | **Consumer Group Mechanics** | Visualizes partition assignment rules (1-to-1 mapping), handling over-provisioned idle consumers, and real-time rebalance events when instances crash or scale up. |

---

## 🎯 Key Concepts Visualized

1. **Producer Routing & Partitioning:**
   * Key Hashing (`hash(key) % Total Partitions`) to guarantee per-key sequential order.
   * Direct producer connection to Partition Leaders.
2. **Offset Tracking:**
   * Sequential, monotonically increasing non-negative integer offsets (`0, 1, 2, 3...`) stamped per partition.
   * Consumer offset bookmarking stored externally inside Kafka's `__consumer_offsets` topic.
3. **Replication & High Availability:**
   * Leader vs. Follower Replica distribution across physical brokers.
   * In-Sync Replica (ISR) data synchronization across nodes.
4. **Consumer Group Load Balancing:**
   * Division of partition labor across consumers under a shared `group.id`.
   * The strict 1-to-1 partition-to-consumer assignment rule within a single group.
   * Dynamic **Rebalance** execution when scaling consumer instances or simulating server crashes.

---

## 🛠️ How to Run Locally

These simulators require **zero external dependencies, frameworks, or backend servers**. They run directly in any modern web browser.

### Option 1: Using VS Code + Live Server (WSL / Linux / Windows / macOS)

1. Clone or download this repository into your working directory:
   ```bash
   git clone https://github.com/tameemsyed-k/kafka-interactive-simulator.git
   cd kafka-interactive-simulators
# 🚀 Apache Kafka Interactive Simulators

A collection of lightweight, single-file HTML5/JS interactive visual simulators designed to build intuitive mental models of **Apache Kafka** core architecture, replication mechanics, partition routing, offset tracking, and consumer group rebalancing.

---

## 📸 What's Included

| Simulator File | Focus Area | Description |
| :--- | :--- | :--- |
| **`kafka_simulator.html`** | **3-Broker Basic Architecture** | Simulates event publishing, key hashing (`hash(key) % partitions`), leader/follower replication across 3 brokers, and offset commits to consumers. |
| **`kafka_6broker_simulator.html`** | **6-Broker High Availability** | Demonstrates how 3 partitions with a Replication Factor of 3 (1 Leader + 2 Followers per partition) distribute load across a 6-broker cluster. |
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

## 🛠️ How to Download and Run Locally

These simulators require **zero external dependencies, frameworks, or backend servers**. They run directly in any modern web browser.


### Option 1: Using Git & VS Code + Live Server (Recommended)

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/tameemsyed-k/kafka-interactive-simulator.git](https://github.com/tameemsyed-k/kafka-interactive-simulator.git)
   cd kafka-interactive-simulator

Open in VS Code:

Bash
code .
Install the Live Server Extension:

Press Ctrl + Shift + X (or Cmd + Shift + X on macOS) to open Extensions.

Search for Live Server (by Ritwick Dey) and click Install.

Launch a Simulator:

Open any HTML file (e.g., consumer_group_simulator.html).

Click Go Live at the bottom-right status bar of VS Code (or right-click inside the file and select Open with Live Server).

Option 2: Direct Download (Without Git)
Click the green Code button at the top of this GitHub repository.

Select Download ZIP.

Extract the downloaded ZIP file on your machine.

Double-click any .html file (e.g., kafka_simulator.html) to open and run it directly in your web browser (Chrome, Firefox, Edge, Safari).

## 🕹️ Interactive Controls & Features

* **Publish Event / Produce Batch:** Send single messages or batches through the key hash partitioner and watch data route to partition leaders in real-time.

* **Auto Produce Mode:** Toggle automated streaming data generation to observe high-throughput log stacking and partition offset increments.

* **Add / Remove Consumer:** Simulate horizontal auto-scaling or service crashes to trigger instant consumer group **Rebalancing**.

* **Key Customization:** Test different message keys (e.g., `Order-101`, `Txn-881`) to verify how hashing consistently routes specific keys to the exact same partition leader.

---

## 🏗️ Architecture & Concepts Covered

This repository helps visualize core Kafka mechanics in action:

* **Producer Partitioner Logic:**
  $$\text{Partition Index} = \text{hash}(\text{Key}) \pmod{\text{Total Partitions}}$$

* **Consumer Group Load Balancing:** Strictly enforces the **1 Partition -> 1 Consumer** mapping rule within a single `group.id`.

* **Offset State Management:** Simulates bookmark tracking stored in Kafka's internal `__consumer_offsets` topic.

* **High Availability & Failover:** Shows Leader vs. Follower replica states across multi-broker clusters.

---

## 📂 Repository Structure

```text
.
├── consumer_group_simulator.html    # Interactive simulator for Consumer Group & Rebalance logic
├── kafka_simulator.html             # 3-Broker basic architecture simulator
├── kafka_6broker_simulator.html     # 6-Broker High Availability & replication simulator
└── README.md                        # Project documentation

🤝 Contributing
Contributions, issues, and feature requests are welcome! If you'd like to add new visualization scenarios (such as KRaft quorum consensus or partition reassignment), feel free to open a Pull Request or Issue.

📄 License
This project is open-source
# VPN Mesh

## Performance & Scalability Analysis

This document provides a comprehensive analysis of mesh-capable VPN systems, focusing on **performance**, **scalability**, and **redundancy**. The objective is to determine the most suitable solution for environments where high performance and resilience are critical, particularly in large-scale deployments with increasing node counts.

---

## **1. Context and Requirements**

The ideal VPN system must:

1. **Mesh Capability**: Ensure continuous connectivity among all nodes, even if one or more nodes fail.
2. **Performance**: Maintain high throughput and low latency in typical scenarios.
3. **Scalability**: Efficiently handle an increasing number of nodes without significant degradation in performance.
4. **Redundancy**: Eliminate single points of failure by distributing critical components across nodes.

---

## **2. Evaluated Solutions**

The following mesh VPN systems were considered:

### **a. Netmaker**

- **Technology**: Built atop **WireGuard**.
- **Mesh Features**: Supports peer-to-peer connections between nodes; established connections persist even if the central controller fails.
- **Performance**: Leverages WireGuard's kernel-based implementation, achieving high throughput with low latency.
- **Scalability**: Designed to handle large-scale deployments efficiently.
- **Redundancy**: Controllers can be deployed redundantly to prevent single points of failure.
- **Ideal Use Case**: Scenarios demanding high network speed and static node setups.

### **b. Nebula**

- **Technology**: A lightweight, decentralized mesh VPN with dynamic routing.
- **Mesh Features**: Fully decentralized; nodes operate without a central server, with multiple "Lighthouses" providing redundancy.
- **Performance**: Operates in userspace with AES-256-GCM encryption, which may introduce higher CPU usage compared to kernel-based solutions.
- **Scalability**: Capable of connecting tens of thousands of nodes seamlessly.
- **Redundancy**: Decentralized architecture ensures resilience even if multiple nodes fail.
- **Ideal Use Case**: Environments requiring robust decentralization and flexibility, such as dynamic or mobile nodes.

---

## **3. Performance and Scalability Analysis**

### **Performance Benchmarks**

| Solution     | Throughput (Mbit/s)  |
|--------------|----------------------|
| **Netmaker** | ~850                 |
| **WireGuard** (direct) | ~750       |
| **Nebula**   | ~400-500             |
| **Tailscale**| ~300                 |
| **ZeroTier** | ~550                 |

- **Netmaker** demonstrates superior point-to-point performance, achieving higher throughput than Nebula.
- **Nebula** provides moderate speeds, which may be sufficient for many use cases.

### **Scalability Considerations**

- **Netmaker**:
  - Designed for scalable deployments but relies on a centralized controller for management, even when deployed redundantly.
  - Performance may degrade as the number of nodes increases significantly due to the overhead introduced by maintaining a central coordination system.

- **Nebula**:
  - Designed to connect tens of thousands of nodes seamlessly, indicating strong scalability.
  - Fully decentralized architecture eliminates the need for a central controller, reducing potential bottlenecks as the network grows.
  - Efficient routing algorithms ensure that performance remains consistent even as the network scales to thousands of nodes.

---

## **4. Decision Framework**

Based on the research, the decision must weigh **performance** against **scalability** and **flexibility**:

1. **Netmaker** offers superior point-to-point throughput and is ideal for scenarios where the number of nodes is relatively small to medium, and high-speed connections between a fixed number of peers are required.
2. **Nebula** provides unparalleled scalability and decentralization, making it the better choice for networks that need to accommodate unpredictable growth, high dynamism, and minimal reliance on central management.

---

## **5. Conclusion**

While **Netmaker** delivers exceptional performance in smaller, more static setups, **Nebula**'s decentralized architecture and superior scalability make it the preferred choice for large-scale and dynamic environments. Nebula’s ability to handle tens of thousands of nodes without degrading performance ensures its suitability for future-proofing large, distributed systems.

This analysis concludes that **Nebula** is the optimal solution for highly scalable and decentralized mesh VPN networks, where long-term growth and resilience outweigh single-node performance advantages.

---

## **Further Reading**

- [Nebula GitHub Repository](https://github.com/slackhq/nebula)
- [Netmaker Official Documentation](https://www.netmaker.io/)
- [iPerf3 Benchmark Comparison](https://techoverflow.net/2022/08/19/iperf-benchmark-of-zerotier-vs-netmaker-vs-tailscale-vs-direct-switched-connection/)
- [Nebula Scalability Analysis](https://arstechnica.com/gadgets/2019/12/nebula-vpn-routes-between-hosts-privately-flexibly-and-efficiently/)

---

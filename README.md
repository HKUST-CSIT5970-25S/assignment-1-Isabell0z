[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/IAASVEAZ)
# CSIT5970 Assignment-1: EC2 Measurement (2 questions, 4 marks)

### Deadline: 11:59PM, Feb, 28, Friday

---

### Name: ZHOU, Chuqiao
### Student Id: 21079274
### Email: czhoubi@connect.ust.hk

---

## Question 1: Measure the EC2 CPU and Memory performance

1. (1 mark) Report the name of measurement tool used in your measurements (you are free to choose *any* open source measurement software as long as it can measure CPU and memory performance). Please describe your configuration of the measurement tool, and explain why you set such a value for each parameter. Explain what the values obtained from measurement results represent (e.g., the value of your measurement result can be the execution time for a scientific computing task, a score given by the measurement tools or something else).

    > Phoronix Test Suite
    >
    > Memory performance test configuration:  
        > Type: Test All Options (Average of Copy, Scale, Add, Triad )  
        > Benchmark: Test All Options (Both Integer and Floating Point)

2. (1 mark) Run your measurement tool on general purpose `t2.micro`, `t2.medium`, and `c5d.large` Linux instances, respectively, and find the performance differences among these instances. Launch all the instances in the **US East (N. Virginia)** region. Does the performance of EC2 instances increase commensurate with the increase of the number of vCPUs and memory resource?

    In order to answer this question, you need to complete the following table by filling out blanks with the measurement results corresponding to each instance type.

    | Size        | CPU performance | Memory performance |
    | ----------- | --------------- | ------------------ |
    | `t2.micro` |       3103 MIPS          |     Integer: 10613.35 MB/s, Floating Point: 10578.31 MB/s              |
    | `t2.medium`  |     3914 MIPS          |     Integer: 12394.32 MB/s, Floating Point: 12137.38 MB/s              |
    | `c5d.large` |      4276 MIPS          |     Integer: 13239.71 MB/s, Floating Point: 13038.39 MB/s              |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI.

    > The performance of CPU and memory increases commensurate with the increase of the number of vCPUs and memory resource

## Question 2: Measure the EC2 Network performance

1. (1 mark) The metrics of network performance include **TCP bandwidth** and **round-trip time (RTT)**. Within the same region, what network performance is experienced between instances of the same type and different types? In order to answer this question, you need to complete the following table.

    | Type                      |      TCP b/w (Mbps)     |     RTT (ms)     |
    | ------------------------- | ----------------------- | ---------------- |
    | `t3.medium` - `t3.medium` |       3430 Mbps         |     0.266 ms     |
    | `m5.large` - `m5.large`   |       4950 Mbps         |     0.172 ms     |
    | `c5n.large` - `c5n.large` |       4960 Mbps         |     0.162 ms     |
    | `t3.medium` - `c5n.large` |       2390 Mbps         |     0.695 ms     |
    | `m5.large` - `c5n.large`  |       2980 Mbps         |     0.620 ms     |
    | `m5.large` - `t3.medium`  |       4500 Mbps         |     0.143 ms     |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. Note: Use private IP address when using iPerf within the same region. You'll need iPerf for measuring TCP bandwidth and Ping for measuring Round-Trip time.

    > The network performance of instances of the same type is better than that of instances of different types.

2. (1 mark) What about the network performance for instances deployed in different regions? In order to answer this question, you need to complete the following table.

    | Connection                | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | N. Virginia - Oregon      |      31.3 Mbps          |    60.0 ms       |
    | N. Virginia - N. Virginia |      4840 Mbps          |    0.208 ms      |
    | Oregon - Oregon           |      4960 Mbps          |    0.158 ms      |
 
    > Region: US East (N. Virginia), US West (Oregon). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. All instances are `c5.large`. Note: Use public IP address when using iPerf within the same region.

    > The network performance of instances deployed in the same region is much better than that of instances deployed in different regions.

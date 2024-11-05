# IITG2406-01T1_JobScheduler (Project 3)

**Dev:** Aman [iitgcs_24061213]

## Overview
IITG2406-01T1_JobScheduler is a distributed job scheduling simulator designed to evaluate multiple scheduling policies across a simulated cluster of worker nodes. This system models real-world scheduling scenarios by managing CPU and memory allocation, allowing for performance analysis with various queueing and resource allocation strategies.

## System Architecture

### Infrastructure
- **128 Worker Nodes**
- **24 CPU Cores per Node**
- **64 GB RAM per Node**
- **Distributed Resource Management**

### Core Components

#### Job Class
The `Job` class defines individual jobs with the following attributes and functionalities:
- **Attributes**:
  - `jobId`: Unique identifier
  - `arrivalTime` & `timeHour`: Temporal properties
  - `coresReq` & `memReq`: Resource requirements
  - `execTime`: Execution duration
  - `grossValue`: A calculated metric for resource utilization (`cores * memory * time`)
- **Functionality**:
  - Tracks resource requirements
  - Outputs formatted status details
  - Calculates runtime metrics

#### WorkerNode Class
Each `WorkerNode` represents an individual node with:
- **Resources**:
  - CPU cores (individually tracked)
  - Memory in GB (granular tracking)
  - Utilization status
- **Operations**:
  - Checks resource availability
  - Allocates and deallocates jobs
  - Manages resource status

#### MasterScheduler Class
The `MasterScheduler` manages the overall system by:
- **Components**:
  - Pool of worker nodes
  - Job queue management
  - System-wide performance metrics
- **Responsibilities**:
  - Implements scheduling policies
  - Allocates resources to jobs
  - Monitors and logs performance metrics

## Implementation Logic

### Scheduling Policies

#### Queue Management Policies
1. **First Come First Serve (FCFS)**:
   - Maintains the original job order
   - Acts as a baseline performance metric
   
2. **Smallest Job First**:
   - Prioritizes jobs with the smallest resource usage (`cores * memory * execTime`)
   - Optimizes for resource efficiency

3. **Shortest Duration First**:
   - Prioritizes jobs with the shortest execution time
   - Reduces average wait time

#### Resource Allocation Strategies
1. **First Fit**:
   - Assigns jobs to the first available node
   - Advantages: Fast allocation, suitable for high-throughput

2. **Best Fit**:
   - Minimizes resource fragmentation by allocating jobs to nodes with the smallest sufficient resource block
   - Optimizes both CPU and memory utilization

3. **Worst Fit**:
   - Allocates jobs to nodes with the maximum available resources
   - Aims for load balancing and future job flexibility

### Operational Flow

#### Input Processing
- Reads jobs from a file (`JobArrival.txt`)
- Parses and validates each job entry
- Populates the job queue

#### Execution Cycle
1. Select scheduling policies
2. Order jobs in the queue based on policy
3. Allocate resources as per policy
4. Collect and log performance metrics

#### Performance Monitoring
Metrics tracked include:
- CPU utilization
- Memory usage
- Job completion rate
- Overall resource efficiency

#### Output Generation
1. **Real-time Console Updates**:
   - Displays daily performance metrics
   - Showcases policy effectiveness and resource utilization

2. **CSV Data Export**:
   - Records detailed metrics for policy comparisons
   - Allows time-series analysis of resource utilization

## Analysis Capabilities

### Performance Evaluation
- Compares policy effectiveness
- Analyzes resource utilization trends
- Identifies system bottlenecks
- Assesses scalability

### Optimization Opportunities
- Evaluates the efficiency of policy combinations
- Improves resource allocation strategies
- Enhances queue management practices
- Assists in capacity planning

## Usage Guidelines

1. **Input Preparation**
   - Format job specifications in `JobArrival.txt`
   - Ensure job resource requirements are within system limits

2. **Execution**
   - Run the simulator and specify simulation duration
   - Monitor real-time metrics and analyze policy effects

3. **Analysis**
   - Review CSV output files
   - Compare the performance of different policies
   - Identify optimal configurations and system efficiencies

## Requirements
- **C++ Standard Library**
- **GCC or equivalent C++ compiler**
- **CSV viewer** (optional, for analysis)

This project provides a robust foundation for evaluating job scheduling policies in distributed environments, aiding in optimizing resource management and improving overall system performance.

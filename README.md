# EXPERIMENT NO. 5 – PROMPT CHAINING

## Aim

To implement an engineering solution using a **series of dependent prompts**, where the result obtained from one prompt is used to guide the next stage of development, and to understand how Prompt Chaining supports systematic problem solving.

## Objective

To develop an **AI-Based Smart Traffic Signal Control System** by breaking the complete engineering task into smaller stages such as problem analysis, requirement identification, architecture design, algorithm development, implementation, testing, and documentation.

---

# Engineering Problem

## AI-Based Smart Traffic Signal Control System

Increasing vehicle density in urban areas causes traffic congestion, particularly during peak hours. Conventional traffic signals generally operate using predefined timings and may not respond effectively when traffic conditions change.

An **AI-Based Smart Traffic Signal Control System** can analyze the number of vehicles approaching different roads and adjust signal durations according to the current traffic condition.

The main purpose of the proposed system is to provide more green time to roads experiencing heavier traffic while maintaining appropriate signal timing for roads with lower traffic.
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/2226aa3f-1578-4f74-b975-e220dad419e8" />


---

# Prompt Chain

```text
        Engineering Problem
                ↓
        Problem Analysis
                ↓
      Requirement Identification
                ↓
         System Architecture
                ↓
        Control Algorithm
                ↓
          Flowchart Design
                ↓
        Python Simulation
                ↓
        Test Case Execution
                ↓
        Result Analysis
                ↓
          Documentation
```

The output of each stage is considered while preparing the prompt for the following stage. This creates a connected sequence of prompts instead of solving the entire problem using one prompt.

---

# 1. Problem Analysis

### Prompt

> Analyze the problem of traffic congestion in an urban area and design an AI-based traffic signal solution. Identify the existing problem, proposed solution, required inputs, system processing, outputs, and major advantages.

### Output

### Existing Problem

Urban traffic congestion increases when large numbers of vehicles arrive at an intersection at the same time. Fixed signal timings may not efficiently distribute green time according to the actual traffic condition.

### Proposed Solution

An AI-based traffic signal controller can collect vehicle information from different roads and use the traffic density to determine suitable signal timings.

### Input Data

* Vehicle count
* Traffic density
* Current signal status
* Waiting vehicles
* Traffic flow

### Processing

The system collects traffic information, compares the traffic levels of different roads, determines the most congested road, and assigns an appropriate green-light duration.

### Output

* Traffic density status
* Selected road priority
* Green-light duration
* Updated traffic signal timing

### Expected Benefits

* Reduction in unnecessary waiting
* Better utilization of road capacity
* Improved traffic movement
* Reduced fuel wastage
* Adaptive signal control

---

# 2. Requirement Identification

### Prompt

> Using the traffic management problem identified above, specify the functional requirements, non-functional requirements, hardware and software requirements, inputs, outputs, and important system constraints.

### Output

## Functional Requirements

1. Collect traffic information from each road.
2. Determine the number of vehicles.
3. Calculate the traffic level.
4. Compare traffic conditions between roads.
5. Select the road requiring higher priority.
6. Assign an appropriate green-light duration.
7. Update the signal timing.
8. Repeat the monitoring process continuously.

## Non-Functional Requirements

* Real-time response
* Reliability
* Scalability
* Maintainability
* Fast processing
* Accurate traffic measurement

## Hardware Requirements

* Traffic camera or vehicle sensor
* Processing unit
* Traffic signal controller
* Signal LEDs
* Communication device

## Software Requirements

* Python
* OpenCV or sensor-processing software
* Machine learning libraries
* Database
* Operating system

## Inputs and Outputs

| Input            | Processing           | Output           |
| ---------------- | -------------------- | ---------------- |
| Vehicle count    | Traffic analysis     | Green duration   |
| Waiting vehicles | Priority calculation | Road priority    |
| Traffic density  | Density comparison   | Congestion level |
| Traffic flow     | Signal optimization  | Updated signal   |

---

# 3. System Architecture

### Prompt

> Based on the requirements identified above, design a simple architecture for the smart traffic signal system. Show the sequence from traffic monitoring to signal control.

### Output

```text
             TRAFFIC MONITORING
                    ↓
          CAMERA / VEHICLE SENSOR
                    ↓
             DATA COLLECTION
                    ↓
          VEHICLE COUNTING UNIT
                    ↓
          TRAFFIC DENSITY ANALYSIS
                    ↓
            AI DECISION MODULE
                    ↓
          PRIORITY DETERMINATION
                    ↓
          SIGNAL TIMING CONTROLLER
                    ↓
             TRAFFIC SIGNALS
                    ↓
          CONTINUOUS MONITORING
                    ↺
```

### Explanation

The system begins by collecting traffic information through cameras or sensors. The collected information is processed to determine the number of vehicles on each road. The AI decision module analyzes the traffic density and determines which road should receive priority. The signal controller then changes the green-light duration accordingly.

The process continuously repeats as new traffic information becomes available.

---

# 4. Control Algorithm

### Prompt

> Using the architecture and requirements obtained in the previous stages, develop an algorithm for selecting traffic signal duration according to vehicle density on four roads.

### Output

## Algorithm

1. Start the traffic control system.
2. Identify the roads connected to the intersection.
3. Obtain the vehicle count for each road.
4. Store the vehicle counts.
5. Determine the road having the highest vehicle count.
6. Compare each road's vehicle count with predefined traffic levels.
7. Assign the highest green duration to the road with maximum traffic.
8. Assign medium duration to roads with moderate traffic.
9. Assign minimum duration to roads with low traffic.
10. Activate the corresponding traffic signal.
11. Collect new traffic information.
12. Repeat the process continuously.

---

# 5. Flowchart

### Prompt

> Convert the traffic signal control algorithm into a simple flowchart showing vehicle-count collection, traffic comparison, signal-time selection, and repeated monitoring.

### Output

```text
                 START
                   ↓
          Read Vehicle Counts
                   ↓
       Compare Traffic Levels
                   ↓
        Find Highest Traffic
                   ↓
       ┌─────────────────────┐
       │ Is traffic very high?│
       └─────────────────────┘
             ↓ YES     ↓ NO
             ↓         ↓
      Longer Green    Check
         Duration     Traffic Level
             ↓         ↓
             └────┬────┘
                  ↓
          Set Signal Timing
                  ↓
          Activate Signal
                  ↓
       Collect New Traffic Data
                  ↓
               REPEAT
```

---

# 6. Python Simulation

### Prompt

> Using the algorithm developed above, write a Python program that accepts vehicle counts for four roads and dynamically assigns signal durations. Use three traffic levels: low, medium, and high. The road with the highest vehicle count should receive the maximum green time.

### Output

```python
roads = ["Road A", "Road B", "Road C", "Road D"]

traffic = {}

for road in roads:
    vehicles = int(input("Enter vehicle count for " + road + ": "))
    traffic[road] = vehicles

highest_road = max(traffic, key=traffic.get)

print("\n--- SMART SIGNAL TIMING ---")

for road, vehicles in traffic.items():

    if road == highest_road:
        signal_time = 60
        level = "Highest"
    elif vehicles >= 40:
        signal_time = 45
        level = "Medium"
    else:
        signal_time = 30
        level = "Low"

    print(road, ":", vehicles, "vehicles |",
          level, "traffic |", signal_time, "seconds")
```

---

## Sample Input

```text
Enter vehicle count for Road A: 18
Enter vehicle count for Road B: 55
Enter vehicle count for Road C: 42
Enter vehicle count for Road D: 25
```

## Sample Output

```text
--- SMART SIGNAL TIMING ---

Road A : 18 vehicles | Low traffic | 30 seconds
Road B : 55 vehicles | Highest traffic | 60 seconds
Road C : 42 vehicles | Medium traffic | 45 seconds
Road D : 25 vehicles | Low traffic | 30 seconds
```

### Output Analysis

Road B has the highest vehicle count with **55 vehicles**, so it receives the maximum green duration of **60 seconds**.

Road C has a relatively higher traffic level and receives **45 seconds**.

Road A and Road D have lower vehicle counts and therefore receive **30 seconds**.

This demonstrates the basic concept of adaptive signal timing.

---

# 7. Testing

### Prompt

> Based on the Python implementation, create multiple test cases using different traffic conditions. Include vehicle counts, expected priority road, actual priority road, signal duration, and test status.

### Output

| Test Case | Vehicle Counts (A,B,C,D) | Expected Priority | Actual Priority | Green Time | Status |
| --------- | ------------------------ | ----------------- | --------------- | ---------- | ------ |
| TC01      | 10, 45, 20, 15           | Road B            | Road B          | 60 sec     | PASS   |
| TC02      | 65, 30, 25, 20           | Road A            | Road A          | 60 sec     | PASS   |
| TC03      | 15, 25, 70, 35           | Road C            | Road C          | 60 sec     | PASS   |
| TC04      | 20, 35, 40, 15           | Road C            | Road C          | 60 sec     | PASS   |
| TC05      | 30, 25, 20, 55           | Road D            | Road D          | 60 sec     | PASS   |

### Testing Observation

The system correctly identifies the road with the highest number of vehicles in the tested cases and assigns the highest green-light duration to that road.

---

# 8. Result Analysis

### Prompt

> Analyze the testing results obtained from the smart traffic signal simulation and explain whether the system correctly performs traffic-based signal prioritization.

### Output

The test cases show that the proposed system can identify the road with the highest vehicle count and assign it the highest green-light duration.

The simulation successfully demonstrates the basic principle of adaptive traffic signal control. When the traffic distribution changes, the priority road also changes according to the new vehicle counts.

However, the current implementation is a simplified simulation. A real-world system would require camera-based vehicle detection, real-time data processing, safety constraints, emergency vehicle handling, and integration with physical traffic signal controllers.

---

# 9. Documentation

### Prompt

> Using the outputs generated in the previous stages, prepare concise engineering documentation for the AI-Based Smart Traffic Signal Control System. Include the problem, solution, requirements, architecture, algorithm, implementation, testing, advantages, limitations, and conclusion.

### Output
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/764becfb-a629-429e-a900-e42cd8cf4fd2" />




## Conclusion

The Smart Traffic Signal Control System demonstrates how an engineering problem can be divided into smaller tasks and solved through Prompt Chaining.

---

# 10. Prompt Chaining Analysis

The experiment demonstrates that Prompt Chaining is useful because each stage builds upon information produced earlier.

| Chain Stage          | Output Produced            | Used By Next Stage   |
| -------------------- | -------------------------- | -------------------- |
| Problem Analysis     | Problem and solution       | Requirement analysis |
| Requirement Analysis | System requirements        | Architecture         |
| Architecture         | System components and flow | Algorithm            |
| Algorithm            | Step-by-step logic         | Flowchart and code   |
| Flowchart            | Visual process             | Implementation       |
| Python Code          | Working simulation         | Testing              |
| Testing              | Test results               | Result analysis      |
| Result Analysis      | System observations        | Documentation        |

Instead of asking ChatGPT to solve the complete engineering problem in one prompt, the problem is divided into smaller connected tasks.

This makes it easier to:

* Check each stage separately.
* Identify errors early.
* Improve individual stages.
* Maintain consistency between design and implementation.
* Produce organized documentation.

---

# Final Result

The **AI-Based Smart Traffic Signal Control System** was successfully designed using Prompt Chaining. The engineering problem was divided into a sequence of connected stages, beginning with problem analysis and continuing through requirements, architecture, algorithm design, flowchart creation, Python implementation, testing, result analysis, and documentation.

The experiment demonstrates that Prompt Chaining can help transform a complex engineering problem into a series of **smaller, connected, and manageable tasks**.

---

# Learning Outcome

After completing this experiment, students can:

1. Understand the concept and working principle of Prompt Chaining.
2. Divide an engineering problem into sequential tasks.
3. Design prompts whose outputs can support subsequent prompts.
4. Use AI assistance for system analysis and software development.
5. Convert requirements into algorithms and program logic.
6. Test an AI-assisted engineering solution using different inputs.
7. Analyze and document the final system.

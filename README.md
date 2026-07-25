# Hardware Side-Channel Attacks

An academic hardware-security project exploring cache-based side-channel attacks using Prime+Reload and Flush+Reload techniques.

The repository contains single-threaded and multi-threaded implementations, experimental attack variants, supporting code, and an independent study report.

## Project Overview

Modern processors use cache memory to improve performance. However, cache behavior can also reveal information about a program’s execution.

This project studies how timing differences in cache access can be used to infer memory-access patterns. It focuses on two cache side-channel techniques:

- Prime+Reload
- Flush+Reload

The project was completed as an academic independent study in hardware security and computer architecture.

## Objectives

- Study cache-based side-channel behavior
- Implement single-threaded attack experiments
- Implement multi-threaded attack experiments
- Compare different attack variants
- Analyze timing measurements
- Document experimental results and observations

## Techniques

### Prime+Reload

Prime+Reload observes changes in cache behavior by first loading selected memory locations into the cache and later measuring whether they remain cached.

The general experimental flow is:

1. Prime selected cache lines.
2. Allow the target workload to execute.
3. Reload the monitored memory locations.
4. Measure access latency.
5. Infer whether specific locations were accessed.

### Flush+Reload

Flush+Reload removes selected cache lines from the cache before measuring whether they are later reloaded.

The general experimental flow is:

1. Flush selected cache lines.
2. Allow the target workload to execute.
3. Reload the monitored memory locations.
4. Measure access latency.
5. Infer whether the target accessed the monitored locations.

> This repository is intended for academic study, defensive research, and controlled experimentation.

## Repository Structure

```text
hardware-side-channel-attacks/
├── Multi_thread_Mengjia_1/         # Multi-threaded experiment variant
├── Single_Thread/                   # Single-threaded implementation
├── Single_Thread_Attack_Working/    # Working single-threaded attack version
├── Stackoverflow Syntax/            # Supporting syntax and reference experiments
├── multi_thread/                    # Additional multi-threaded implementation
├── ECE 396 Independent Study Report.docx
└── README.md
```

## Experimental Variants

### Single-Threaded Implementation

The single-threaded version provides a controlled environment for testing cache timing behavior and validating the attack logic.

It is useful for:

- measuring cache-hit and cache-miss timing;
- validating threshold values;
- testing the reload mechanism;
- analyzing basic side-channel behavior.

### Multi-Threaded Implementation

The multi-threaded version extends the experiment to concurrent execution.

It is useful for studying:

- synchronization;
- timing variability;
- inter-thread interference;
- shared-cache behavior;
- reliability under concurrent workloads.

### Working Attack Version

The `Single_Thread_Attack_Working/` directory contains the working single-threaded implementation used to validate the attack workflow.

## Research Report

The file:

```text
ECE 396 Independent Study Report.docx
```

contains the full academic report for the project.

The report includes:

- project motivation;
- background on cache memory;
- side-channel attack methodology;
- implementation details;
- experimental observations;
- conclusions and future work.

Consider renaming it to:

```text
hardware-side-channel-attacks-report.docx
```

## Technologies and Concepts

- C or C++
- Multithreading
- Cache timing analysis
- CPU memory hierarchy
- Hardware security
- Computer architecture
- Side-channel analysis
- Performance measurement

Only keep the listed programming languages if they are actually used in the repository.

## Running the Project

The exact build and execution instructions depend on the implementation inside each directory.

A typical workflow is:

```bash
cd Single_Thread_Attack_Working
```

Compile the source files using the appropriate compiler:

```bash
gcc <source-files> -o side_channel_test
```

or:

```bash
g++ <source-files> -o side_channel_test
```

Run the compiled program:

```bash
./side_channel_test
```

For multi-threaded implementations, the build command may require thread support:

```bash
gcc <source-files> -pthread -o side_channel_test
```

Replace `<source-files>` with the actual source filenames in the selected directory.

## Experimental Results

The experiments evaluate cache-access timing and compare the observed latency between likely cache hits and cache misses.

Useful measurements include:

- average cache-hit latency;
- average cache-miss latency;
- timing threshold;
- detection accuracy;
- false-positive rate;
- false-negative rate;
- impact of multithreading;
- execution-time variability.

Add the actual measurements from the report here.

Example format:

| Experiment | Cache-hit latency | Cache-miss latency | Detection threshold |
|---|---:|---:|---:|
| Single-threaded | Add result | Add result | Add result |
| Multi-threaded | Add result | Add result | Add result |

## Project Scope

This project demonstrates experience with:

- hardware security;
- processor cache behavior;
- timing measurements;
- low-level systems programming;
- multithreading;
- experimental research;
- computer architecture;
- technical documentation.

## Limitations

- Results may vary across processor architectures.
- Cache behavior depends on hardware, operating system, and compiler optimization.
- Timing thresholds may require recalibration on different systems.
- Multithreading can introduce scheduling noise.
- The project is an academic prototype rather than a production security tool.

## Possible Improvements

- Add exact build instructions for every implementation
- Add a Makefile or CMake configuration
- Add processor and operating-system details
- Document experimental methodology
- Add timing-distribution graphs
- Add cache-hit and cache-miss benchmarks
- Add automated experiment scripts
- Standardize directory names
- Add reproducible test data
- Add a PDF version of the research report
- Add a license
- Add GitHub Actions for compilation checks

## Responsible Use

This repository is intended for:

- academic research;
- controlled security experimentation;
- defensive security education;
- understanding processor and cache behavior.

Do not use the techniques in this repository against systems without authorization.

## Project Status

This project was completed as an independent study in hardware security and cache-based side-channel analysis.

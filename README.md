# Regress CLI
A CLI tool that runs benchmarks on two versions of a binary/service and generates statistical comparisons
showing improvements or regressions.

## Key Features

### Usage:
```shell
regress --old ./v1.0/binary --new ./v2.0/binary --suite benchmarks.yaml
```

### Metrics to Measure
- Latency (p50, p95, p99)
- Throughput (requests/sec, transactions/sec)
- Resource usage (CPU, memory, disk I/O)
- Error rates
- Blockchain-specific: coming soon.

### Stack
- Criterion.rs for statistical benchmarking
- tokio for async runtime
- sysinfo for system metrics
- plotters for graphs
- Markdown/JSON/HTML output formats

### Architecture
```bash
src/
├── config.rs          // Parse benchmark suites
├── executor.rs        // Run old/new binaries
├── collectors/        // Metric collection
├── analyzer.rs        // Statistical comparison
├── reporters/         // Various output formats
└── main.rs
```

Key Implementation Details:
- Statistical rigor: multiple runs, outlier detection, confidence intervals
- Process isolation between runs
- Warmup period handling
- CI/CD integration with --fail-on-regression flag

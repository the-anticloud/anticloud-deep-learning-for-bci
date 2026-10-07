# Build and Test

**Project:** `DEEP_LEARNING_FOR_BCI`
**Upstream:** https://github.com/xiangzhang1015/Deep-Learning-for-BCI
**License:** MIT

## Quick Start

```bash
git clone https://github.com/xiangzhang1015/Deep-Learning-for-BCI
cd Deep-Learning-for-BCI
pip install -r requirements-anticloud.txt
python anticloud_main.py --offline --pax-local
```

## Anticloud Improvements Applied

1. PAX L5 Narrow L2 General 27B local neural signal decoding — air-gapped clinical device
2. AIOSS tamper-evident neural recording chain (FDA De Novo/510k audit-ready)
3. AES-256 encryption for all neural signal data (most sensitive PII category)
4. Single-binary BCI runtime deployable on embedded clinical hardware
5. Zero-cloud: all decoding, classification, and feedback run on-device
6. GPU/CPU equalizer: real-time decoding on embedded GPU, logging on CPU
7. Open BrainFlow/LSL integration replacing proprietary BCI SDK interfaces
8. Offline stimulation parameter optimizer replacing cloud neuromodulation APIs

## Benchmark Targets

| Metric | Target |
| --- | --- |
| Latency | Primary inference task: <5s on CPU, <1s on GPU |
| Throughput | Batch processing: >100 items/hour on single CPU server |
| Memory | <8GB RAM for standard deployment |
| Accuracy | Task-specific accuracy within 5% of cloud-API baseline |

## Build Status

Not yet measured. Run verified build and record actual figures above.

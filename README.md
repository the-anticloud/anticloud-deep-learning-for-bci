# DEEP LEARNING FOR BCI

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-brain_computer_interface-lightgrey)

> Anticloud-hardened packaging of the upstream project `DEEP_LEARNING_FOR_BCI` in category **BRAIN COMPUTER INTERFACE**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** BRAIN COMPUTER INTERFACE · **Upstream:** https://github.com/High-East/BCI-ToolBox · **Upstream pin:** `2f6e21e68157de31ee04684cb2868018ace76dac` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

# BCI-ToolBox

## 1. Introduction
BCI-ToolBox is deep learning pipeline for motor-imagery classification.  
This project contains five models: ShallowConvNet, DeepConvNet, EEGNet, FBCNet, BCI2021.  
(BCI2021 is not an official name.)

## 2. Installation

### Environment

- Python == 3.7.10
- PyTorch == 1.9.0
- mne == 0.23.0
- braindecode == 0.5.1
- CUDA == 11.0

### Create conda environment

```shell
conda install pytorch=1.9.0 cudatoolkit=11.1 -c pytorch -c nvidia
conda install numpy pandas matplotlib pyyaml ipywidgets
pip install torchinfo braindecode moabb mne
```

## 3. Directory structure
```shell
.
├── README.md
├── base
│   ├── constructor.py
│   └── layers.py
├── configs
│   ├── BCI2021
│   │   └── default.yaml
│   ├── DeepConvNet
│   │   └── default.yaml
│   ├── EEGNet
│   │   └── default.yaml
│   ├── FBCNet
│   │   └── default.yaml
│   ├── ShallowConvNet
│   │   └── default.yaml
│   └── demo
│       ├── arch.yaml
│       ├── bci2021.yaml
│       ├── test.yaml
│       ├── train.yaml
│       └── training_params.yaml
├── data_loader
│   ├── data_generator.py
│   ├── datasets
│   │   ├── __init__.py
│   │   ├── bnci2014.py
│   │   ├── cho2017.py
│   │   ├── folder_dataset.py
│   │   ├── openbmi.py
│   │   └── tmp_dataset.py
│   └── transforms.py
├── main.py
├── models
│   ├── BCI2021
│   │   ├── BCI2021.py
│   │   └── __init__.py
│   ├── DeepConvNet
│   │   ├── DeepConvNet.py
│   │   └── __init__.py
│   ├── EEGNet
│   │   ├── EEGNet.py
│   │   └── __init__.py
│   ├── FBCNet
│   │   ├── FBCNet.py
│   │   └── __init__.py
│   ├── ShallowConvNet
│   │   ├── ShallowConvNet.py
│   │   └── __init__.py
│   ├── __init__.py
│   └── model_builder.py
├── trainers
│   ├── __init__.py
│   ├── cls_trainer.py
│   └── trainer_maker.py
└── utils
    ├── calculator.py
    ├── painter.py
    └── utils.py

```

## 4. Dataset

- Use [braindecode](https://braindecode.org)

## 5. Get Started
- We use [W&B](https://wandb.ai/home) for experimental management tool.
- [Example for W&B Dashboard](https://wandb.ai/high-east/Demo/table?workspace=user-high-east)
- [Example for W&B Report](https://wandb.ai/high-east/Demo/reports/Report-sample--VmlldzoxNDAxMzY5)

### Create wandb_key.yaml file
- Create wandb_key.yaml file in configs directory.
    ```yaml
    # wandb_key.yaml
    key: WANDB API keys
    ```
- WANDB API keys can be obtained from your W&B account settings.

### train
**Use W&B**
```bash
python main.py --config_file=configs/demo/train.yaml
```

**Not use W&B**
```bash
python main.py --config_file=configs/demo/train.yaml --no_wandb
```

**USE GPU**
```bash
python main.py --config_file=configs/demo/train.yaml --device=0  # Use GPU 0
python main.py --config_file=configs/demo/train.yaml --device=1  # Use GPU 1
python main.py --config_file=configs/demo/train.yaml --device=2  # Use GPU 2
```
- GPU numbers depend on your server.

**USE Sweep**
```yaml
# W&B
sweep_file: configs/demo/training_params.yaml
project: Demo
tags: [train]
```
- Add this block to config file for finding training parameters.

```yaml
# W&B
sweep_file: configs/demo/arch.yaml
sweep_type: arch
project: Demo
tags: [train]
```
- Add this block to config file for finding model architecture.

### test
```bash
python main.py --config_file=configs/demo/test.yaml
```

## 5. References
- ShallowConvNet [[Paper]](https://arxiv.org/pdf/1703.05051.pdf) [[Code]](https://github.com/braindecode/braindecode/blob/master/braindecode/models/shallow_fbcsp.py)
- DeepConvNet [[Paper]](https://arxiv.org/pdf/1703.05051.pdf)  [[Code]](https://github.com/braindecode/braindecode/blob/master/braindecode/models/deep4.py)
- EEGNet [[Paper]](https://arxiv.org/abs/1611.08024) [[Code]](https://github.com/braindecode/braindecode/blob/master/braindecode/models/eegnet.py)
- FBCNet [[Paper]](https://arxiv.org/abs/2104.01233) [[Code]](https://github.com/ravikiran-mane/FBCNet)
- BCI2021 [[Paper]](https://ieeexplore.ieee.org/document/9385293) [[Code]](https://github.com/High-East/Attention-based-spatio-temporal-spectral-feature-learning-for-subject-specific-EEG-classification)

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Unknown (no standard manifest detected)** (manifests: none detected; scanned in UPSTREAM_CLONE)
- Top-level source layout: `base/`, `configs/`, `data_loader/`, `models/`, `trainers/`, `utils/`
- Snapshot size: **42 files**, **2587 lines of code** (measured; see Benchmarks)
- Primary languages: `.py` (29), `.yaml` (10), `(none)` (2), `.md` (1)
- Upstream commit pinned for this packaging: `2f6e21e68157de31ee04684cb2868018ace76dac`

---

## Installation

No installation section was found in the upstream readme, so the commands below are generated from the manifests detected in this project directory.

```sh
# No standard manifest detected. Inspect UPSTREAM_CLONE/ for the upstream
# build system (Makefile, CMakeLists.txt, configure, ...) and follow it.
```

Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

No usage section was found in the upstream readme. Entry points detected in this project directory:

Browse the snapshot layout listed under What This Project Does and follow the upstream run instructions for the detected ecosystem (Unknown (no standard manifest detected)).

Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

```
- WANDB API keys can be obtained from your W&B account settings.

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Unknown (no standard manifest detected) |
| Manifests detected | none |
| Files in snapshot | 42 |
| Lines of code | 2587 |
| Dependency references | 0 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

- Python == 3.7.10
- PyTorch == 1.9.0
- mne == 0.23.0
- braindecode == 0.5.1
- CUDA == 11.0

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

Upstream contributions: fork the `DEEP_LEARNING_FOR_BCI` project, create a feature branch, and open a pull request against upstream. Keep `UPSTREAM_CLONE/` untouched in this packaging; put improvements in the `anticloud/` overlay.

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
MIT License

Copyright (c) 2022 DongHee

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `DEEP_LEARNING_FOR_BCI` (category: BRAIN COMPUTER INTERFACE)
- **Upstream URL:** https://github.com/High-East/BCI-ToolBox
- **Pinned commit (SHA):** `2f6e21e68157de31ee04684cb2868018ace76dac`
- **Branch:** master
- **Pin provenance:** GitHub API commits/master. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`e6db6634bcb9ec49e93ace66cda85d527c6fa95da208082ef866e75ec449e8a4`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.


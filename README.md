# Optimizing LLM Code Suggestions: Feedback-Driven Timing with Lightweight State Bounds

This repository contains the artifacts accompanying the paper:

*Title:* **Optimizing LLM Code Suggestions: Feedback-Driven Timing with Lightweight State Bounds**

*Authors:* **Mohammad Nour Al Awad, Sergey Ivanov, Olga Tikhonova**

*Affiliation:* **ITMO University, Saint Petersburg, Russia**

## Repository Structure

- Jupyter notebook containing the data analysis, statistical tests, and visualization of the performance metrics across three experimental phases.
- JSON file containing the collected suggestion metrics data from the experiments.

## Data Description

The `suggestion_metrics_data.json` file contains a list of suggestion events collected during the experiments. Each entry includes:

- `timestamp`: ISO 8601 formatted timestamp of the suggestion event.
- `accepted`: Boolean or integer indicating whether the suggestion was accepted (1) or rejected (0).
- `decision_time_sec`: Time in seconds taken by the user to decide on the suggestion (null if not applicable).
- Other metadata fields related to the suggestion context.

The data is divided into three phases based on timestamps:
- **Phase 1**: Before 2025-03-03 (baseline period with no delay)
- **Phase 2**: 2025-03-03 to 2025-04-03 (static delays)
- **Phase 3**: After 2025-04-03 (adaptive delays)

## Key Results

The analysis reveals progressive improvements in suggestion timing optimization:

- **Blind Rejections** (decisions < 0.3 seconds): Reduced from 8.7% in Phase 1 to 0.4% in Phase 3 as a percentage of all rejections.
- **Acceptance Rates**: Increased from 4.9% in Phase 1 to 18.6% in Phase 3.
- **Statistical Significance**: Proportion tests confirm significant reductions in blind rejections between phases (p-values < 0.05).
- **Efficiency Gains**: Reduced the number of inference calls per accepted suggestion by 75%.


## Adaptive Delay Method Overview

The core of the system is a feedback-driven algorithm that adjusts suggestion delays based on:

1. **High-level State Anchoring**: Binary classification of developer cognitive state (implementing vs. debugging) using LLM-based inference on behavioral telemetry.
2. **Acceptance-Rate Based Adaptation**: Logistic transform of recent acceptance rates to modulate delay within bounded ranges.
3. **Smoothing**: Per-update delay adjustments to prevent abrupt changes.

## Citation

If you use this work, please cite:

```bibtex
@inproceedings{alawad2025optimizing,
  title={Optimizing LLM Code Suggestions: Feedback-Driven Timing with Lightweight State Bounds},
  author={Al Awad, Mohammad Nour and Ivanov, Sergey and Tikhonova, Olga},
  booktitle={Proceedings of the IEEE/ACM International Conference on Automated Software Engineering (ASE)},
  year={2025},
}
```

## License

This repository is provided for academic and research purposes. Please refer to the paper for usage rights and contact the authors for any questions.

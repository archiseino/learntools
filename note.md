# Recap of the `learntools` Repository

## Overview

The `learntools` repository contains the checking code and notebooks used in [Kaggle Learn](https://www.kaggle.com/learn) courses. The materials in this repository are designed to provide feedback to users in Kaggle Learn courses and are not intended for independent use.

## Repository Structure

The repository is divided into two main parts:

1. `learntools` package
2. `notebooks` subdirectory

### `learntools` Package

The `learntools` package provides the infrastructure for exercise checking and is further divided into the following submodules:

- `core`: Contains the basic elements of exercise checking, shared across all Learn micro-courses and exercises. It includes:
  - `problem.py`: Defines the `Problem` class and its subclasses for different types of problems.
  - `problem_view.py`: Provides an interface that wraps a `learntools.core.Problem`.
  - `utils.py`: Contains utility functions for binding exercises and other helper functions.
  - `ISSUES.md`: Lists issues and feature requests for `learntools.core`.
  - `README.md`: Provides guidance on implementing exercises using the `learntools.core` API.

- Course-specific submodules: Each course has its own submodule that subclasses `ProblemViews` from `learntools.core`. Examples include:
  - `python`: Used to check exercises in the Python course.
  - `machine_learning`: Used to check exercises in the Machine Learning course.
  - `deep_learning`: Used to check exercises in the Deep Learning course.
  - And many more...

### `notebooks` Subdirectory

The `notebooks` subdirectory contains tools to simplify publishing courses on Kaggle as well as the course materials themselves. The course materials are in notebooks, which are processed in a templating system before being uploaded to Kaggle.

The structure of the `notebooks` subdirectory is as follows:

- `raw/`: Contains the raw notebooks authored by course creators. These notebooks are recipes for generating publishable notebooks.
- `default/`: Contains the rendered notebooks and `kernel-metadata.json` files for syncing notebooks to Kaggle Kernels via the API.
- `track_meta.py`: Defines metadata about the notebooks to be synced.
- `default.yaml`: A config file specifying how to build raw notebooks into kernels.
- `README.md`: Explains the notebook pipeline and directory structure.
- `ISSUES.md`: Lists issues related to the notebook pipeline.

## Running Tests

To run all tests against the staging image:

```
./test.sh
```

To run all tests against a specific image:

```
./test.sh -i gcr.io/kaggle-images/python:some-tag
```

To run only the tests for a specific track (e.g., `computer_vision`):

```
./test.sh -t computer_vision
```

To run only the tests for a specific exercise within a track (e.g., the 1st exercise of the `computer_vision` track):

```
./test.sh -t computer_vision -n ex1
```

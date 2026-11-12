# Easy Pantry Dataset

## Overview

The Easy Pantry dataset supports a computer vision object-detection
application that identifies common pantry items from user-supplied
photos.

The initial version of the project focuses on three object classes:

1. `pasta_box`
2. `snack_bag`
3. `soda_can`

The goal is to detect and locate individual pantry items so the
detections can later be converted into a simple inventory summary.

## Dataset Sources

The dataset will combine:

- Original photographs collected for the Easy Pantry project
- An external Roboflow dataset containing relevant pantry or grocery
  object images

### External Dataset

- **Dataset name:** TBD
- **Provider:** Roboflow
- **Dataset URL:** TBD
- **License:** TBD
- **Classes used:** TBD

The exact dataset name, URL, license, and classes used will be recorded
here before model training.

## Target Classes

### pasta_box

Rectangular boxes containing dry pasta products.

Examples may include:

- spaghetti boxes
- penne boxes
- macaroni boxes
- other boxed dry pasta

### snack_bag

Flexible packaged snack bags.

Examples may include:

- potato chip bags
- tortilla chip bags
- pretzel bags
- similar flexible snack packaging

### soda_can

Individual aluminum beverage cans.

Examples may include:

- standard soda cans
- diet soda cans
- zero-sugar soda cans
- different brands and package designs

## Data Collection Goals

The dataset should contain varied examples of each class.

Important sources of variation include:

- brand
- package color
- lighting
- camera angle
- object orientation
- distance from camera
- background
- clutter
- partial occlusion
- object scale

The initial goal is at least 30 labeled images for each target class.

## Annotation

The project uses object-detection annotations.

Each visible target object should receive:

- a bounding box
- one class label

Only the three defined Easy Pantry classes should be labeled during
the initial project scope.

## Annotation Rules

### General Rules

- Draw the bounding box as closely as practical around the visible object.
- Use the correct class name exactly as defined above.
- Do not create new class names for individual brands.
- Label multiple target objects separately when more than one appears.
- Review ambiguous examples before adding them to the final dataset.

Additional class-specific annotation rules will be documented as the
dataset is reviewed.

## Dataset Quality Checks

Before training, the dataset will be reviewed for:

- duplicate images
- corrupted images
- incorrect labels
- missing bounding boxes
- incorrect bounding boxes
- class imbalance
- inconsistent class names
- unrealistic or unusable images

## Dataset Split

The final labeled dataset will be separated into:

- training set
- validation set
- test set

The validation set will be used during model development.

The test set will remain separate from model tuning and will be used
for final evaluation.

## Repository Policy

Large image datasets and generated training outputs should not be
committed directly to this Git repository unless intentionally required.

Dataset files excluded by `.gitignore` should be documented here so
that another user can understand how to recreate the dataset.

## Status

- [ ] Exact Roboflow dataset identified
- [ ] Roboflow dataset URL recorded
- [ ] Dataset license recorded
- [ ] Class annotation rules finalized
- [ ] Minimum image target reached for `pasta_box`
- [ ] Minimum image target reached for `snack_bag`
- [ ] Minimum image target reached for `soda_can`
- [ ] Dataset quality audit completed
- [ ] Train/validation/test split created
- [ ] Final dataset configuration documented
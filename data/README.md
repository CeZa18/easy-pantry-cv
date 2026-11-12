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

---

## Negative Images

Negative images are photographs that contain no valid instances of
the three Easy Pantry target classes:

- `pasta_box`
- `snack_bag`
- `soda_can`

Negative images do not receive a separate class label.

### Annotation Rule

If an image contains none of the target classes:

- Keep the image in the dataset.
- Create no bounding boxes for the image.
- Do not create a `negative`, `background`, `other`, or `non_target`
  object class.
- Record the image as a negative example in the dataset manifest.

Expected annotation:

    Target objects: 0
    Bounding boxes: 0

### Negative Image Categories

For dataset documentation, negative images may be assigned a
metadata category. These categories are for analysis only and are
NOT YOLO object classes.

#### negative_general

A realistic pantry, cabinet, countertop, kitchen, or grocery scene
that contains none of the three target object classes.

Examples:

- canned vegetables
- jars
- cereal containers
- condiments
- household items
- empty pantry shelves

#### negative_hard_box

Contains box-shaped products that could be confused with
`pasta_box`, but are not pasta boxes.

Examples:

- cereal boxes
- cracker boxes
- granola-bar boxes
- tea boxes
- boxed rice
- boxed baking products

Correct annotation: no bounding boxes.

#### negative_hard_bag

Contains flexible packages that could be confused with
`snack_bag`, but do not satisfy the snack-bag definition.

Examples:

- rice bags
- bean bags
- flour bags
- sugar bags
- flexible pasta packages
- bread bags
- pet-food bags

Correct annotation: no bounding boxes.

#### negative_hard_can

Contains cylindrical packages that could be confused with
`soda_can`, but do not satisfy the soda-can definition.

Examples:

- canned vegetables
- canned soup
- canned beans
- energy-drink cans
- sparkling-water cans
- alcoholic-beverage cans
- other non-soda cans

Correct annotation: no bounding boxes.

### Mixed Images Are Not Negative Images

An image containing both target and non-target products is a
positive/mixed image, not a negative image.

Example:

A pantry photograph contains:

- one pasta box
- one cereal box
- two soup cans

Annotate only:

- the pasta box as `pasta_box`

Do not annotate:

- the cereal box
- the soup cans

### Quality-Control Rules

Before marking an image as negative:

- [ ] Inspect the entire image.
- [ ] Confirm that no valid `pasta_box` is visible.
- [ ] Confirm that no valid `snack_bag` is visible.
- [ ] Confirm that no valid `soda_can` is visible.
- [ ] Check partially occluded objects before declaring the image negative.
- [ ] Check objects near the image boundaries.
- [ ] Do not create boxes around non-target objects.
- [ ] Record the negative-image metadata category when applicable.

### Test-Set Use

Negative test images are used to evaluate false-positive behavior.

For a true negative image, the desired Easy Pantry result is:

    pasta_box: 0
    snack_bag: 0
    soda_can: 0

Any predicted target object on a true negative image should therefore
be reviewed as a potential false positive.

Hard-negative images are especially useful because they test whether
the detector has learned the intended class boundaries rather than
simple visual shortcuts such as:

    box -> pasta_box
    bag -> snack_bag
    can -> soda_can
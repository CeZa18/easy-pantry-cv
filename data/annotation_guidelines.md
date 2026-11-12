# Easy Pantry Annotation Guidelines

## Purpose

These guidelines define how images will be annotated for the Easy Pantry object-detection dataset. The goal is consistent, repeatable bounding-box labels for three target classes:

- `pasta_box`
- `snack_bag`
- `soda_can`

Easy Pantry is an object-detection project. Each visible target object is labeled separately so the model can learn both **what** the object is and **where** it appears in an image.

> **Project convention:** When an edge case is not covered below, do not guess. Flag the image for review and document the decision before adding a new rule.

---

## 1. General Annotation Rules

1. Label every clearly identifiable instance of a target class.
2. Use exactly one class label per object.
3. Use only the three approved class names. Do not create brand-specific classes.
4. Draw one bounding box around each distinct object, even when several objects of the same class appear in one image.
5. Draw the box around the visible physical object, not its shadow, reflection, shelf label, or surrounding background.
6. Keep boxes reasonably tight while including all visible parts that belong to the object.
7. Do not intentionally include neighboring products in the box when they can be excluded.
8. If an object cannot be identified confidently as one of the three classes, do not force a label. Mark the image for review.
9. Do not label pictures of products printed on packaging, posters, screens, or advertisements as real pantry objects.
10. Apply the same rules to original photographs and externally sourced images.

---

## 2. Target Classes

### `pasta_box`

**Definition:** A rigid retail carton whose primary product is dry pasta.

#### Include

- Rectangular cardboard cartons containing dry pasta.
- Boxes containing spaghetti, penne, macaroni, lasagna, or other dry pasta shapes.
- Boxes from different brands, colors, and package designs.
- Upright, sideways, tilted, or horizontally positioned boxes.
- Open boxes when the package is still clearly identifiable as a pasta box.
- Partially occluded pasta boxes when enough of the package is visible to identify the class confidently.

#### Exclude

- Pasta sold only in flexible plastic bags or pouches.
- Canned pasta or prepared pasta meals.
- Bowls, plates, or containers of cooked pasta.
- Cardboard boxes that contain non-pasta foods.
- Loose pasta without its retail box.
- A printed photograph of a pasta box on another surface.

#### Borderline examples

- **Box with a clear plastic window:** label as `pasta_box` if the overall container is a rigid retail carton.
- **Multipack/carton containing several individual pasta boxes:** label the visible individual pasta boxes when they can be distinguished. Do not add one extra box for the outer shipping/display carton unless the outer carton itself is the retail pasta package being treated as the object.
- **Severely damaged box:** label only when its identity as a pasta box remains clear.

---

### `snack_bag`

**Definition:** A flexible retail bag or pouch whose primary contents are ready-to-eat snack food.

#### Include

- Potato-chip bags.
- Tortilla-chip bags.
- Pretzel bags.
- Popcorn bags sold as ready-to-eat snacks.
- Cheese-puff or similar extruded-snack bags.
- Flexible snack packages of different brands, sizes, and colors.
- Open or partially collapsed snack bags when they remain identifiable.
- Partially occluded snack bags when enough of the package is visible to identify the class confidently.

#### Exclude

- Rigid snack boxes or tubs.
- Grocery bags, storage bags, trash bags, or reusable bags.
- Flexible bags containing dry pasta, rice, beans, flour, sugar, bread, pet food, or other non-snack products.
- Candy wrappers or very small single-item wrappers unless the project scope is later explicitly expanded.
- A printed photograph of a snack bag.

#### Borderline examples

- **Standing resealable snack pouch:** label as `snack_bag` when it is a flexible package containing a ready-to-eat snack.
- **Bag inside a multipack carton:** label the individual bag only when it is visibly distinct and identifiable.
- **Heavily crumpled bag:** label when the object is still clearly identifiable as a target snack bag.

---

### `soda_can`

**Definition:** An individual rigid beverage can containing, or intended to contain, carbonated soft drink/soda.

#### Include

- Standard soda cans of different brands and flavors.
- Regular, diet, zero-sugar, and caffeine-free soda cans.
- Standard-size, slim, mini, or tall soda cans when they are clearly soda products.
- Opened cans.
- Dented cans when they remain identifiable.
- Upright, sideways, tilted, or partially occluded cans when their class remains clear.

#### Exclude

- Bottles of soda.
- Energy-drink cans.
- Beer, hard seltzer, or other alcoholic-beverage cans.
- Canned food.
- Sparkling-water cans unless the project scope is explicitly expanded to include them.
- Empty unlabeled metal cans that cannot confidently be identified as soda cans.
- A printed image of a soda can.

#### Borderline examples

- **Brand or flavor unfamiliar to the annotator:** label only if packaging makes it reasonably clear that it is soda/soft drink.
- **Can with most branding hidden:** label only if remaining visual evidence is sufficient to distinguish it from excluded beverage cans.
- **Crushed can:** label if it remains visually identifiable as a soda can; otherwise flag for review.

---

## 3. Bounding-Box Rules

### Box placement

- Draw the smallest practical rectangle that contains the visible target object.
- Include the visible edges of the object.
- Exclude unnecessary background.
- Do not expand the box to make all boxes a similar size.
- Do not use a single box around a group of objects when the individual objects can be distinguished.

### Multiple objects

If an image contains five visible soda cans, create five `soda_can` annotations. If a snack bag overlaps a pasta box, annotate each object separately.

### Touching objects

When two objects touch, draw a separate box for each object based on its own visible extent. Overlapping annotation boxes are acceptable when the physical objects overlap in the image.

---

## 4. Occlusion Rules

An object is **occluded** when another object blocks part of it.

- Label partially occluded objects when the class can still be identified confidently.
- Draw the box around the object's **visible extent** for this project. Do not guess the position of hidden edges.
- If only a tiny or ambiguous fragment is visible and the class cannot be identified confidently, do not label it.
- If repeated uncertainty occurs around a particular occlusion pattern, flag examples and update this document with a consistent rule.

---

## 5. Image-Edge and Cropping Rules

- Label a target object that extends beyond the image boundary if the visible portion is sufficient for confident identification.
- Bound the annotation to the visible portion inside the image.
- Do not estimate or extend the bounding box beyond the image.
- If the crop leaves only an ambiguous fragment, do not label it.

---

## 6. Small, Blurry, and Difficult Objects

Label an object only when a human reviewer can confidently determine its target class at the available image resolution.

Flag for review when:

- the object is extremely small;
- motion blur or focus prevents reliable identification;
- glare hides most distinguishing packaging;
- heavy occlusion makes the class uncertain;
- the packaging could plausibly belong to a target class or an excluded class.

Do not use brand knowledge or context alone to force a label when the visible evidence is insufficient.

---

## 7. Orientation and Package Condition

Orientation does not change the class. Valid examples may be:

- upright;
- horizontal;
- tilted;
- upside down;
- viewed from the side;
- partially facing away from the camera.

Opened, dented, crushed, or partially collapsed packaging remains eligible when it is still clearly identifiable and follows the class definitions above.

---

## 8. Background and Context

The dataset should allow realistic pantry variation. Target objects may appear:

- on pantry shelves;
- on kitchen counters;
- in cabinets;
- on tables;
- among other groceries;
- alone or in cluttered scenes.

The background does not determine the class. A soda can on a desk is still a `soda_can`; a pasta box outside the pantry is still a `pasta_box`.

---

## 9. Ambiguous Cases and Review Process

When uncertain:

1. Do not invent a new class.
2. Do not choose the closest class merely to avoid leaving the object unlabeled.
3. Flag the image for review.
4. Record the reason for uncertainty.
5. Decide the case consistently.
6. If the decision represents a reusable pattern, update these guidelines before continuing annotation.

Suggested review notation:

```text
image_filename | candidate class | issue | final decision | guideline updated? yes/no
```

---

## 10. Negative Examples

Images may contain objects that resemble target classes but are intentionally not labeled. Examples include:

- cereal boxes near pasta boxes;
- rice or flour bags near snack bags;
- sparkling-water or energy-drink cans near soda cans;
- soda bottles near soda cans.

These examples can help ensure that the dataset reflects the actual class boundaries, provided target objects are still annotated correctly when present.

---

## 11. Quality-Control Checklist

Before accepting an annotated image, confirm:

- [ ] Every clearly visible target object is labeled.
- [ ] Every object has exactly one class label.
- [ ] Class names use the exact approved spelling.
- [ ] No brand-specific or unapproved classes were created.
- [ ] Each bounding box is reasonably tight around the visible object.
- [ ] Boxes do not unnecessarily include neighboring products or background.
- [ ] Multiple instances are annotated separately.
- [ ] Occluded and cropped objects follow the rules above.
- [ ] Non-target objects are not labeled.
- [ ] Printed/displayed images of products are not labeled as physical products.
- [ ] Uncertain cases are flagged rather than guessed.

---

## 12. Dataset-Split Guardrail

Annotation rules must remain the same across training, validation, and test data. Dataset splitting will occur only after quality review. The validation set will be used during development, while the test set will remain held out for final evaluation.

---

## 13. Version History

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-09-29 | Initial Easy Pantry annotation guidelines drafted for `pasta_box`, `snack_bag`, and `soda_can`. |

---

## Sources and Rationale

Easy Pantry uses object detection because the project needs to identify and locate individual pantry items. Course Module 06 distinguishes detection from classification by defining detection output as a bounding box and label for each object. The project's emphasis on consistent labels, data cleaning, and separate training/validation/test data also follows the ML lifecycle described in Module 03. The class definitions and edge-case decisions above are project-specific conventions and should be applied consistently once annotation begins.

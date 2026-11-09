# Easy Pantry

**Problem:**

 People forget what food they already have, which can result in duplicate purchases or unused pantry items.

**Goal:**

 Take a phone photograph of a pantry and turn detected pantry items into a simple inventory report.

**Initial target classes:**

- pasta_box
- snack_bag
- soda_can

**Baseline model:**

 Pretrained YOLO11 object detector.

**Custom model:**
 
 Fine-tuned YOLO11 detector trained on the Easy Pantry dataset.

**Current limitation:**
 
 The pretrained detector is being used initially to establish a working detection pipeline. It does not have preexisting training on the proposed custom classes required for the Easy Pantry labels. Fine-tuning is what will teach the detector the project-specific classes.

**Target:**
 
 The target is to investigate how to reach a 0.85 confidence score, and if possible implement a working product as an MVP.
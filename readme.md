# Dataset Release Page (Planned): Microgravity Human Motion and Contact Trajectories

Repository: `https://github.com/oaioyu/Dataset`

This repository hosts the **documentation and release plan** for a processed microgravity motion/contact dataset used in robot-astronaut motion learning research.

## Current Status

**Current status:** Documentation-only (README first).
**Planned release:** Processed trajectory files in `.npz` format.

A public download link will be added here after the release package and documentation are finalized.

---

## Planned Release Contents

We plan to release a processed trajectory dataset in **`.npz` format**, including:

### 1) SMPL kinematic parameters

* `poses` (SMPL pose parameters, axis-angle)
* `trans` or `transl` (metric root/global translation)
* `betas` (SMPL shape parameters, if included in the release)

### 2) Contact annotations

* `contact`: vertex-level binary contact labels
* `obj`: vertex-level semantic contact category labels

### 3) Metadata (release-dependent)

* e.g., `gender`
* additional sequence metadata (if included)

This release is intended to support reproducible research in:

* imitation learning
* contact-aware motion modeling
* robot astronaut mobility/control in microgravity environments

---

## Data Format (Planned)

The processed files are designed to be **AMASS-compatible / AMASS-style** where applicable.

### Core fields (example specification)

* **`poses`**: shape `(T, 72)`, `float32`
  SMPL pose parameters in axis-angle representation (radians).

* **`trans`** (or **`transl`**): shape `(T, 3)`, `float32`
  Metric root translation sequence (meters).

* **`betas`**: shape `(10,)`, `float32`
  SMPL shape parameters (if included in the public package).

* **`contact`**: shape `(T, 6890)`, `uint8` / `bool`
  Binary vertex-level contact labels (`1` = contact, `0` = no contact).

* **`obj`**: shape `(T, 6890)`, integer type
  Vertex-level semantic contact category labels.
  `0` indicates **no contact**; positive IDs indicate predefined environment-contact categories.

* **`gender`**: string or scalar metadata
  SMPL model-loading metadata (release-dependent).

> **Note:** Final field names and exact dtypes will be confirmed in the public release documentation.
> In particular, the translation key may be `trans` or `transl` depending on the finalized package.

---

## Semantic Contact Taxonomy (Planned)

`obj[t, v]` stores the semantic contact category ID for SMPL vertex `v` at frame `t`.

* **`0`**: `no_contact`
* **`1 ... K`**: predefined environment-contact categories

Planned example categories (subject to final release specification):

* `handrail`
* `wall`
* `foot_restraint`
* `panel_console`

A complete category list and ID mapping will be provided in the repository documentation at release time.

---

## Coordinate Frame and Units (Planned Documentation)

To support reproducible reconstruction and evaluation, the release documentation will explicitly define:

* coordinate frame convention (e.g., camera/world/scene frame)
* handedness (right-handed / left-handed)
* axis directions (`+x`, `+y`, `+z`)
* origin definition
* units (meters, radians)

---

## Raw Source Videos

Raw source videos are **not redistributed** in this repository.

Since the source videos were collected from publicly available online resources and may be subject to third-party terms, this repository will instead provide:

* the **original source links (URLs)**, and
* **instructions for obtaining the source videos**

used in our data processing pipeline.

---

## Release Plan

We are preparing a public release of the processed trajectory dataset (`.npz`) including **SMPL parameters** and **contact annotations**.

This repository will be updated with:

* dataset download link
* license
* usage instructions
* file format specification
* field dictionary
* semantic contact taxonomy
* parsing examples (if provided)

---

## Data Availability Statement (Repository-Aligned)

A public project page is maintained in this repository, which currently provides dataset documentation and release planning information. We are preparing a public release of the processed trajectory dataset in `.npz` format, including SMPL parameters and contact annotations (vertex-level binary contact labels and semantic contact categories). The repository will be updated with the download link, license, and usage instructions when the release package is finalized. Raw source videos are not redistributed; instead, original source links (URLs) and acquisition instructions will be provided.

---

## Citation

A BibTeX entry will be added after publication.

---




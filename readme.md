# Microgravity Human Contact Dataset (Planned Release)

This repository hosts the documentation and release plan for a processed microgravity motion/contact dataset used for robot-astronaut motion learning research.

## Status

**Current status:** Documentation-only (README + data format specification).  
**Planned release:** Processed trajectory files in `.npz` format (SMPL + contact annotations).

A public download link will be added to this repository upon release.

---

## Planned Dataset Contents

Each trajectory will be released as a processed `.npz` file (no raw video in this repository), including:

- **SMPL kinematic parameters**
  - pose parameters (`poses`)
  - global/root translation (`trans` or `transl`)
  - shape parameters (`betas`, if included in the release)
- **Contact annotations**
  - vertex-level binary contact labels (`contact`)
  - vertex-level semantic contact categories (`obj`)
- **Metadata**
  - e.g., `gender` (and additional fields if provided)

The release is intended for reproducible research in imitation learning, contact-aware motion modeling, and robot astronaut mobility tasks in microgravity environments.

---

## Data Format (Planned)

The processed files are designed to be AMASS-compatible (or AMASS-style) where applicable.

### Core fields (example)

- `poses`: shape `(T, 72)`, `float32`  
  SMPL pose parameters in axis-angle representation (radians).

- `trans` (or `transl`): shape `(T, 3)`, `float32`  
  Metric root translation sequence (meters).

- `betas`: shape `(10,)`, `float32`  
  SMPL shape parameters (if included).

- `contact`: shape `(T, 6890)`, `uint8`/`bool`  
  Binary vertex-level contact labels.

- `obj`: shape `(T, 6890)`, integer type  
  Vertex-level semantic contact category labels. `0` indicates no contact.

- `gender`: string or scalar metadata  
  SMPL model loading metadata.

> **Note:** Final field names and exact dtypes will be documented in the release version.  
> In particular, the translation key may be `trans` or `transl` depending on the release package.

---

## Semantic Contact Taxonomy (Planned)

`obj[t, v]` stores a semantic contact category ID for SMPL vertex `v` at frame `t`.

- `0`: no_contact
- Positive IDs (`1...K`): predefined environment-contact categories

The complete category list and ID mapping will be provided in this repository (see `docs/category_taxonomy.md` in a future update).

Example categories (subject to the final release specification):
- handrail
- wall
- foot restraint
- panel / console

---

## Coordinate Frame and Units (Planned Documentation)

The release documentation will explicitly define:

- coordinate frame convention (e.g., camera/world frame)
- handedness (right-handed / left-handed)
- axis directions (`+x`, `+y`, `+z`)
- origin definition
- units (meters, radians)

This information will be included in the data specification to support reproducible reconstruction and evaluation.

---

## Release Plan

We plan to release the processed trajectory dataset in `.npz` format, including SMPL parameters and contact annotations:

- **Timing:** upon paper acceptance / after publication / by [target date]
- **Repository updates to include:**
  - download link
  - license
  - changelog
  - parsing examples
  - field dictionary and category taxonomy tables

---

## What Is Not Included (Current Plan)

- Raw source videos are **not** included in this repository [due to copyright/privacy/institutional constraints, if applicable].
- This repository currently does **not** contain the final downloadable dataset files.

---

## Citation (To Be Added)

A citation entry (BibTeX) will be added after publication.

---

## Contact

For questions regarding the planned release, please open an issue in this repository or contact: [project email]

(If issue tracking is disabled during review, contact via email.)

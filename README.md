# hers-devtool-json

Dev-tool / Intake Speedrunner V2 configuration and answer map JSON files.

## Table of Contents

- [Project Overview](#project-overview)
- [How to Use](#how-to-use)
    - [Loading Default Configurations](#loading-default-configurations)
    - [Running the Speedrunner](#running-the-speedrunner)
    - [Creating and Managing Custom Answer Maps](#creating-and-managing-custom-answer-maps)
- [Working with Data JSON](#working-with-data-json)
- [Customizing Default Configurations](#customizing-default-configurations)

---

## Project Overview

**Intake Speedrunner V2** is a browser-based development utility that speeds up QA and development workflows for medical intake forms. It allows you to automate the process of filling out patient questionnaires by preloading answer maps from JSON configurations. These answer maps can be defaulted by treatment type or fully customized to fit unique testing scenarios.

---

## How to Use

### Loading Default Configurations

Loading Default Configurations
Start a V2 visit and navigate to a medical intake form. These pages typically have URLs that include the word "intake".

Once on the intake page, click the Load Default PSYCHIATRY Config (or choose WEIGHT_MANAGEMENT, HAIR_LOSS).

Then click Run, Run Once, or Stop Run depending on what you need.

ℹ️ Speedrunner Unavailable:
If you are not on a valid intake form page, you’ll see the message:
"Speedrunner unavailable: This tool works only on intake form pages. Start a v2 visit and go to a URL containing 'intake'."

The tool will auto-detect:

Whether you are on the Hims or Hers domain

The correct treatment type

It will then load the appropriate default answer map. Once loaded, the configuration will appear in the Saved answer maps section and its content will populate the text area.
---

### Running the Speedrunner

You can run the tool once a configuration is loaded into the textarea. The action buttons are enabled only on valid medical intake pages.

**Supported Routes by Treatment:**

- `WEIGHT_MANAGEMENT`: `/wm/medical-intake?offset={...}`
- `PSYCHIATRY`: `/c/mh/p-g?offset={...}`
- `HAIR_LOSS`: `/hl/intake-step?offset={...}`

**Controls:**

- 🏃 **Run**: Auto-fill and auto-advance through the form.
- 🐢 **Run Once**: Fill only the current page.
- 🛑 **Stop Run**: Interrupt execution.

---

### Creating and Managing Custom Answer Maps

1. Click **Copy current `visit.answers`** to grab answers from your session.
2. Paste into the text area and name the configuration.
3. Click **Save Answer Map** to store in browser local storage.
4. Use saved map buttons to **load** or **delete** them.

---

## Working with Data JSON

All configuration files reside under:
`packages/web/components/dev-menu/data/`

They are named by treatment type and brand:

- `weight_management_hims.json`
- `weight_management_hers.json`
- `psychiatry_hims.json`
- `psychiatry_hers.json`
- `hair_loss_hims.json`
- `hair_loss_hers.json`

Each JSON file supports **multiple named answer maps**, structured like this:

```json
{
  "happy_path_v1": {
    "question_id_1": "answer_id_a",
    "question_id_2": "answer_id_b"
  },
  "edge_case_v1": {
    "question_id_1": "answer_id_c",
    "question_id_2": "answer_id_d"
  }
}
```

## Customizing Default Configurations

To extend or customize configurations for Hims or Hers:

1. Open the relevant `.json` file inside the `data/` directory.
2. Add a new key-value object for your test case. Use a clear name, like `smoke_test_01`.
3. Fill it with the desired answers using the `question_id: answer_id` format.

### Example

```json
{
  "smoke_test_01": {
    "q1": "a1",
    "q2": "a2",
    "q3": "a3"
  }
}
```

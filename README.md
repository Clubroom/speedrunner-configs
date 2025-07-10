# 🚀 Questionnaire Speedrunner

A tool for automating medical intake forms on Hims and Hers platforms. The speedrunner supports multiple treatment types and provides an intuitive interface for filling out forms quickly.

## 📋 Table of Contents

- [🎯 Supported Treatments](#-supported-treatments)
- [🚀 Quick Start](#-quick-start)
- [🎮 Controls & Buttons](#-controls--buttons)
- [📖 How to Use](#-how-to-use)
  - [Loading Default Configurations](#loading-default-configurations)
  - [Running the Speedrunner](#running-the-speedrunner)
  - [Creating Custom Answer Maps](#creating-custom-answer-maps)
- [⚙️ Configuration Management](#️-configuration-management)
- [🚨 Troubleshooting](#-troubleshooting)

## 🎯 Supported Treatments

The speedrunner works with these treatment types on both Hims and Hers platforms:

- **Weight Management** - `/wm/medical-intake`, `/wm/intake-height-weight`
- **Mental Health (Psychiatry)** - `/c/mh/p-g`, `/mh/intake`

## 🚀 Quick Start

1. **Go to an intake page** (URL contains "intake", "medical-intake", "intake-height-weight", "/mh/p-g", or "/mh/intake")
2. **Open Dev tool** - Intake Speedrunner V2
3. **Load a configuration** - Click `Load Default Config` button
4. **Click Run** - Auto-fills and advances through the form


## 🎮 Controls & Buttons

<details>
<summary><strong>🏃 Action Buttons</strong></summary>

| Button | Icon | Description |
|--------|------|-------------|
| **Run** | 🏃 | Auto-fills forms and advances through all pages |
| **Run Once** | 🐢 | Fills only current page |
| **Stop Run** | 🛑 | Stops the speedrunner |

</details>

<details>
<summary><strong>⚙️ Configuration Buttons</strong></summary>

| Button | Description |
|--------|-------------|
| **Load Default Config** | Automatically detects treatment type and loads default configuration from repository |
| **Copy current visit.answers** | Copies answers from current session |
| **Save Answer Map** | Saves the current configuration to local storage |
| **Load** | Loads a saved configuration (source and name are automatically updated) |
| **🗑️** | Deletes a saved configuration |

**Configuration Sources:**
- ⭐ **Remote** - Default configurations from repository
- 💾 **Saved** - Configurations saved to local storage
- 📂 **Uploaded** - Custom uploaded JSON files
- ✍️ **Manual** - Manually entered configurations

</details>

<details>
<summary><strong>🔧 Advanced Settings</strong></summary>

**Optional settings (at least one must be enabled to activate controls):**
- **File Upload** - Upload custom JSON configuration files (usually best source)
- **Use smart default answers** - Fallback answers (if enabled) helps with smart filling if flow changed
- **Generate random answers** - Random answers (if enabled) helps with random filling if flow changed

**Priority System:**
- 🥇 **Priority 1**: Remote/Default answers (highest priority)
- 🥈 **Priority 2**: Fallback answers
- 🥉 **Priority 3**: Intelligent detection based on question content (in progress)
- 🎲 **Priority 4**: Random fallback (lowest priority)

</details>

<details>
<summary><strong>📁 Folding Options</strong></summary>

**Interface Folding:**
- **Folding feature** - Helps improve visibility by collapsing/expanding sections
- **Waiting state** - Shows when folding option is available but not active
- **Active state** - Automatically changes from waiting to active when available
- **Run compatibility** - Works seamlessly with the Run functionality

**Benefits:**
- **Space optimization** - Reduces screen clutter when folded
- **Better visibility** - Easier to see more content when sections are collapsed
- **Improved workflow** - Maintains functionality while providing cleaner interface

</details>

## 📖 How to Use

<details>
<summary><strong>1️⃣ Loading Default Configurations</strong></summary>

1. **Navigate to an intake page** (URL contains "intake", "medical-intake", "intake-height-weight", "/mh/p-g", or "/mh/intake")
2. **Open Dev tool** - Intake Speedrunner V2
3. **Click** `Load Default Config` - Automatically detects treatment type
4. **Click Run** to start auto-filling

> ℹ️ **Note**: Tool only works on intake form pages (URLs containing "intake", "medical-intake", "intake-height-weight", "/mh/p-g", or "/mh/intake"). The speedrunner automatically detects Hims/Hers and treatment type, then loads the appropriate configuration from repository.

</details>

<details>
<summary><strong>2️⃣ Creating Custom Answer Maps</strong></summary>

1. **Copy current session** - Click `Copy current visit.answers`
2. **Paste and edit** in the text area
3. **Name your configuration** and click `Save Answer Map`
4. **Manage saved configurations** using Load/Delete buttons

</details>

## ⚙️ Configuration Management

<details>
<summary><strong>📝 JSON Configuration Format</strong></summary>

**Input Field Format (what you enter):**
```json
{
  "question_id_1": "answer_id_a",
  "question_id_2": "answer_id_b"
}
```

**File/Git Format (with smart detection):**
```json
{
  "configuration_name": {
    "question_id_1": "answer_id_a",
    "question_id_2": "answer_id_b"
  }
}
```

**Smart Detection:**
- **Single configuration**: Automatically selects it and places the inner object in the textarea
- **Multiple configurations**: Prompts user to select which scenario to use
- **The speedrunner always uses the flat object in the textarea as the answer map**

</details>

## 🚨 Troubleshooting

<details>
<summary><strong>❓ Common Issues</strong></summary>

**"Speedrunner unavailable" Message**
- Navigate to a valid intake form page (URL contains "intake", "medical-intake", "intake-height-weight", "/mh/p-g", or "/mh/intake")

**Configuration Not Loading**
- Verify JSON syntax is valid
- Try loading a default configuration first

**Speedrunner Stops Unexpectedly**
- Try "Run Once" to test individual pages
- Check browser console for error messages
- Enable fallback options if the form flow has changed and some questions are missing

**Performance Issues**
- Clear browser cache and local storage

</details>

<details>
<summary><strong>🔍 Debug Mode</strong></summary>

Enable debug logging in browser developer tools:
```javascript
localStorage.setItem('speedrunner_debug', 'true');
```

</details>

---

**Need help?** Check the troubleshooting section above or reach out to the development team.

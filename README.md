# 🔎 SFMC SQL Activity Content Inspector

A lightweight **CloudPage solution** for Salesforce Marketing Cloud that allows developers to inspect the contents of a **SQL Query Activity** without needing to pause or deactivate an Automation.

### 💡 The Problem it Solves

In Marketing Cloud, once an Automation is **Activated**, you cannot view the SQL syntax inside its Query Activities without pausing the automation. This tool bypasses that restriction by using `WSProxy` to fetch the `QueryDefinition` directly from the system, regardless of its activation status.

---

## 🚀 Key Features

* **Status Agnostic:** Works for both "Activated" and "Non-Activated" queries.
* **Dual-Lookup Logic:** It searches both `QueryDefinition` (general queries) and `AutomationActivity` (queries specifically tied to automations) to ensure the metadata is found.
* **Full Metadata:** Returns the **SQL Statement**, the **Target Data Extension**, and the **Update Type** (Overwrite, Update, or Append).
* **Syntax Styling:** Displays SQL code in a dark-themed, monospace container for easy reading and copying.

---

## 🛠️ How to Deploy

1. **Create a CloudPage:** In Marketing Cloud, go to **CloudPages** and create a new **Landing Page**.
2. **Paste the Code:** Switch to the **Code View** and paste the provided HTML/SSJS code.
3. **Publish:** Schedule and Publish the page.
4. **Usage:** * Copy the **exact name** of your SQL activity from Automation Studio.
* Paste it into the search box on your new CloudPage.
* Click **Inspect SQL Query Activities**.



---

## 📖 Technical Details

The tool uses Server-Side JavaScript (SSJS) and the `WSProxy` object to interact with the Marketing Cloud SOAP API:

| Component | Description |
| --- | --- |
| **WSProxy Retrieve** | Used to pull `QueryDefinition` properties like `QueryText` and `DataExtensionTarget`. |
| **AutomationActivity** | Used as a secondary check to verify if the query is associated with an active automation. |
| **Grid Layout** | A CSS-based layout used to display the "Target DE" and "Update Type" side-by-side. |

> [!WARNING]
> **Case Sensitivity:** The `SimpleOperator: "equals"` filter is case-sensitive. Ensure you provide the exact name as it appears in the SFMC UI.

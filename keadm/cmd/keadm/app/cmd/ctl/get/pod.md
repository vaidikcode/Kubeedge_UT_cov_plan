# **Code Coverage Improvement Report**

## **1. Untested Code**

Below are the untested sections of the codebase:

- **`NewEdgePodGet` function:**
    - The `RunE` function is partially tested.
    - The `cmdutil.CheckErr(podGetOptions.getPods(args))` line is **untested**.

- **`getPods` function:**
    - The entire function is **untested**.
    - Key untested logic includes:
        - Handling of `args` when they contain pod names.
        - Fetching pods from `GetPod` and `GetPods`.
        - Filtering based on `nodeName`.
        - Error handling when `ParseEdgecoreConfig` fails.
        - Handling JSON/YAML output.

- **`ConvertDataToTable` function:**
    - The entire function is **untested**.

---

## **2. Test Logic for Coverage**

To improve test coverage, the following logic should be implemented:

### **For `getPods` function:**
- **Test behavior when `args` contain pod names.**
- **Test when `args` are empty (retrieving all pods).**
- **Test error handling when parsing edgecore config fails.**
- **Test when no pods are found in the namespace.**
- **Test filtering of pods based on `nodeName`.**
- **Test output in JSON/YAML formats.**
- **Test table output conversion.**

### **For `NewEdgePodGet` function:**
- **Ensure `RunE` function executes properly.**
- **Validate error handling in `cmdutil.CheckErr(podGetOptions.getPods(args))`.**

### **For `ConvertDataToTable` function:**
- **Validate table conversion logic.**
- **Check edge cases with empty/invalid input.**

---

## **3. Test Coverage Summary**

| **Metric**               | **Before Adding Tests** | **After Adding Tests** |  
|--------------------------|------------------------|------------------------|  
| **Tracked Lines**        | **104**               | **104**               |  
| **Covered Lines**        | **26**                | **89**                |  
| **Partial Coverage**     | **1**                 | **1**                 |  
| **Missed Lines**         | **77**                | **14**                |  
| **Test Coverage %**      | **25%**               | **85.57%**            |  

> **Note:** This matrix is specific to the `pod_get.go` file.

---

## **4. Additional Notes**

- The most critical untested logic is in `getPods`, which needs **mocked API calls** for `GetPod` and `GetPods`.
- The `ConvertDataToTable` function should be **tested for table conversion correctness**.
- Edge cases such as **empty args, incorrect namespace, and failed config parsing** must be **covered**.

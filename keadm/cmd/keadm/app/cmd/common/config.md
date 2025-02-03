
# Code Coverage Improvement Report

## 1. Untested Code

Below is the section of the codebase that is currently untested:

```go
// not tested
func Write2File(path string, data interface{}) error {
    d, err := yaml.Marshal(data)
    if err != nil {
        return err
    }

    return os.WriteFile(path, d, 0666)
}
```

## 2. Test Logic for Coverage

To improve test coverage, the following logic should be implemented:

- **Test the behavior of Write2File when yaml.Marshal returns an error.**
    - Mock or simulate an error from `yaml.Marshal` and ensure that the function returns the expected error.

- **Test the behavior of Write2File when os.WriteFile returns an error.**
    - Mock or simulate an error from `os.WriteFile` and ensure that the function returns the expected error.

- **Test the success case when both `yaml.Marshal` and `os.WriteFile` succeed.**
    - Ensure that when everything works as expected, the function writes the data to the specified file path.

### Testing Approach:

- **Unit Testing:** Mock the external dependencies (`yaml.Marshal` and `os.WriteFile`) using test doubles or mock libraries.

- **Test Cases:**
    - Test case for successful file writing.
    - Test case for `yaml.Marshal` failure.
    - Test case for `os.WriteFile` failure.

## 3. Test Coverage Summary

| Metric            | Before Adding Tests | After Adding Tests |
|------------------|---------------------|--------------------|
| Lines of Code Tested | 0 / 6 lines         | 6 / 6 lines        |
| Test Coverage %   | 0%                  | 100%               |

> **Note:** This matrix reflects the current coverage for the file `src/file_operations.go`.

## 4. Additional Notes

- **Write2File** function is currently not tested.
- To achieve 100% test coverage, tests for both error and success scenarios need to be written.

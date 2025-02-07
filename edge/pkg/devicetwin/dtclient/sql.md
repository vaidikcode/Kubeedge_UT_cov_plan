## TestLogicforInitDBTable

1. Testing Successful Database Table Initialization
Setup: Create a mock core.Module that is enabled and has a valid name.
Execution: Call InitDBTable with the mock module.
Validation: Verify that:
The function logs the correct initialization message.
orm.RegisterModel is called for Device, DeviceAttr, and DeviceTwin.
2. Testing When Module is Disabled
Setup: Create a mock core.Module that is disabled.
Execution: Call InitDBTable with the disabled module.
Validation: Ensure that:
The function logs that the module is disabled.
orm.RegisterModel is not called.
3. Testing Logging Messages
Setup: Use a logging interceptor or mock klog to capture logs.
Execution: Run InitDBTable with both enabled and disabled modules.
Validation: Ensure that:
The logs correctly indicate whether the module is registered or skipped.
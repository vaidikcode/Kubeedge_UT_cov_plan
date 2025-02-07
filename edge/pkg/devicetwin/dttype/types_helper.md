
## types_helper

Unmarshal Functions:

Test UnmarshalMembershipDetail: Ensure correct unmarshalling of a membership detail payload into the MembershipDetail struct. Provide valid and invalid JSON inputs and verify the results.
Test UnmarshalMembershipUpdate: Similar to the above, test with both valid and invalid membership update payloads.
Test UnmarshalBaseMessage: Test with a valid BaseMessage payload and ensure proper unmarshalling, as well as error handling with invalid payloads.
Test UnmarshalDeviceUpdate: Test with valid and invalid DeviceUpdate payloads, ensuring correct parsing and error handling.
Device Attribute and Twin Conversion Functions:

Test DeviceAttrToMsgAttr: Verify that the device attributes are correctly converted to MsgAttr format, testing with different device attributes and checking if optional values and metadata are properly handled.
Test DeviceTwinToMsgTwin: Test conversion of device twin objects into MsgTwin. Ensure all fields like Expected, Actual, ExpectedVersion, and ActualVersion are correctly populated based on the device twin data.
Test MsgAttrToDeviceAttr: Test that the conversion from MsgAttr to DeviceAttr works correctly, especially considering optional fields and attribute types.
Test MsgTwinToDeviceTwin: Test conversion of MsgTwin back to DeviceTwin and ensure the correct setting of attributes like Optional, AttrType, and Version.
Copy Functions:

Test CopyMsgTwin: Test whether the function correctly copies MsgTwin objects with and without version information.
Test CopyMsgAttr: Test copying of MsgAttr objects, ensuring that the content is correctly cloned without modifying the original object.
Building Device Messages:

Test BuildDeviceCloudMsgState: Provide a BaseMessage and Device object and ensure that the message is correctly constructed and serialized to JSON.
Test BuildDeviceAttrUpdate: Validate the correct construction of a device attribute update message from given attributes.
Test BuildMembershipGetResult: Verify that the correct membership result is built when given a list of devices. Ensure that the result matches the expected structure.
Test BuildDeviceTwinResult: Validate that the device twin result is correctly built with correct mappings for MsgTwin objects based on different twin states (0 for get, 1 for update, 2 for sync).
Test BuildErrorResult: Ensure error result messages are built with the right EventID, Code, and Reason.
Delta Calculation:

Test BuildDeviceTwinDelta: Test the calculation of twin deltas by comparing expected and actual values for each twin. Ensure that the function returns the expected payload and correctly identifies differences between the two values. Test cases with no delta should return a boolean indicating no changes.
Test BuildDeviceTwinDocument: Ensure correct construction of the twin document message based on the TwinDoc data. This will require testing the JSON output and verifying that the structure is valid.
Error Handling:

For all functions, test edge cases such as:
Missing fields.
Incorrect data types.
Invalid JSON structures.
Testing the robustness of unmarshalling and message construction functions against malformed or incomplete data.
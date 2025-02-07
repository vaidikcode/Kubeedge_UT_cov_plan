
## Test Logic for MQTT Message Handlers

Setup & Teardown
Mock beehiveContext.SendToGroup.
Capture messages sent to verify correctness.
Reset mocks after each test.
Test Cases for handleDeviceTwin
Test Message Routing to Twin Group
Call handleDeviceTwin with a valid topic (e.g., $hw/events/device/123/twin/update).
Verify that the target group is TwinGroup.
Ensure the resource is correctly base64 encoded.
Validate that SendToGroup is called with expected arguments.
Test Cases for handleUploadTopic
Test Message Routing to Hub Group

Call handleUploadTopic with SYS/dis/upload_records.
Verify that the target group is HubGroup.
Ensure that SendToGroup is called with the correct message structure.
Test Payload Integrity

Send different payloads.
Verify that the payload remains unchanged in the FillBody call.
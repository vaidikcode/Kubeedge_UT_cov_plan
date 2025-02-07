
## All test logic for filter

Test Logic for mqtt Message Mux
Setup & Teardown
Initialize a MessageMux instance.
Register mock handlers.
Clean up after tests.
Test Cases for MessageExpression
Test GetExpression Generates Correct Regex
Verify regex for static topics (e.g., device/data).
Verify regex for parameterized topics (e.g., device/{id}/data).
Ensure wildcard (*) is correctly handled.
Test Cases for MessagePattern
Test Match Method Matches Correct Topics
Create a pattern for device/{id}/data.
Check that device/123/data matches.
Ensure device/123/status does not match.
Test Cases for MessageMux
Test Entry Adds Handlers Correctly

Register a handler for device/{id}/data.
Verify that it is added to muxEntry.
Test Dispatch Calls Correct Handler

Register multiple handlers.
Dispatch a message to a matching topic.
Ensure the correct handler is called.
Test Dispatch Calls handleUploadTopic When No Match Found

Dispatch a message that does not match any handler.
Verify handleUploadTopic is called.
Test RegisterMsgHandler Registers Expected Handlers

Call RegisterMsgHandler.
Verify that handlers for $hw/events/device/ and SYS/dis/upload_records are registered.

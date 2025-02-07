
## Test Logic for config Package

Test Cases for InitConfigure
Test Single Initialization

Call InitConfigure with a valid EdgeHub config and a node name.
Verify that Config is correctly initialized with the expected values.
Test Idempotent Initialization (Singleton Behavior)

Call InitConfigure multiple times with different values.
Verify that Config remains unchanged after the first initialization.
Test WebSocketURL Formatting

Pass different EdgeHub configurations and node names.
Ensure that WebSocketURL is formatted correctly based on input values.
Test Empty EdgeHub Config

Provide an empty EdgeHub struct and verify how WebSocketURL is constructed.
Test Edge Cases for WebSocket.Server and ProjectID

Use edge cases like missing WebSocket.Server, empty ProjectID, or special characters in nodeName.
Ensure WebSocketURL generation still functions as expected.
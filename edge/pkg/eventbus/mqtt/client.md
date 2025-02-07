
## All test logic for client

Test Logic for mqtt Package
Setup & Teardown
Initialize a mock MQTT broker.
Set up test MQTT clients.
Clean up connections after tests.
Test Cases for MQTT Client Initialization
Test InitPubClient Successfully Creates a Publisher

Call InitPubClient.
Verify that the PubCli client is connected.
Ensure it uses the expected PubClientID.
Test InitSubClient Successfully Creates a Subscriber

Call InitSubClient.
Verify that SubCli is connected.
Ensure it subscribes to predefined SubTopics.
Test Cases for Subscription Handling
Test onSubConnect Subscribes to Default Topics

Simulate an MQTT connection event.
Check that all topics in SubTopics are subscribed.
Test onSubConnect Subscribes to Stored Topics

Mock database with stored topics.
Verify the client subscribes to those topics on connection.
Test Cases for Connection Loss Handling
Test onPubConnectionLost Reinitializes Publisher

Simulate a connection loss.
Verify InitPubClient is called.
Test onSubConnectionLost Reinitializes Subscriber

Simulate a connection loss.
Verify InitSubClient is called.
Test Cases for Message Handling
Test OnSubMessageReceived Dispatches Messages
Simulate receiving an MQTT message.
Verify that NewMessageMux().Dispatch() is called with the correct topic and payload.
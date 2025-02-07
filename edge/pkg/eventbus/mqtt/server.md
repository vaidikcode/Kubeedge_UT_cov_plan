
## Test Logic for MQTT Internal Server

Setup & Teardown
Initialize Server with a mock transport and backend.
Mock transport.Launch to simulate server startup.
Capture logs and backend interactions.
Reset mocks after each test.
Test Cases for Run
Test Successful Server Start

Call Run and verify that:
transport.Launch is called with the correct URL.
broker.NewMemoryBackend initializes properly.
The broker engine starts accepting connections.
Test Server Start Failure

Simulate an error in transport.Launch.
Verify that the function returns the expected error.
Ensure logs capture the failure.
Test Cases for onSubscribe
Test Message Dispatch on Subscription Match
Publish a message with a topic that exists in the topic tree.
Verify NewMessageMux().Dispatch is called with the correct topic and payload.
Test Cases for InitInternalTopics
Test Default Topic Subscription

Call InitInternalTopics.
Ensure all SubTopics are added to the topic tree with correct QoS.
Test Database Topic Subscription

Mock dao.QueryAllTopics to return stored topics.
Verify that retrieved topics are added to the topic tree.
Handle case where no topics exist.
Test Cases for SetTopic & RemoveTopic
Test Topic Addition

Call SetTopic with a sample topic.
Verify it is added to the topic tree.
Test Topic Removal

Call RemoveTopic with a previously added topic.
Verify it is removed from the topic tree.
Test Cases for Publish
Test Message Publishing
Call Publish with a topic and payload.
Verify that backend.Publish is called with the correct message.
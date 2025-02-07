## Test Cases for NewWebSocketClient
Test Initialization with Valid Config

Provide a valid WebSocketConfig and ensure that NewWebSocketClient correctly initializes the struct.
Test Initialization with Nil Config

Pass nil to NewWebSocketClient and check for proper handling (should return an error or panic).
Test Cases for Init
Test Successful Initialization

Provide valid TLS certificates and verify that Init correctly establishes a connection.
Test Initialization with Invalid Certificate Paths

Set invalid paths for CertFilePath or KeyFilePath, and ensure Init fails with the expected error.
Test Initialization with Malformed Certificates

Provide incorrectly formatted certificates and check if Init detects and handles the issue.
Test Initialization with Invalid CA Certificate

Simulate a scenario where config.Config.TLSCAFile contains invalid CA certificates and verify that Init fails.
Test Initialization with Failed Connection

Simulate a network failure or incorrect URL, and verify that Init retries the expected number of times before returning an error.
Test Maximum Retry Mechanism

Ensure Init makes exactly retryCount connection attempts before failing.
Test Cases for UnInit
Test Closing an Active Connection

Ensure that UnInit successfully closes the connection.
Test Closing an Already Closed Connection

Call UnInit multiple times and verify that it does not cause a panic.
Test Cases for Send
Test Sending Message Successfully

Mock a valid connection and verify that Send correctly sends the message.
Test Sending Message with Closed Connection

Close the connection and check if Send returns an appropriate error.
Test Sending Message with Nil Connection

Set wsc.connection to nil and ensure that Send fails gracefully.
Test Sending Large Message

Send a message of significant size and ensure proper handling.
Test Write Deadline Failure

Mock a scenario where SetWriteDeadline fails and ensure Send properly handles the error.
Test Cases for Receive
Test Receiving Message Successfully

Mock a connection that sends a valid model.Message and verify correct deserialization.
Test Receiving Message with Closed Connection

Close the connection before calling Receive and ensure it returns an appropriate error.
Test Receiving Corrupted Message

Simulate a case where a corrupted message is received and check how the function handles it.
Test Cases for Notify
Test Notify Logging Behavior
Ensure that Notify logs the expected message when called.

## Test Cases for Restart Method

Valid Restart Request

Send a valid JSON body with a list of pod names.
Ensure the storage Restart method is called with correct arguments.
Expect a successful response (200 OK) with restart response JSON.
Invalid JSON Body

Send an improperly formatted JSON.
Expect an error response (500 Internal Server Error).
Storage Restart Failure

Simulate an error in the Restart method.
Expect an error response (500 Internal Server Error).
Test Cases for ConfirmUpgrade Method
Successful Upgrade Command Execution

Ensure upgrade logs are generated.
Verify that the correct upgrade command is executed.
Expect a successful response.
Upgrade Command Execution Failure

Simulate an error in exec.Command.
Expect an error response (500 Internal Server Error).
Database Cleanup Failure

Simulate an error while deleting upgrade metadata.
Verify log warnings are generated but request still succeeds.
Test Cases for Logs Method
Valid Log Retrieval

Provide a valid request with all expected query parameters.
Ensure the Logs method of storage is called correctly.
Expect a 200 OK response with JSON logs.
Failure in Retrieving Logs

Simulate a failure in storage.Logs.
Expect an error response (500 Internal Server Error).
Log Streaming Enabled (follow=true)

Ensure streaming is enabled when follow=true.
Validate that logs are streamed as chunks.
Log Streaming Not Supported

Simulate a response writer that does not support streaming.
Expect an error response (500 Internal Server Error).
Test Cases for Exec Method
Valid Execution Request

Provide valid query parameters for execution.
Ensure Exec method of storage is called correctly.
Expect a 200 OK response with execution result.
Execution Handler Exists

Simulate the presence of an HTTP handler in storage.Exec.
Ensure the handler is invoked correctly.
Execution Failure

Simulate an error response from storage.Exec.
Expect an error response (500 Internal Server Error).
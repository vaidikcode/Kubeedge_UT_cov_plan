
## test logic for storage

1. Agent and Cloud Fallback Paths
For Methods That Use the Agent (e.g., Get, List, Create, Update, Patch, Delete, PassThrough)
Success Path (Cloud Returns a Valid Response)
Setup:
Simulate a successful call by having the agent’s Generate and Apply methods return a valid response (for example, a JSON-encoded unstructured object or list).
Ensure that any side effects (like inserting the object into local storage via the imitator client) are “observed” (for example, by verifying that the appropriate stub was called).
Verification:
Confirm that the returned object is correctly unmarshalled.
Validate that the response contains the expected fields and that any decoration (like setting the GVK on a list) is performed.
Error/Failure Path (Agent Call Fails)
Setup:
Simulate an error in the agent call (e.g., error from Apply or Generate).
Configure the local store (or the fallback imitator) to return either a valid object (for Get/List) or an error.
Verification:
For Get: Verify that when the cloud call fails, the fallback to the local store’s Get is triggered and, if that fails, an appropriate “NotFound” error is returned.
For List/PassThrough: Check that the fallback mechanism retrieves the object or list from local storage when the remote call fails.
Confirm that the error messages are logged appropriately.
2. Method-Specific Testing
Get
Cloud Success Scenario:
Simulate a valid JSON response from the agent.
Check that the object is unmarshalled correctly.
Verify that the object is saved into the local storage (imitator client).
Cloud Failure Scenario:
Force the agent call to error out.
Verify that the local store’s Get is called and that, if it returns an error, a NotFound error is generated with the proper group/resource details.
PassThrough
Cloud Success:
Simulate a valid response from the agent.
Verify that the response is stored using the imitator’s InsertOrUpdatePassThroughObj.
Cloud Failure:
Simulate an error and ensure the fallback to GetPassThroughObj works.
Validate that if the fallback also fails, the method returns a proper NotFound error.
List
Cloud Success:
Simulate a successful remote call returning a valid unstructured list.
Verify that the helper function decorateList sets the GroupVersionKind if needed.
Cloud Failure:
Force the agent to fail and then simulate a successful response from the local store’s List.
Validate that the list is returned correctly.
Watch
Cloud Watch Application Success:
Simulate a successful watch setup (agent’s Generate/Apply for a watch request) and ensure that the context is decorated with an application ID.
Confirm that the fallback local store’s Watch is eventually returned.
Cloud Watch Application Failure:
Simulate an error in the agent call and check that the method still returns a watch interface from the local store.
Create
Success:
Simulate the agent returning a valid JSON response for a created object.
Verify that the object is correctly unmarshalled and returned.
Failure:
Simulate an agent error and check that the error is properly returned.
Delete
Success:
Simulate a successful deletion via the agent.
Verify that the method returns a “successful” flag (true) and no object.
Failure:
Simulate an error from the agent and check that the error is propagated.
Update
Regular Update vs. Status Subresource:
For a regular update, simulate an agent call that returns a valid updated object.
For an update on the “status” subresource, ensure that the agent is called with the correct verb (UpdateStatus) and the response is handled similarly.
Error Handling:
Simulate an error in generating or applying the agent call, and check that the error is wrapped as an internal error.
Patch
Success:
Simulate a valid patch response from the agent.
Verify that the resulting object is correctly unmarshalled.
Failure:
Simulate a failure in the agent call and check that the error is returned.
3. Remote Runtime Service Functions (Restart, Logs, Exec)
For these methods, you will need to simulate interactions with a remote runtime service.

Restart
Successful Restart:
Simulate a valid container list for a given pod.
For each container, have the StopContainer call succeed.
Verify that the response contains a success log message.
Partial or Complete Failure:
Simulate some containers failing to stop (or none found).
Confirm that error messages are aggregated in the response.
Runtime Service Creation Failure:
Force remote.NewRemoteRuntimeService to return an error.
Validate that the response includes an appropriate error message.
Logs
Edged Disabled:
Set the configuration to disable edged.
Confirm that the response contains an error message stating that edged is not enabled.
Successful Log Retrieval:
With edged enabled, simulate finding the target pod (via container list) and a successful call to the RESTful logs request.
Verify that the HTTP response (or the log messages in the response) is as expected.
Container Not Found or Runtime Service Error:
Simulate scenarios where no containers match the pod labels or where the runtime service fails.
Check that the error messages are correctly recorded.
Exec
Edged Disabled / Missing Command:
Test that if edged is disabled or if no command is provided, an error message is returned immediately.
Non-TTY Mode Execution:
Simulate a call to ExecSync that returns valid stdout and stderr.
Verify that the returned ExecResponse includes the expected output and error messages.
TTY Mode Execution:
Simulate a successful call to Exec that returns an execution URL.
Verify that the URL is parsed correctly and that a proxy handler is created and returned.
Multiple Containers / Container Not Found:
Test cases where either multiple containers exist (and no container name was provided) or the specified container is not found.
Check that appropriate error messages are generated in the ExecResponse.
4. General Considerations
Dependency Injection / Mocking:

For each method, replace the agent, local store, imitator client, and remote runtime service with mocks or fakes that you can control in tests.
This allows you to simulate both successful responses and various error conditions.
Context and Request Info:

Create test contexts that include the necessary request information (using functions like apirequest.WithRequestInfo or similar) so that functions like decorateList and error messages get the correct group, version, and resource values.
Logging Verification:

Although verifying log output is secondary, ensure that when errors occur, the expected error messages are logged (this might involve capturing logs if needed).
Side Effects and External Calls:

Verify that any side effects (such as inserting/updating objects in the local store via the imitator client) are triggered when appropriate.
For methods that interact with external APIs (e.g., the RESTful logs request), simulate both success and failure responses.
Error Propagation:

Confirm that errors (whether from the agent, local store, or remote runtime service) are correctly propagated back to the caller with the proper error types (e.g., errors.NewNotFound, errors.NewInternalError).

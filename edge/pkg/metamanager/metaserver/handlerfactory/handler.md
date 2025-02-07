
## Test Plan for Factory Handlers

1. Initialization & Factory Creation
Verify that NewFactory() correctly initializes the Factory struct.
Ensure that storage is initialized properly.
Validate that scope is set correctly.
2. Get() Handler
Check if calling Get() returns the same handler after the first call (caching behavior).
Ensure that the returned handler correctly retrieves a resource from storage.
Test behavior when storage returns an error.
3. List() Handler
Verify that List() returns a cached handler after the first call.
Ensure it correctly lists resources from storage.
Check behavior when the request times out.
4. Create() Handler
Ensure Create() initializes the correct RequestScope.
Validate that handlers.CreateResource() is invoked with the expected parameters.
Test behavior when an invalid resource kind is provided.
5. Delete() Handler
Verify that Delete() retrieves a cached handler if already created.
Ensure it correctly deletes a resource from storage.
Validate error handling when deletion fails.
6. Update() Handler
If the resource is devices, confirm updateEdgeDevice() is invoked.
For other resources, validate that handlers.UpdateResource() is used.
Test error handling when storage update fails.
7. updateEdgeDevice() (Edge Device Specific Update)
Validate that the request body is correctly read and unmarshaled.
Ensure the device object is correctly set up with the expected GroupVersionKind.
Verify that the model.NewMessage() is properly created and routed.
Check error handling when sending a sync message to beehiveContext fails.
Ensure a valid response is written when the update succeeds.
8. PassThrough() Handler
Verify that PassThrough() calls storage.PassThrough().
Test error handling when storage.PassThrough() returns an error.
Validate the correct response is written to the client.
9. Patch() Handler
Ensure it correctly extracts the Content-Type header and determines PatchType.
Validate correct namespace and resource name extraction.
Test that the PatchOptions parameters are properly decoded.
Verify behavior when an invalid PatchOptions is provided.
Check that storage.Patch() is called with the correct PatchInfo.
Ensure that the response writer correctly sends back the patched object.
10. Concurrency & Locking
Test concurrent calls to Get(), List(), and Delete() to ensure correct locking behavior.
Ensure there are no race conditions when accessing handlers map.
11. Error Handling
Simulate various error conditions (e.g., missing resources, bad input, timeouts).
Verify that appropriate HTTP status codes (400, 404, 500) are returned.
This test logic covers all major aspects of the handlerfactory package to ensure correctness, stability, and proper error handling.
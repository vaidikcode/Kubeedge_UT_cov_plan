## Test Logic for EdgeHub Implementation
1. Initialization Tests
Test newEdgeHub Function

Verify that the EdgeHub object is created correctly with the expected fields initialized.
Ensure that rateLimiter, reconnectChan, and enable are set properly.
Test Register Function

Ensure that the config.InitConfigure function is called with the correct parameters.
Verify that newEdgeHub is properly registered with core.Register.
2. Module Properties Tests
Test Name Method

Validate that Name() returns modules.EdgeHubModuleName.
Test Group Method

Ensure that Group() returns modules.HubGroup.
Test Enable Method

Check that Enable() returns the correct boolean value based on the enable field.
3. Certificate Manager Tests
Test Certificate Synchronization Channel
Validate that NewCertSyncChannel() correctly initializes certSync.
Ensure that GetCertSyncChannel() retrieves the correct map.
Check if the channel exists for modules.EdgeStreamModuleName.
4. Start Method Tests
Test Initialization of Start Method

Ensure certificate.NewCertManager is initialized properly.
Check if certManager.Start() is executed.
Validate that certificate sync channels are notified and closed.
Test ifRotationDone Execution

Verify that ifRotationDone is correctly called in a separate goroutine.
Test initial Method Execution

Simulate failure and success cases for eh.initial().
Validate proper error handling if initialization fails.
Test Client Initialization and Reconnection

Ensure eh.chClient.Init() is called, and verify reconnection logic in case of failure.
Validate that after successful initialization:
pubConnectInfo(true) is called.
routeToEdge(), routeToCloud(), and keepalive() methods are triggered in separate goroutines.
Simulate a disconnection scenario and ensure reconnectChan handles it correctly.
Verify that pubConnectInfo(false) is called after disconnection.
Ensure proper wait times and retries occur.
5. Reconnect Logic Tests
Test Reconnection Handling
Simulate a disconnect scenario and ensure eh.reconnectChan receives a signal.
Validate that eh.chClient.UnInit() is called.
Ensure the system waits for the configured heartbeat interval before attempting a reconnection.
Verify that reconnectChan is cleared before the next connection attempt.
6. Edge and Cloud Routing Tests
Test routeToEdge and routeToCloud Execution
Ensure routeToEdge() and routeToCloud() are executed after a successful connection.
7. Keepalive Mechanism Tests
Test keepalive Execution
Verify that keepalive() runs in a separate goroutine after a successful connection.
Simulate heartbeat intervals and check if it sends keepalive messages as expected.
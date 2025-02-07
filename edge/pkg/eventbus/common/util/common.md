

## All test logic for common


Test Logic for util Package
Test Cases for CheckKeyExist
Test with All Keys Present

Provide a disinfo map containing all expected keys.
Ensure the function returns nil.
Test with Missing Keys

Provide a disinfo map missing at least one expected key.
Ensure the function returns an error.
Test Cases for CheckClientToken
Test with Successful Token

Mock an MQTT.Token that completes successfully.
Ensure the function returns true with no error.
Test with Failed Token

Mock an MQTT.Token that has an error.
Ensure the function returns false with the error.
Test Cases for PathExist
Test with Existing Path

Create a temporary file and check if PathExist returns true.
Test with Non-Existing Path

Provide a non-existing file path and ensure PathExist returns false.
Test Cases for HubClientInit
Test with Valid Credentials

Provide valid parameters (server, clientID, username, password).
Ensure the returned MQTT.ClientOptions contains the correct values.
Test with TLS Enabled

Mock eventconfig.Config.TLS.Enable = true with valid certificate paths.
Ensure the function returns a ClientOptions with a properly configured TLS setting.
Test with TLS Disabled

Mock eventconfig.Config.TLS.Enable = false.
Ensure TLS is disabled in the returned ClientOptions.
Test Cases for LoopConnect
Test with Immediate Connection Success

Mock an MQTT.Client that successfully connects on the first attempt.
Ensure LoopConnect exits immediately.
Test with Multiple Connection Attempts

Mock an MQTT.Client that fails a few times before succeeding.
Ensure the function retries the expected number of times before a successful connection.
Test with Persistent Connection Failure

Mock an MQTT.Client that always fails to connect.
Ensure LoopConnect keeps retrying indefinitely.

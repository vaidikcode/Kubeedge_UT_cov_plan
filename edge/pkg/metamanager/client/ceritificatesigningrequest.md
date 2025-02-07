
## Test Logic for CertificateSigningRequest Client

Setup & Teardown
Mock SendInterface to simulate sending and receiving messages.
Create a test instance of certificateSigningRequests.
Use valid and invalid CSR objects for testing.
Clean up after each test.
Test Cases for Create
Test Successful CSR Creation

Mock SendSync to return a valid CSR response.
Verify handleCertificatesSigningRequestResp correctly parses the response.
Ensure the returned CSR matches the expected data.
Test CSR Creation Failure

Simulate SendSync returning an error.
Verify the function returns an appropriate error message.
Test Malformed Response from SendSync

Return invalid/malformed JSON content.
Verify the function correctly handles and logs the error.
Test Cases for Get
Test Successful CSR Retrieval from MetaManager

Mock SendSync to return a valid CSR response from MetaManager.
Ensure handleCertificateSigningRequestFromMetaManager correctly parses it.
Test Successful CSR Retrieval from MetaDB

Mock SendSync to return a valid CSR response from MetaDB.
Verify handleCertificateSigningRequestFromMetaDB correctly handles it.
Test CSR Retrieval Failure

Simulate an error from SendSync.
Verify the function returns an appropriate error.
Test Malformed CSR Response

Return an invalid JSON response.
Verify error handling in handleCertificateSigningRequestFromMetaManager and handleCertificateSigningRequestFromMetaDB.
Test Cases for Helper Functions
Test handleCertificateSigningRequestFromMetaDB with Multiple CSR Entries

Return a response containing multiple CSR entries.
Verify the function returns an error indicating an unexpected list length.
Test handleCertificatesSigningRequestResp with API Errors

Mock a response containing an API error.
Ensure the function correctly detects and returns the error.

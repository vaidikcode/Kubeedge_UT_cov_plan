
## Test Cases for HTTPDo Method

Successful GET Request

Create a URLClient instance.
Call HTTPDo("GET", "http://example.com", nil, nil).
Verify the response is not nil and contains a valid status code.
Successful POST Request with Headers and Body

Provide headers and a JSON payload.
Call HTTPDo("POST", "http://example.com", headers, body).
Check if headers are correctly set in the request.
Verify the response.
Handling Authentication Failure

Mock SignRequest to return an error.
Ensure HTTPDo returns an authentication error.
Request with Compressed Encoding

Enable compression in URLClientOption.
Ensure Accept-Encoding contains gzip and deflate.
Handling HTTP Request Failure

Pass an invalid URL (http://invalid-url).
Ensure HTTPDo returns an error.
Test Cases for clientHasPrefix Method
HTTPS URL with SSL Config

Ensure the TLSClientConfig is applied when the URL starts with https.
Non-HTTPS URL

Ensure TLSClientConfig is not applied for http URLs.
Test Cases for GetURLClient Function
Create a Client with Default Options

Call GetURLClient(nil).
Verify the returned client has default options.
Create a Client with Custom Timeout Values

Pass a custom URLClientOption.
Verify that the client’s timeout values match the provided ones.
Create an SSL-Enabled Client

Set SSLEnabled = true with a TLS config.
Verify that the client’s TLSClientConfig is correctly assigned.

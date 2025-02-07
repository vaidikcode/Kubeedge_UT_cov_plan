
## All test cases for auth

1. JWTTokenAuthenticator()
Valid Case:
Create an authenticator instance with a valid indexer, issuers, keys, implicitAuds, and validator.
Ensure the returned instance is not nil.
Verify that the issuers map correctly stores the provided issuers.
2. hasCorrectIssuer(tokenData string)
Valid Case:
Provide a valid JWT token with an issuer present in issuers and ensure it returns true.
Invalid Case:
Provide a JWT token with an issuer not in issuers and ensure it returns false.
Provide a malformed JWT token (wrong number of parts, invalid Base64 encoding) and ensure it returns false.
Provide a JWT token with a missing iss claim and ensure it returns false.
3. AuthenticateToken(ctx context.Context, tokenData string)
Valid Case:
Provide a valid token with a correct issuer and signature, and ensure authentication succeeds.
Ensure the returned authenticator.Response contains correct user information and audiences.
Invalid Case:
Provide a token with an incorrect issuer and ensure authentication fails (false, nil).
Provide a token with an invalid signature and ensure authentication fails with an error.
Provide a token that is not in the local database when keys is empty and ensure authentication fails.
Provide a token with no valid intersection of audiences and ensure authentication fails.
Ensure that an invalid or malformed token returns false and an appropriate error message.
4. parseSigned(tokenData, public, private) (Indirect Testing)
Valid Case:
Ensure it correctly decodes and extracts claims from a valid signed token.
Invalid Case:
Ensure parsing fails if the token signature is incorrect.
Ensure it fails gracefully when decoding an invalid JWT.
5. Validate(ctx, tokenData, public, private) (Validator Behavior)
Valid Case:
Ensure the service account validator correctly validates a token and returns expected user info.
Invalid Case:
Ensure validation fails with an error when given an invalid token.
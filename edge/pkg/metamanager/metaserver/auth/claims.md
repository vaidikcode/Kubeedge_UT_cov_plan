
## Test Cases for Validate method

Valid Token:

Provide a valid token with correct claims.
Ensure the token is not expired.
Ensure the service account, secret, and pod exist with matching UIDs.
Expect a successful validation.
Expired Token:

Provide a token with an expiration time in the past.
Expect an error: "service account token has expired".
Token Not Yet Valid:

Provide a token with a "not valid before" time in the future.
Expect an error: "service account token is not valid yet".
Token with Deleted Service Account:

Provide a token where the referenced service account has a DeletionTimestamp before now - leeway.
Expect an error: "service account <namespace>/<name> has been deleted".
Token with Mismatched Service Account UID:

Provide a token where the service account UID in the token does not match the retrieved service account UID.
Expect an error: "service account UID (<actual UID>) does not match claim (<token UID>)".
Token with Deleted Secret:

Provide a token where the referenced secret has a DeletionTimestamp before now - leeway.
Expect an error: "service account token has been invalidated".
Token with Mismatched Secret UID:

Provide a token where the secret UID in the token does not match the retrieved secret UID.
Expect an error: "secret UID (<actual UID>) does not match service account secret ref claim (<token UID>)".
Token with Deleted Pod:

Provide a token where the referenced pod has a DeletionTimestamp before now - leeway.
Expect an error: "service account token has been invalidated".
Token with Mismatched Pod UID:

Provide a token where the pod UID in the token does not match the retrieved pod UID.
Expect an error: "pod UID (<actual UID>) does not match service account pod ref claim (<token UID>)".
Invalid Private Claims Object Type:

Pass an incorrect type instead of *privateClaims to Validate.
Expect an error: "service account token claims could not be validated due to unexpected private claim".
Test Cases for NewPrivateClaims method
Should Return a New privateClaims Object:
Call NewPrivateClaims and ensure it returns an empty *privateClaims.
Test Cases for parseSigned function
Valid Signed Token:

Provide a valid signed JWT.
Ensure it correctly unmarshals into the provided destination structs.
Malformed Token String:

Provide an invalid JWT format (not base64 encoded or missing parts).
Expect an error: "failed to parse token".
Invalid JSON in Claims:

Provide a valid JWT structure, but with an invalid JSON payload.
Expect an error: "failed to parse claims".

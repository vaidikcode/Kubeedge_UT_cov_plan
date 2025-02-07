
## All Test logic for serviceaccount.go

1. Testing GetServiceAccountToken
Case 1: Token exists locally and is valid

Mock dao.QueryMeta to return a valid token.
Verify that getTokenLocally retrieves the token.
Ensure getTokenRemotely is not called.
Case 2: Token exists locally but is expired

Mock dao.QueryMeta to return an expired token.
Ensure requiresRefresh triggers deletion.
Verify that getTokenRemotely is called.
Case 3: Token does not exist locally

Mock dao.QueryMeta to return no result.
Ensure getTokenRemotely is called.
Case 4: Remote retrieval succeeds

Mock c.send.SendSync to return a valid token.
Verify token is correctly unmarshaled and returned.
Case 5: Remote retrieval fails

Mock c.send.SendSync to return an error.
Ensure the function returns an error.
2. Testing DeleteServiceAccountToken
Case 1: Token exists and is linked to the given pod UID

Mock dao.QueryAllMeta to return tokens.
Ensure dao.DeleteMetaByKey is called for matching tokens.
Case 2: No matching tokens found for the given pod UID

Mock dao.QueryAllMeta with non-matching tokens.
Ensure dao.DeleteMetaByKey is not called.
Case 3: Database query fails

Mock dao.QueryAllMeta to return an error.
Ensure the function logs an error and exits.
3. Testing requiresRefresh
Case 1: Token has no expiration time

Pass a token with ExpirationSeconds as nil.
Verify function returns false.
Case 2: Token is within refresh threshold (80% of TTL)

Set expiration time close to 80% of its TTL.
Ensure function returns true.
Case 3: Token is still valid

Set expiration far from refresh threshold.
Ensure function returns false.
Case 4: Token is older than maxTTL (24 hours)

Ensure function returns true.
4. Testing getTokenLocally
Case 1: Token exists in the database and is valid

Mock dao.QueryMeta to return a valid token.
Ensure the token is returned.
Case 2: Token exists but is expired

Mock dao.QueryMeta with an expired token.
Ensure dao.DeleteMetaByKey is called.
Function should return an error.
Case 3: Token does not exist

Mock dao.QueryMeta to return an empty list.
Ensure function returns an error.
5. Testing getTokenRemotely
Case 1: Message successfully retrieves token from MetaDB

Mock c.send.SendSync to return a token from MetaDB.
Ensure handleServiceAccountTokenFromMetaDB is called.
Case 2: Message retrieves token from MetaManager

Mock c.send.SendSync to return a token from MetaManager.
Ensure handleServiceAccountTokenFromMetaManager is called.
Case 3: Message retrieval fails

Mock c.send.SendSync to return an error.
Ensure function returns an error.
6. Testing ServiceAccount Get
Case 1: Service account exists in the database

Mock dao.QueryMeta to return a matching ServiceAccountAccess.
Ensure the correct ServiceAccount is returned.
Case 2: Service account does not exist

Mock dao.QueryMeta with no matching service accounts.
Ensure function returns an error.
7. Testing CheckTokenExist
Case 1: Token exists in the database

Mock dao.QueryMeta to return a matching token.
Ensure function returns true.
Case 2: Token does not exist

Mock dao.QueryMeta with no matching tokens.
Ensure function returns false.
Case 3: Database query fails

Mock dao.QueryMeta to return an error.
Ensure function logs an error and returns false.

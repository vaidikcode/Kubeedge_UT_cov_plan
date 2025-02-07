## Test Cases for InsertUrls
Insert a new URL

Call InsertUrls("http://example.com").
Verify that the URL is inserted into the database.
Fetch the URL using GetUrlsByKey to confirm insertion.
Insert a duplicate URL (should replace the existing one)

Insert http://example.com.
Reinsert the same URL.
Ensure no duplicates exist.
Test Cases for DeleteUrlsByKey
Delete an existing URL

Insert http://example.com.
Delete it using DeleteUrlsByKey("http://example.com").
Verify that the URL is removed.
Delete a non-existent URL

Attempt to delete http://nonexistent.com.
Ensure no errors occur and no entries are deleted.
Test Cases for IsTableEmpty
Check empty table

Ensure IsTableEmpty() returns true when no URLs exist.
Check non-empty table

Insert a URL.
Verify that IsTableEmpty() returns false.
Test Cases for GetUrlsByKey
Retrieve an existing URL

Insert http://example.com.
Fetch it using GetUrlsByKey.
Verify the returned URL matches the inserted one.
Retrieve a non-existent URL

Call GetUrlsByKey("http://notfound.com").
Ensure it returns nil or an appropriate error.
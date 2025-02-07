This File include all the test logic for the file deviceattr_db

## deviceattr_db


1. Testing SaveDeviceAttr
Success Case: Insert a new DeviceAttr and verify that there are no errors.
Failure Case: Simulate a database failure during insertion and ensure the function returns an error.
2. Testing DeleteDeviceAttrByDeviceID
Success Case: Delete all attributes for a given DeviceID and ensure the operation completes successfully.
Failure Case: Simulate a database failure during deletion and verify error handling.
3. Testing DeleteDeviceAttr
Success Case: Delete a specific device attribute by DeviceID and Name and ensure the attribute is removed.
Failure Case: Attempt to delete a non-existent attribute and ensure the function handles it gracefully.
4. Testing UpdateDeviceAttrField
Success Case: Update a single field of a specific device attribute and verify that the update is reflected in the database.
Failure Case: Simulate a database failure and ensure the function returns an error.
5. Testing UpdateDeviceAttrFields
Success Case: Update multiple fields of a specific device attribute and validate the changes.
Failure Case: Simulate an update failure due to invalid column names or database issues.
6. Testing QueryDeviceAttr
Success Case: Query attributes based on a condition and verify that the correct attributes are returned.
Failure Case: Simulate a query failure and ensure the function handles errors properly.
7. Testing UpdateDeviceAttrMulti
Success Case: Update multiple device attributes at once and ensure all updates are correctly applied.
Failure Case: Simulate an update failure in one of the updates and ensure error propagation.
8. Testing DeviceAttrTrans
Success Case: Perform a transactional operation that includes adding, deleting, and updating attributes, ensuring all changes are applied correctly.
Failure Cases:
Simulate a failure while adding an attribute and verify that the transaction is rolled back.
Simulate a failure while deleting an attribute and ensure rollback.
Simulate a failure while updating an attribute and validate rollback.
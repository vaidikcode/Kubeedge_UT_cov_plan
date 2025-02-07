This files call the test logic for the file device_db

## device_db.go

1. Testing SaveDevice
Success Case: Insert a new Device and verify that there are no errors.
Failure Case: Simulate a database failure during the transaction and ensure the function returns an error.
2. Testing DeleteDeviceByID
Success Case: Delete a device by ID and verify successful execution.
Failure Case: Simulate a failure during deletion and check if an error is returned.
3. Testing UpdateDeviceField
Success Case: Update a specific field for a device and ensure the database reflects the change.
Failure Case: Simulate an update failure and ensure an error is returned.
4. Testing UpdateDeviceFields
Success Case: Update multiple fields of a device and verify the update count.
Failure Case: Simulate an update failure due to invalid input or database issues.
5. Testing QueryDevice
Success Case: Query devices based on a specific condition and verify the expected devices are retrieved.
Failure Case: Simulate a database query failure and ensure the function returns an error.
6. Testing QueryDeviceAll
Success Case: Retrieve all devices and ensure the expected data is returned.
Failure Case: Simulate a query failure and validate error handling.
7. Testing UpdateDeviceMulti
Success Case: Perform multiple field updates on different devices and verify the changes.
Failure Case: Simulate an error in one of the updates and ensure the function stops and returns the error.
8. Testing AddDeviceTrans
Success Case: Add multiple devices, attributes, and twins in a transaction and verify success.
Failure Cases:
Simulate failure while saving a device and ensure the transaction rolls back.
Simulate failure while saving attributes and ensure rollback.
Simulate failure while saving twins and verify rollback.
9. Testing DeleteDeviceTrans
Success Case: Delete multiple devices along with their attributes and twins, verifying their removal.
Failure Cases:
Simulate failure while deleting a device and ensure rollback.
Simulate failure while deleting attributes and ensure rollback.
Simulate failure while deleting twins and validate rollback.
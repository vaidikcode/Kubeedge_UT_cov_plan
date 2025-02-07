
## meta

1. SaveMeta(meta *Meta) error
Valid Case:
Create a new Meta object and save it using SaveMeta().
Ensure that no error is returned.
Verify that the object exists in the database by querying it.
Invalid Case:
Try inserting a duplicate key and ensure that IsNonUniqueNameError() properly handles it.
Pass an invalid Meta object (e.g., empty key) and check for an error.
2. IsNonUniqueNameError(err error) bool
Valid Case:
Pass an error message containing "UNIQUE constraint failed" or "constraint failed".
Ensure that the function returns true.
Invalid Case:
Pass a different error message and ensure that the function returns false.
3. DeleteMetaByKey(key string) error
Valid Case:
Insert a Meta object with a known key.
Delete it using DeleteMetaByKey().
Verify that the key is removed by querying it.
Invalid Case:
Attempt to delete a non-existent key and ensure it doesn't cause a fatal error.
4. DeleteMetaByKeyAndPodUID(key, podUID string) (int64, error)
Valid Case:
Insert a Meta object where Value contains podUID.
Delete using this function.
Ensure the correct number of rows are affected.
Invalid Case:
Call the function with a non-existent podUID.
Ensure it returns 0 rows affected.
5. UpdateMeta(meta *Meta) error
Valid Case:
Insert a Meta object.
Update its Value field.
Retrieve the updated record and verify the new value.
Invalid Case:
Attempt to update a non-existent record and verify the behavior.
6. InsertOrUpdate(meta *Meta) error
Valid Case:
Insert a new Meta object.
Call InsertOrUpdate() with the same key but a different value.
Verify that the value is updated, not duplicated.
7. UpdateMetaField(key, col, value interface{}) error
Valid Case:
Insert a Meta record and update only its Value column.
Ensure only the intended field is modified.
Invalid Case:
Try updating a non-existent field and expect an error.
8. UpdateMetaFields(key, cols map[string]interface{}) error
Valid Case:
Insert a Meta record and update multiple fields in one call.
Verify all changes are applied correctly.
Invalid Case:
Try updating multiple invalid fields and check for proper error handling.
9. QueryMeta(key string, condition string) (*[]string, error)
Valid Case:
Insert multiple Meta objects with similar keys but different conditions.
Query them and verify that the correct values are returned.
Invalid Case:
Query a key that doesn’t exist and ensure it returns nil.
10. QueryAllMeta(key string, condition string) (*[]Meta, error)
Valid Case:
Insert multiple Meta records and retrieve all of them.
Verify that the function correctly fetches all relevant entries.
Invalid Case:
Query an empty dataset and confirm it returns an empty list.
11. SaveMQTTMeta(nodeName string) error
Valid Case:
Call SaveMQTTMeta() with a test node name.
Verify that the metadata is stored correctly with the expected JSON format.
Retrieve the stored data and parse it back into a Pod object to ensure correctness.
Invalid Case:
Pass an empty nodeName and verify error handling.

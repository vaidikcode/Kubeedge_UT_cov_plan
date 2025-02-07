
## All test logic for subtopics

Test Logic for dao Package
Setup & Teardown
Before each test, initialize an in-memory database to avoid modifying real data.
After each test, clean up the database.
Test Cases for InsertTopics
Test Insert Valid Topic

Insert a new topic.
Verify that the topic is stored correctly.
Test Insert Duplicate Topic

Insert the same topic twice.
Verify that the topic is updated or remains unchanged.
Test Cases for DeleteTopicsByKey
Test Delete Existing Topic

Insert a topic.
Delete the topic.
Verify that the topic is removed from the database.
Test Delete Non-Existing Topic

Try deleting a topic that does not exist.
Verify that no error occurs and nothing is deleted.
Test Cases for QueryAllTopics
Test Query With Topics Present

Insert multiple topics.
Fetch all topics.
Verify the returned list contains all inserted topics.
Test Query With No Topics

Ensure the database is empty.
Fetch all topics.
Verify the returned list is empty.

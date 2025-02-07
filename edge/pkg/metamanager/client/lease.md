### **Test Logic for `leases` Client**

#### **Setup & Teardown**
- Mock `SendInterface` to simulate responses from the `SendSync()` method.
- Create an instance of `leases` with a test namespace.
- Use valid and invalid `Lease` objects for testing.
- Handle JSON unmarshalling errors and error responses.

---

### **Test Cases for CRUD Operations**

#### **Create**
1. **Test `Create` Sends Correct Message**  
   - Call `Create()` with a valid `Lease`.
   - Verify `SendSync()` is called with the correct `InsertOperation` message.
   - Mock a successful response and ensure the returned `Lease` matches expectations.

2. **Test `Create` Handles SendSync Failure**  
   - Simulate `SendSync()` returning an error.
   - Ensure `Create()` returns a proper error message.

3. **Test `Create` Handles Invalid Response Data**  
   - Mock a response with invalid JSON.
   - Verify `Create()` returns a JSON unmarshalling error.

4. **Test `Create` Handles API Error Response**  
   - Simulate `LeaseResp.Err` containing an error.
   - Ensure `Create()` returns the correct API error.

---

#### **Update**
5. **Test `Update` Sends Correct Message**  
   - Call `Update()` with a valid `Lease`.
   - Verify `SendSync()` is called with the correct `UpdateOperation` message.
   - Mock a successful response and ensure the returned `Lease` matches expectations.

6. **Test `Update` Handles SendSync Failure**  
   - Simulate `SendSync()` returning an error.
   - Ensure `Update()` returns a proper error message.

7. **Test `Update` Handles Invalid Response Data**  
   - Mock a response with invalid JSON.
   - Verify `Update()` returns a JSON unmarshalling error.

8. **Test `Update` Handles API Error Response**  
   - Simulate `LeaseResp.Err` containing an error.
   - Ensure `Update()` returns the correct API error.

---

#### **Get**
9. **Test `Get` Sends Correct Message**  
   - Call `Get()` with a valid lease name.
   - Verify `SendSync()` is called with the correct `QueryOperation` message.
   - Mock a successful response and ensure the returned `Lease` matches expectations.

10. **Test `Get` Handles SendSync Failure**  
    - Simulate `SendSync()` returning an error.
    - Ensure `Get()` returns a proper error message.

11. **Test `Get` Handles Invalid Response Data**  
    - Mock a response with invalid JSON.
    - Verify `Get()` returns a JSON unmarshalling error.

12. **Test `Get` Handles API Error Response**  
    - Simulate `LeaseResp.Err` containing an error.
    - Ensure `Get()` returns the correct API error.

---


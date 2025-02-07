This section contains the source code for clientset_bridge

## clientset_bridge file 

1. Test NewSimpleClientset Function
Setup: Create a mock metaClient implementing client.CoreInterface.
Action: Call NewSimpleClientset(metaClient).
Assertions:
Ensure the returned Clientset is not nil.
Ensure the embedded MetaClient is correctly assigned.
Ensure the Fake client from fakekube.NewSimpleClientset() is properly set.
2. Test CoreV1 Method
Setup: Create an instance of Clientset using NewSimpleClientset.
Action: Call CoreV1().
Assertions:
Ensure the returned object is of type kecorev1.CoreV1Bridge.
Ensure the FakeCoreV1 and MetaClient fields are correctly assigned.
3. Test StorageV1 Method
Setup: Create an instance of Clientset using NewSimpleClientset.
Action: Call StorageV1().
Assertions:
Ensure the returned object is of type kestoragev1.StorageV1Bridge.
Ensure the FakeStorageV1 and MetaClient fields are correctly assigned.
4. Test CoordinationV1 Method
Setup: Create an instance of Clientset using NewSimpleClientset.
Action: Call CoordinationV1().
Assertions:
Ensure the returned object is of type kecoordinationv1.CoordinationV1Bridge.
Ensure the FakeCoordinationV1 and MetaClient fields are correctly assigned.
5. Test Mock Behavior
Setup: Create a mock MetaClient and inject it into NewSimpleClientset.
Action: Use the returned clientset to make fake API calls (e.g., get a pod via CoreV1().Pods("namespace").Get(...)).
Assertions:
Ensure the API calls interact with the fake client as expected.
Ensure interactions with MetaClient happen when expected.
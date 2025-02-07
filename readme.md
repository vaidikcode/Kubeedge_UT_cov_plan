
---

### 📊 **KubeEdge UT Coverage Report**

#### **Overview**
This proposal addresses the current Unit Test (UT) coverage across the `KubeEdge` repository, targeting improvements to ensure robust and high-quality code. The main goals are:
- Identify missing files and their corresponding test coverage.
- Enhance test coverage for critical files and directories.
- Provide a clear mapping of **covered** and **uncovered** lines for each file.
- Document strategies to close the gaps in coverage.
- Every bit of code report is coevered in keadm and the whole report on this package is very detailed. Every other core package is covered too but not as detailed as keadm.
- I have used multiple tools to approximate the no of lines that will be after the implementation of the test logic written in every file's report.
The coverage percentage approximations will be very close to the actual coverage range as every bit of file is covered making the numbers pretty accurate.

---

### 📁 **Package Coverage Breakdown Before Implementaion**

| Package | Tracked Lines | Covered | Partial | Missed | Coverage % | Target%    |
|---------|---------------|---------|---------|--------|------------|------------|
| `cloud/` | **9,348**    | 2,989   | 205     | 6,154  | **31.97%** | **87.39%** | 7417/8487 
| `edge/`  | **6,903**    | 3,932   | 191     | 2,780  | **56.96%** |    TBD     |
| `keadm/` | **4,703**    | 1,062   | 48      | 3,593  | **22.58%** | **77.29%** | 6674/8641
| `pkg/`   | **1,298**    | 635     | 52      | 611    | **48.92%** | **83.01%** | 1168/1407
| **Subtotal** | **22,252** | **8,618** | 496 | **13,138** | **38.69%** |            |

---

### 🛠️ **Plan Details**



#### **Proper way To Analyse my report**
- **Open Pkg**:
    - Open the package and locate the file you want to see the ut test report on.


---

### 🎯 **Per-Package Metrics**

#### **1. Cloud Package (`cloud/`)**
- **Coverage Before**: **31.97%**
- **Focus Areas & Observations**

- Pkg directory in Cloud Pkg Coverage Improvent

1. It was trying to cover the whole report in this but it seems guidance of mentors on this particular pkg is necessary and we definately need a long discussion on what to teste here. Target of 7000+ line tested is achieveable. Although i have reviewed almost all the code but generating reports on all is not worth the effort.

> 7000+/8000

2. **cmd** package is thoroughly covered here though.

#### **2. Edge Package (`edge/`)**
- **Coverage**: **56.96%**
- **Focus Areas**: Optimize integration tests, focus on high-impact modules.

1. I have not made a very detailed report on this as there is no matrix testing approximations but i have mentioned the test logic. This was all beacuse it is not worth the effort because this needs to be discussed with the maintainers first on what to cover here.

#### **3. Keadm Package (`keadm/`)**
- **Coverage**: **22.58%**
- **Focus Areas and Observations**: 

1. This Package seems to have lowest coverage rate so the whole report is very detailed for this. 

2. I have thoroughly reviewed the keadm command tool, and it appears that many files were never tested or included in the test coverage shown on Codecov. I went through each of these files and aimed to achieve over 90% coverage for their unit tests. I understand that we don't want to write unit tests for everything; however, I have attempted to cover as much of the code as possible. We will need to discuss what to prioritize for unit testing to avoid introducing unnecessary burdens.

3. Another significant observation is that the utility package in KubeEdge, located at `/keadm/cmd/keadm/app/cmd/util`, primarily contains code related to root access and various operations in containerized environments. This can also be tested through integration or end-to-end tests. However, this situation causes the overall code coverage to drop significantly. If needed, we can always mock environments to write unit tests when necessary.

#### **4. Pkg Package (`pkg/`)**
- **Coverage**: **48.92%**
- **Focus Areas and Observations**

1. High percentage seems pretty achievable.

2. I have encountered many files that are not even in codecov but they need ut. Might need to discuss with mentors to decide on that

3. The work on viaduct packge is already in progress Under the issue To update quick go and add supplement tets. I have updated the code to handle context. Need to to resolve build failures and change assertions but already reaching 95% coverage there.

(Viaduct PR)[https://github.com/kubeedge/kubeedge/pull/6111]



# Using Shared Library - VPC Test Pipeline

This repository tests the VPC pipeline template defined in [a79354205-code/shared-lib](https://github.com/a79354205-code/shared-lib).

---

## 🚀 How the Pipeline Works

The template in [`vars/vpc.groovy`](https://github.com/a79354205-code/shared-lib/blob/main/vars/vpc.groovy) runs two stages:

1. **Checkout Stage**: Automatically performs `checkout scm` to pull this repository onto the Jenkins agent.
2. **VPC Stage**: Creates/provisions the VPC using the specified name (defaults to `my-vpc`).

```groovy
@Library('shared-lib') _

vpc()
```

---

## ⚙️ Options & Parameter Usage

### 1. Default Run (VPC name: `my-vpc`)
```groovy
@Library('shared-lib') _

vpc()
```

### 2. Custom VPC Name
```groovy
@Library('shared-lib') _

vpc('production-vpc')
// or: vpc(name: 'production-vpc')
```

### 3. Dynamic Loading (No Jenkins Admin configuration needed)
If `shared-lib` is not yet configured in Jenkins Global Settings, load it dynamically:
```groovy
library identifier: 'shared-lib@main', retriever: modernSCM(
    [$class: 'GitSCMSource',
     remote: 'https://github.com/a79354205-code/shared-lib.git']
)

vpc()
```

---

## 🛠️ Jenkins Setup Steps

1. Go to **Manage Jenkins** &rarr; **System** (or **Configure System**).
2. Scroll to **Global Pipeline Libraries** and click **Add**:
   - **Name**: `shared-lib`
   - **Default version**: `main`
   - **Retrieval method**: Modern SCM &rarr; Git &rarr; `https://github.com/a79354205-code/shared-lib.git`
3. Click **Save**.
4. Create a new **Pipeline** job in Jenkins:
   - Under **Pipeline**, choose **Pipeline script from SCM**.
   - **SCM**: Git.
   - **Repository URL**: `https://github.com/a79354205-code/using-shared-lib-.git`.
   - **Branch Specifier**: `*/main`.
   - **Script Path**: `Jenkinsfile`.
5. Click **Build Now** to run the test.
